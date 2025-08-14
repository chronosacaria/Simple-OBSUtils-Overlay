# Simple OBSUtils Overlay
The goal of this repository is to provide a simple overlay that people can use, look at and learn from, freely. There is a simple guide that is provided in the CSS file, itself; but I will try to go over things here, as well.

## Background
So, as I said: this is a stylesheet that works with the FoundryVTT Module called [OBS Utils](https://foundryvtt.com/packages/obs-utils) by the amazing developer Faey, who has been absolutely instrumental to the development of this stylesheet. She has an awesome Discord and is extremely responsive when people have questions. Please consider checking her out here: [Faey's Discord](https://discord.com/invite/WfMaKPPdeM). You can also support her module development on her Patreon, here: [Faey's Patreon](https://patreon.com/voidmonster).

## Guide for New Readers (What this file does)
Okay, so what does this stylesheet actually do? Well, let's take a look at a visual example, first.
![Image of four character cards with the styling from this repository](https://github.com/chronosacaria/Simple-OBSUtils-Overlay/blob/main/img/card_examples.png?raw=true)
### Groundwork
As we can see, there are a few elements that are provided with this stylesheet. Whilst we can jump right into the overlays, it is important to understand some of the `:root` contents of the stylesheet as these are the foundation upon which everything else is built. Let's look at them one by one:
- Dimensions
    - We have three variables that are provided here:
        - `--card-width` (Default Value: `220px`): this controls the overall width of the card
        - `--card-height` (Default Value: `320px`): this controls the overall height of the card. It is important to note that this means the height of the card *without* the relocation of the elements. This is because the individual elements are placed absolutely.
        - `--radius-card` (Default Value: `10px`): this is the `border-radius` of the card. This is what allows for the rounded corners
- Colours
    - We have one variable that is provided here:
        - `--card-bg` (Default Value: `#a58e57`): This is the hex value of colour that the Physical and Mental stats as well as the HP and AC are held in. In this case, I am using `#a58e57` which is a kind of gold colour. This only needs to be changed in the variable and it will change the colour for any of the areas with that colour.
- Layout Constants
    - We have eight variables that are provided here:
        - `--cards-top` (Default Value: `10px`): This is used to help position the gradient that is used for the background of the tokens. This is also used for spacing the gradient when the cards are "exploded".
        - `--bar-height` (Default Value: `28px`): This variable is used as a unit of measurement that functions as a vertical "tick mark" across the bottom section of the card. This value is then used in other formulae throughout the stylesheet to allow for a more consistant and predictable height of elements as they are adjusted.
        - `--stack-height` (Default Value: `26px`): Much like the `--bar-height` variable, this is also used as a unit of measurement. However, in this case, it is specifc to the "floating pills" of the HP and AC (Overlay #3 and #4, respectively). It is used for the fine adjustment of both of these pills to make sure that they are at the same height.
            > **ⓘ Note:** <br/>
            > It is important to note that with the `--stack-height` variable, there is a bit of a "gotcha". This is because there is a decorative border around those pills and a slight "tab" of the colour that extends below the pills to make them appear as a contiguous unit with the stats section. If the `--stack-height` is adjusted, it is important to note that the `--pill-extend` variable may also need to be adjusted so that there is no visible seam.
        - `--inset-x` (Default Value: `8px`): This variable is used to control the space between the HP and AC pills that sit above the stats. The larger the value, the larger the gap. The smaller the value, the smaller the gap. As long as the `--pill-extend` variable is the right amount, it should not show any visible seams and should allow for a clean sliding to adjust for the space that may be needed.
        - `--nameplate-height` (Default Value: `38px`): This variable controls the height of the "wooden" namebar at the top of the card. It is important to note that it is connected to the height of the section that holds the character token. As such, there may be a need to make some slight tweaks elsewhere, depending on the size that you want the namebar to be.
        - `--initial-card-left-placement` (Default Value: `0px`): This variable is used to control the offsent of the cards from the left most element.
        - `--card-placement-offset` (Default Value: `258px`): This variable controls the amount of pixels between each card when there is more than one card.
        - `--gradient-gap` (Default Value: `48px`): This is the distance between the bottom of the cards and the top of the gradient when the cards are "exploded".
- Typography
    - There are several subsections under the Typography section. These are to facilitate in easier customisation.
        - Font Family Information
            - `--nameplate-font-family` (Default Value: `'UnifrakturCook', cursive`): This is the font that you are looking to use in the nameplate a the top of the card. I have found that [Google Fonts](https://fonts.google.com/) work exceptionally well. However, it is important to keep in mind that not all fonts have a licence that will permit you to stream with them. Remember: it is your responsiblity to make sure that any content that you use for your streams is used appropriately.
            - `--nameplate-font-weight` (Default Value: `700`): You can think of this as the boldness of the nameplate font. In this case, we are using a value of `700` because we want something that is quite bold.
        - Font Size Information
            - `--nameplate-text-size` (Default Value: `18px`): This is the text size for the name in the nameplate.
            - `--pill-text-size` (Default Value: `18px`): This is the text size for the HP and AC pills. Please keep in mind that the value here changes not only the size of the text, but the size of the images in the pills as well. This is because the images are actually from Font Awesome and are being rendered as part of the font rather than as an image.
            - `--stat-text-size` (Default Value: `16px`): This is the text size for the Physical and Mental stats at the bottom of the card. It is worth noting that if these values get too large, they will go off the edge of the card and other values may need to be adjusted. This is most easily tweaked by adjusting the `--card-width` variable that was mentioned above.
        - Font Colour Information
            - `--unified-font-color` (Default Value: `#ffffff`): This is provided in case you want to have all of the font be the same colour. If so, all you need to do is change this value and it will update across the stylesheet.
            - `--nameplate-font-color` (Default Value: `var(--unified-font-color)`): This is the colour of the character's name in the nameplate at the top of the card. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--hp-font-color` (Default Value: `var(--unified-font-color)`): This is the colour for the HP value and the heart that is rendered next to the HP value. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--ac-font-color` (Default Value: `var(--unified-font-color)`): This is the colour for the AC value and the shield that is rendered next to the AC value. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--physical-stats-font-color` (Default Value: `var(--unified-font-color)`): This is the colour for the values of the physical stats of the character. These are the first three stats under the HP and AC values. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--mental-stats-font-color` (Default Value: `var(--unified-font-color)`): This is the colour for the value sof the mental stats of the character. These are the last three stats under the Physical Stat values. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
- Nameplate
    - These three variables are used to work out which colours will be used to make the knotty texture in the nameplate at the top of the card. These variables work together to give the desired effect.
    - `--name-wood-1` (Default Value: `#9a6a3a`): This is the colour for the base stripes colour for the wooden nameplate at the top of the card. 
    - `--name-wood-2` (Default Value: `#b37a41`): This is the colour for the secondary stripes colour for the wooden nameplate at the top of the card.
    - `--name-wood-3` (Default Value: `#865c33`): This is the colour for the tertiary stripes colour for the wooden nameplate at the top of the card.
        > **ⓘ Note:** <br/>
        > It is advisable to keep these colours pretty close to each other, but adjust the values. Whilst any colours can be used, it just comes down to what effect you are looking for.
- Wood Borders
    - These variables are used to control the colours of the borders that surround the Physical and Mental Stats as well as the HP and AC pills. These colours are used to form a linear gradient that allows for some variation in the line that is created. The thickness of the border is also controlled in this section.
        - `--wood-dark` (Default Value: `#6b4e2e`): This is the darkest colour that is used for the border gradient.
        - `--wood-mid` (Default Value: `#8a653b`): This is the middle colour that is used for the border gradient.
        - `--wood-lite` (Default Value: `#b48853`): This is the lightest colour that is used for the border gradient.
        - `--wood-thickness` (Default Value: `3px`): This is the thickness of the border.
- Pill Adjustments
    - These variables are used to adjust the positioning of the pills that contain the HP and AC values.
        - `--pill-raise` (Default Value: `8px`): This variable controls the height of pill relative to the top of the Physical Stats section.
        - `--pill-extend` (Default Value: `8px`): This variable controls the extension of the background of the pill to make it so that the pills look like they are unified with the stat block that is at the bottom of the card.
- Gradient Behind Portrait
    - These variables are used with the `Gradient Helpers` in order to create the gradient behind the tokens as well as when the cards are "exploded".
        - `--desired-alpha-value` (Default Value: `1`): This variable controls the alpha (transparency) of the whole gradient.
            > **ⓘ Note:** <br/>
            > At this time, there is no way to control the alpha value of the different sides of the gradient. Therefore, the `--desired-alpha-value` will provide a consistent alpha value across the whole gradient.
        - `--gradient-lower-left` (Default Value: `#b6e1ff`): This variable is a hex colour value that controls the starting value of the gradient, which starts from the bottom left.
        - `--gradient-upper-right` (Default Value: `#f4f5f7`): This variable is a hex colour value that controls the ending value of the gradient, which ends at the top right.
- Boolean Values
    - These values are used as a toggle between on and off for their respective part. `0` shall serve as `false` or `No` and `1` shall serve as `true` or `Yes`.
        - `--is-token-visible` (Default Value: `1`): This value controls whether the token portrait in the centre of the card is visible.
            > **ⓘ Note:** <br/>
            > Why might you not want to the token to be visible? The way that this stylesheet is set up, you can hide the token and explode out the background so that you can add other elements into your OBS overlay if you wish to do so.
        - `--is-token-background-offset` (Default Value: `0`): This value controls whether the background that is behind the token is exloded out from the card. When the background is exploded out, it will be positioned below the first card.
### Overlays
- Overlay 1 - Character Name Information
    - This section contains the "wooden" backplate and the name of the character. In the example, above, it is using a different font from the rest of the card. This is achieved through the use of waht are called Psuedo-Elements. 
        > **ⓘ Note:** <br/>
        > Throughout this stylesheet, anything in the `::before` psuedo-element is used for backgrounds, gradients and textures whereas anything in the `::after` psuedo-element is used for decorations to the element as well as borders.
- Overlay 2 - Token Image and Background
    - This section contains the character's token. 
        > **ⓘ Note:** <br/>
        > The amazing token art that has been used here is made by SolaceSky. You can find her commissions here: [Solace's Commissions Page](https://solacesky.carrd.co/#commissions)