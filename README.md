# minihass

![MiniHass-Banner-01](https://github.com/fredrikpersson92/minihass/assets/105781178/5b3fd949-3a2f-406e-904b-17997335c291)

**Hi and welcome to MiniHass MKII, my second version of this minimalistic, rounded, and colorful dashboard UI for Home Assistant.
I was fortunate to have this featured in Everything Smart Home's [Youtube video](https://www.youtube.com/watch?v=7g9T_vKD4ww&t=8s&ab_channel=EverythingSmartHome) and there have since been many requests to share the cards. So here it goes! I hope everything works as I am quite new to sharing things on Github :)**

## How do I install it?
This dashboard is 90% made of [custom Button Card](https://github.com/custom-cards/button-card). However, this UI does use some custom components that will need to be downloaded from HACS, but other than that, it completely relies on your ability to add lines of YAML code to either your GUI Lovelace dashboard or through the backend, using tools such as Visual Studio Code. The latter is much easier and gives you more control. However, if you already have a dashboard in the GUI editor, then you can add any of the cards there by using the manual card and pasting the code. Please note that the cards rely on templates though, which will need to be added in the Raw Config Editor, or in your Lovelace config. You can read more on that [here](https://github.com/custom-cards/button-card#configuration-templates). 

### Step 1 - Install button-card
The templates rely on the integration button-card (https://github.com/custom-cards/button-card). If you have install HACS, you can jump to https://github.com/custom-cards/button-card#installation-and-tracking-with-hacs. If not, please see https://github.com/custom-cards/button-card#installation how to install it manually. 

### Step 2 - Theme and font
The components are based on a custom theme to utilize the card's full potential, including light and dark modes. You can either activate the theme globally per device or just for a single dashbord, for example if you have multiple. For a global activation, go to your user accont, search for dashboard, and select the theme after you installed it. You can of course edit the values in the theme to suit your style :) I also opted for the font Montserrat from Google Fonts. To install the theme and the font you have to do the following steps:

#### Install theme
Inside the config folder create new folder `themes` and copy the file `minihass.yaml` located under `minihass/theme` inside this folder. Than active the theme by adding the followind lines to your `configuration.yaml`.
```yaml
frontend:
  themes: !include_dir_merge_named themes
```
This assumes that the configuration.yaml is in the same folder were the `themes`-folder is located. 

```yaml
  lovelace:
    mode: yaml
    resources:
    - url: /www/community/button-card/button-card.js
      type: module
    - url: https://fonts.googleapis.com/css2?family=Montserrat:wght@300;700&display=swap"
      type: css
  ```


Ps. If using a YAML dashboard, I recommend creating a folder for all templates and referencing that in your Lovelace configuration. ('m not sure if this also can be done in the GUI)
```
button_card_templates: !include_dir_merge_named "/config/ui_lovelace_minihass/templates/"
```


## Included cards

I will keep adding new cards gradually. For now, these are the available card templates you can copy and use. For each card, there is a template (multiple for some) and an example of the actual code to put in your dashboard. 

* Settings Card
* Section Title Card
* Navigate Card
* Light Card
* Garbage Collection Card
* Camera Card
* Security Card
* Alarm(s) Card

![Cards](https://github.com/fredrikpersson92/minihass/assets/105781178/4ce74cd0-1e09-4c9e-80d5-47e45cf5cb62)



*Please note that this is very much a work in progress and many things are not perfect. Especially the backend theme :)
