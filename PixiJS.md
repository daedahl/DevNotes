# Looking into PixiJS

Starting with KittyKatAttack's PixiJS Tutorial on GitHub. It seems to be pretty comprehensive and well written. (These are rough notes for my own personal reference, refer to the link below for better readability - it's the original source)

https://github.com/kittykatattack/learningPixi

Pixi can auto-detect and serve up either the Canvas Drawing API or WebGL (2D) based on the client side environment. Typically WebGL is preferable and Canvas API is the fallback.

## The Renderer
    var renderer = PIXI.autoDetectRenderer(256, 256, {antialias: false, transparent: false, resolution: 1});

The last parameter is an optional array.

Canvas or WebGL can also be explicitly set:

    renderer = new PIXI.CanvasRenderer(256, 256);

    renderer = new PIXI.WebGLRenderer(256, 256);

### A Basic Implementation

    //Create the renderer
    var renderer = PIXI.autoDetectRenderer(256, 256);

    //Add the canvas to the HTML document
    document.body.appendChild(renderer.view);

    //Create a container object called the `stage`
    var stage = new PIXI.Container();

    //Tell the `renderer` to `render` the `stage`
    renderer.render(stage);

### Renderer View

renderer.view is the canvas element so

    renderer.view.style.border = "5px solid red";
    renderer.backgroundColor = 0x061639;
to find the height or width use
    render.view.width
    render.view.height

to fill the entire window

    renderer.view.style.position = "absolute";
    renderer.view.style.display = "block";
    renderer.autoResize = true;
    renderer.resize(window.innerWidth, window.innerHeight);

## Scale to Window Function
Courtesy of KittyKatAttack, the scaleToWindow function takes any canvas element and sizes and centers it to fill the browser window. If using PixiJS then the render.view object should be passed. The second optional parameter sets the bordering background color.

    function scaleToWindow(canvas, backgroundColor) {

      backgroundColor = backgroundColor || "#2C3539";
      var scaleX, scaleY, scale, center;

      //1. Scale the canvas to the correct size
      //Figure out the scale amount on each axis
      scaleX = window.innerWidth / canvas.offsetWidth;
      scaleY = window.innerHeight / canvas.offsetHeight;

      //Scale the canvas based on whichever value is less: `scaleX` or `scaleY`
      scale = Math.min(scaleX, scaleY);
      canvas.style.transformOrigin = "0 0";
      canvas.style.transform = "scale(" + scale + ")";
      console.log(scaleX)

      //2. Center the canvas.
      //Decide whether to center the canvas vertically or horizontally.
      //Wide canvases should be centered vertically, and
      //square or tall canvases should be centered horizontally
      if (canvas.offsetwidth > canvas.offsetHeight) {
        if (canvas.offsetWidth * scale < window.innerWidth) {
          center = "horizontally";
        } else {
          center = "vertically";
        }
      } else {
        if (canvas.offsetHeight * scale < window.innerHeight) {
          center = "vertically";
        } else {
          center = "horizontally";
        }
      }

      //Center horizontally (for square or tall canvases)
      var margin;
      if (center === "horizontally") {
        margin = (window.innerWidth - canvas.offsetWidth * scale) / 2;
        canvas.style.marginTop = 0;
        canvas.style.marginBottom = 0;
        canvas.style.marginLeft = margin + "px";
        canvas.style.marginRight = margin + "px";
      }

      //Center vertically (for wide canvases)
      if (center === "vertically") {
        margin = (window.innerHeight - canvas.offsetHeight * scale) / 2;
        canvas.style.marginTop = margin + "px";
        canvas.style.marginBottom = margin + "px";
        canvas.style.marginLeft = 0;
        canvas.style.marginRight = 0;
      }

      //3. Remove any padding from the canvas  and body and set the canvas
      //display style to "block"
      canvas.style.paddingLeft = 0;
      canvas.style.paddingRight = 0;
      canvas.style.paddingTop = 0;
      canvas.style.paddingBottom = 0;
      canvas.style.display = "block";

      //4. Set the color of the HTML body background
      document.body.style.backgroundColor = backgroundColor;

      //Fix some quirkiness in scaling for Safari
      var ua = navigator.userAgent.toLowerCase();
      if (ua.indexOf("safari") != -1) {
        if (ua.indexOf("chrome") > -1) {
          // Chrome
        } else {
          // Safari
          //canvas.style.maxHeight = "100%";
          //canvas.style.minHeight = "100%";
        }
      }

      //5. Return the `scale` value. This is important, because you'll nee this value
      //for correct hit testing between the pointer and sprites
      return scale;
    }

It returns the ratio by which the canvas was scaled which is useful when you need to covert browser pixel coordinates to the scaled canvas coordinates.

It can also be placed into an event listener to auto-resize whenever the browser window is resized.

    window.addEventListener("resize", function(event){
      scaleToWindow(anyCanvasElement);
    });

## Sprites
Images must be converted to textures for WebGL to make use of them.

    PIXI.utils.TextureCache["images/anyImage"];

### Loading Sprites
Recommended loader format:

    PIXI.loader
      .add("images/anyImage.png")
      .load(setup);

    function setup() {
      var sprite = new PIXI.Sprite(
        PIXI.loader.resources["images/anyImage.png"].texture
      );
    }

Multiple files in an array:

    PIXI.loader
      .add([
        "images/imageOne.png",
        "images/imageTwo.png",
        "images/imageThree.png"
      ])
      .load(setup);

### Displaying Sprites
Need to add the sprite to the stage and rerender

    stage.addChild(cat);
    renderer.render(stage);

Can be removed with:

    stage.removeChild(name);

But this is probably better:

    anySprite.visible = false;

## Aliases

    //Aliases
    var Container = PIXI.Container,
    autoDetectRenderer = PIXI.autoDetectRenderer,
    loader = PIXI.loader,
    resources = PIXI.loader.resources,
    Sprite = PIXI.Sprite;

    //Create a Pixi stage and renderer and add the
    //renderer.view to the DOM
    var stage = new Container(),
    renderer = autoDetectRenderer(256, 256);
    document.body.appendChild(renderer.view);

    //load an image and run the `setup` function when it's done
    loader
    .add("images/cat.png")
    .load(setup);

    function setup() {

    //Create the `cat` sprite, add it to the stage, and render it
    var cat = new Sprite(resources["images/cat.png"].texture);  
    stage.addChild(cat);
    renderer.render(stage);
    }
