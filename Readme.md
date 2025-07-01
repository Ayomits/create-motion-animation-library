  # create-motion-animation-library

  The module for creating reusable animation configs for `motion` library

  ## Features

  1. [ x ] Reusable animation factory
  2. [ x ] Less boilerplate

  ## Installation

  > npm

  ```bash
  npm install create-motion-animation-library
  ```

  > yarn

  ```bash
  yarn add create-motion-animation-library
  ```

  > copy-paste way <br>

  Just copy everything from `src/create-animation-library`

  ## Usage

  ```ts
  import { createAnimationLibrary } from "@ayo/create-motion-animation-library";

  import { createAnimationLibrary } from "./__create-animations";

  /**
   * The first function is global options provider
   *
   * This options will be inherit in the next function
   * */
  export const fadeAnimations = createAnimationLibrary({
    variants: {
      // This variant will be everywhere
      hidden: {
        opacity: 0,
      },
      // This variant will be everywhere
      visible: {
        // if this variant exists, the properties will be extended
        opacity: 1,
      },
    },
    // Animations which you want to extend
    // You can use it as barel for all animations
    animations: {},
  })(
    // The second function for define animations
    {
      // Keep it blank and properties from variants will be inherit
      fade: {},
      fadeScalable: {
        // As I said before you can extend global variants
        hidden: {
          scale: 0.9,
        },
        visible: {
          scale: 1,
        },
      },
      fadeYDown: {
        visible: {
          y: 0,
        },
        hidden: {
          y: -20,
        },
      },
      fadeYUp: {
        visible: {
          y: 20,
        },
        hidden: {
          y: 0,
        },
      },
      fadeXLeft: {
        visible: {
          x: -100,
        },
        hidden: {
          x: 0,
        },
      },
      fadeXRight: {
        visible: {
          x: 100,
        },
        hidden: {
          x: 0,
        },
      },
    }
  );
  ```

  ```ts
  // output
  {
      "fade": {
          "hidden": {
              "opacity": 0
          },
          "visible": {
              "opacity": 1
          }
      },
      "fadeScalable": {
          "hidden": {
              "scale": 0.9,
              "opacity": 0
          },
          "visible": {
              "scale": 1,
              "opacity": 1
          }
      },
      "fadeYDownDefault": {
          "hidden": {
              "y": -100,
              "opacity": 0
          },
          "visible": {
              "y": 0,
              "opacity": 1
          }
      },
      "fadeYDown": {
          "visible": {
              "y": 0,
              "opacity": 1
          },
          "hidden": {
              "y": -20,
              "opacity": 0
          }
      },
      "fadeYUp": {
          "visible": {
              "y": 20,
              "opacity": 1
          },
          "hidden": {
              "y": 0,
              "opacity": 0
          }
      },
      "fadeYUpDefault": {
          "visible": {
              "y": 100,
              "opacity": 1
          },
          "hidden": {
              "y": 0,
              "opacity": 0
          }
      },
      "fadeXLeft": {
          "visible": {
              "x": -100,
              "opacity": 1
          },
          "hidden": {
              "x": 0,
              "opacity": 0
          }
      },
      "fadeXRight": {
          "visible": {
              "x": 100,
              "opacity": 1
          },
          "hidden": {
              "x": 0,
              "opacity": 0
          }
      }
  }
  ```
