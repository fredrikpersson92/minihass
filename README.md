# minihass

![MiniHass-Banner-01](https://github.com/fredrikpersson92/minihass/assets/105781178/5b3fd949-3a2f-406e-904b-17997335c291)

**Hi and welcome to MiniHass MKII, my second version of this minimalistic, rounded, and colorful dashboard UI for Home Assistant.**

## How do I install it?

This UI does use some custom components that will need to be downloaded from HACS, but other than that, it completely relies on your ability to add lines of YAML code to either your GUI Lovelace dashboard or through the backend, using tools such as Visual Studio Code. The latter is much easier and gives you more control. However, if you already have a dashboard in the GUI editor, then you can add any of the cards there by using the manual card and pasting the code. Please note that the cards rely on templates though, which will need to be added in the Raw Config Editor, or in your Lovelace config. You can read more on that [here](https://github.com/custom-cards/button-card#configuration-templates).

Ps. If using a YAML dashboard, I recommend creating a folder for all templates and referencing that in your Lovelace configuration. ('m not sure if this also can be done in the GUI)
```
button_card_templates: !include_dir_merge_named "/config/ui_lovelace_minihass/templates/"
```

## Theme and font and cards

This dashboard is 90% made of [custom Button Card](https://github.com/custom-cards/button-card). Follow the instructions in the link to install it. You will also need to add my theme to utilize the card's full potential, including light and dark modes. You can of course edit the values in the theme to suit your style :) I also opted for the font Montserrat from Google Fonts. You can install the font by adding the line below to your configuration.yaml, or as a *resource* to your GUI dashboard.

```
  lovelace:
    mode: yaml
    resources:
    - url: /www/community/button-card/button-card.js
      type: module
    - url: https://fonts.googleapis.com/css2?family=Montserrat:wght@300;700&display=swap"
      type: css
  ```

## Included cards

I will keep adding new cards gradually. For now, these are the available card templates you can copy and use. For each card, there is a template (multiple for some) and an example of the actual code to put in your dashboard. 

* Settings Card
* Title Card
* Navigate Card
* Garbage Collection Card
* Light Card
* Security Card
* Alarm Card
* Camera Card
* Alarm Card(s)

![Cards](https://github.com/fredrikpersson92/minihass/assets/105781178/5f58a9be-ef37-46c1-a051-a5f675cc9949)
