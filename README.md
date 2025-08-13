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
        - `--card-width`: this controls the overall width of the card
        - `--card-height`: this controls the overall height of the card. It is important to note that this means the height of the card *without* the relocation of the elements. This is because the individual elements are placed absolutely.
        - `--radius-card`: this is the `border-radius` of the card. This is what allows for the rounded corners
- Colours
    - We have one variable that is provided here:
        - `--card-bg`: This is the hex value of colour that the Physical and Mental stats as well as the HP and AC are held in. In this case, I am using `#a58e57` which is a kind of gold colour. This only needs to be changed in the variable and it will change the colour for any of the areas with that colour.
- Layout Constants
    - We have four variables that are provided here:
        - `--bar-height`: This variable is used as a unit of measurement that functions as a vertical "tick mark" across the bottom section of the card. This value is then used in other formulae throughout the stylesheet to allow for a more consistant and predictable height of elements as they are adjusted.
        - `--stack-height`: Much like the `--bar-height` variable, this is also used as a unit of measurement. However, in this case, it is specifc to the "floating pills" of the HP and AC (Overlay #3 and #4, respectively). It is used for the fine adjustment of both of these pills to make sure that they are at the same height.
> [!NOTE]
> It is important to note that with the `--stack-height` variable, there is a bit of a "gotcha". This is because there is a decorative border around those pills and a slight "tab" of the colour that extends below the pills to make them appear as a contiguous unit with the stats section. If the `--stack-height` is adjusted, it is important to note that the `--pill-extend` variable may also need to be adjusted so that there is no visible seam.
        - `--inset-x`: This variable is used to control the space between the HP and AC pills that sit above the stats. The larger the value, the larger the gap. The smaller the value, the smaller the gap. As long as the `--pill-extend` variable is the right amount, it should not show any visible seams and should allow for a clean sliding to adjust for the space that may be needed.
        - `--nameplate-height`: This variable controls the height of the "wooden" namebar at the top of the card. It is important to note that it is connected to the height of the section that holds the character token. As such, there may be a need to make some slight tweaks elsewhere, depending on the size that you want the namebar to be.
- Typography
    - There are several subsections under the Typography section. These are to facilitate in easier customisation.
        - Font Family Information
            - `--nameplate-font-family`: This is the font that you are looking to use in the nameplate a the top of the card. I have found that [Google Fonts](https://fonts.google.com/) work exceptionally well. However, it is important to keep in mind that not all fonts have a licence that will permit you to stream with them. Remember: it is your responsiblity to make sure that any content that you use for your streams is used appropriately.
            - `--nameplate-font-weight`: You can think of this as the boldness of the nameplate font. In this case, we are using a value of `700` because we want something that is quite bold.
        - Font Size Information
            - `--nameplate-text-size`: This is the text size for the name in the nameplate.
            - `--pill-text-size`: This is the text size for the HP and AC pills. Please keep in mind that the value here changes not only the size of the text, but the size of the images in the pills as well. This is because the images are actually from Font Awesome and are being rendered as part of the font rather than as an image.
            - `--stat-text-size`: This is the text size for the Physical and Mental stats at the bottom of the card. It is worth noting that if these values get too large, they will go off the edge of the card and other values may need to be adjusted. This is most easily tweaked by adjusting the `--card-width` variable that was mentioned above.
        - Font Colour Information
            - `--unified-font-color`: This is provided in case you want to have all of the font be the same colour. If so, all you need to do is change this value and it will update across the stylesheet.
            - `--nameplate-font-color`: This is the colour of the character's name in the nameplate at the top of the card. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--hp-font-color`: This is the colour for the HP value and the heart that is rendered next to the HP value. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--ac-font-color`: This is the colour for the AC value and the shield that is rendered next to the AC value. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--physical-stats-font-color`: This is the colour for the values of the physical stats of the character. These are the first three stats under the HP and AC values. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
            - `--mental-stats-font-color`: This is the colour for the value sof the mental stats of the character. These are the last three stats under the Physical Stat values. Should you wish to change this to a specific colour, you just need to remove the `var(--unified-font-color)` and replace it with a hex value of your choosing.
- Nameplate

### Overlays
- Overlay 1 - Character Name Information
    - This section contains the "wooden" backplate and the name of the character. In the example, above, it is using a different font from the rest of the card. This is achieved through the use of waht are called Psuedo-Elements. 
> [!NOTE]
> Throughout this stylesheet, anything in the `::before` psuedo-element is used for backgrounds, gradients and textures whereas anything in the `::after` psuedo-element is used for decorations to the element as well as borders.
- Overlay 2 - Token Image and Background
    - This section contains the character's token. 
> [!NOTE]
> The amazing token art that has been used here is made by SolaceSky. You can find her commissions here: [Solace's Commissions Page]()