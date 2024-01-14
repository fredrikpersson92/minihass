# minihass

![MiniHass-Banner-01](https://github.com/fredrikpersson92/minihass/assets/105781178/5b3fd949-3a2f-406e-904b-17997335c291)

**Hi and welcome to MiniHass MKII, my second version of this minimalistic, rounded, and colorful dashboard UI for Home Assistant.
I was fortunate to have this featured in Everything Smart Home's [Youtube video](https://www.youtube.com/watch?v=7g9T_vKD4ww&t=8s&ab_channel=EverythingSmartHome) and there have since been many requests to share the cards. So here it goes! I hope everything works as I am quite new to sharing things on Github :)**

## How do I install it?
This dashboard is 90% made of [button Card](https://github.com/custom-cards/button-card). However, this UI does use some custom components that will need to be downloaded from HACS, but other than that, it completely relies on your ability to add lines of YAML code to either your GUI Lovelace dashboard or through the backend, using tools such as Visual Studio Code. The latter is much easier and gives you more control. However, if you already have a dashboard in the GUI editor, then you can add any of the cards there by using the manual card and pasting the code. Please note that the cards rely on templates though, which will need to be added in the Raw Config Editor, or in your Lovelace config. You can read more on that [here](https://github.com/custom-cards/button-card#configuration-templates). 

### Step 1 - Install button-card
If you've already installed HACS, proceed to [install via HACS](https://github.com/custom-cards/button-card#installation-and-tracking-with-hacs). Otherwise, see how to install it manually [here](https://github.com/custom-cards/button-card#installation).

### Step 2 - Theme and font
The components utilize a custom theme to maximize the card's capabilities, including both light and dark modes. You can activate this theme either for each single devices or exclusively for a specific dashboard. For global per device activation, navigate to your user account, search for `dashboard`, and select the theme. You're welcome to modify the theme values to fit your preferences! Additionally, I've chosen the Montserrat font from Google Fonts. To install both the theme and font, follow these steps:

#### Install theme
Within the config folder, create a new subfolder titled `themes`. Transfer the `minihass.yaml` file, found in `minihass/theme`, to this new folder. Activate the theme by appending the following lines to your `configuration.yaml`:
```yaml
frontend:
  themes: !include_dir_merge_named themes
```
This assumes that the configuration.yaml is in the same folder were the `themes`-folder is located. 

#### Add resources
To incorporate the button-card and the selected font, insert the following into your configuration.yaml
```yaml
  lovelace:
    mode: yaml
    resources:
    - url: /www/community/button-card/button-card.js
      type: module
    - url: https://fonts.googleapis.com/css2?family=Montserrat:wght@300;700&display=swap"
      type: css
  ```

#### Adding the button templates
To utilize the custom-made templates, you must first copy all templates to a designated folder and then reference that folder in your dashboard. Create a directory named `ui_lovelace_minihass` with a subfolder titled `templates`. Transfer all `*.yaml` template files to this subfolder. The structure should resemble:
```
ui_lovelace_minihass
|_ templates
   |_ custom_card_light.yaml
   |_ custom_card_section_title.yaml
   |_ ...
```

#### Creating a new dashboard
The best way to integrate everything in a new dashboard is to do this via the yaml configuration. You can us this dashboard side-by-side with a GUI dashboard. Within the directory containing your `configuration.yaml`, create a new file called `dashboard.yaml`. Customize the file name as desired and adjust the name withine `configration.yaml` accordingly. 
```yaml
lovelace:
  mode: yaml
  resources:
    - url: /hacsfiles/button-card/button-card.js
      type: module
    - url: https://fonts.googleapis.com/css2?family=Montserrat:wght@300;700&display=swap"
      type: css
  
  dashboards:
    home-dashboard:
      mode: yaml
      filename: "/config/dashboard.yaml"   #path to your dashboard.yaml
      title: TITLE                         #a title of the dashboard you like
      icon: mdi:script
      show_in_sidebar: true
```
Within the `dashboard.yaml` file, begin with this quickstart example:
```yaml
title: Example
button_card_templates: !include_dir_merge_named "/config/ui_lovelace_minihass/templates/"   #path to your templates .yaml
views:
  - title: Home
    theme: MiniHass_Dark   #Theme you want to activate
    cards:
      - type: "custom:button-card"
        template:
          - custom_card_section_title
        variables:
          section_title: Navigate

      - type: "custom:button-card"
        entity: ENTITY          #specify the entity to switch on/off, e.g. a light
        template:
          - custom_card_light
        variables:
          light_name: Window
          light_label: Bedroom
```


## Included cards
I'll be gradually adding new card templates. Currently, these are the available templates for you to replicate and utilize. Each card features a template (some have multiple) along with an example code to integrate into your dashboard:
* Settings Card
* Section Title Card
* Navigate Card
* Light Card
* Garbage Collection Card
* Camera Card
* Security Card
* Alarm(s) Card

![Cards](https://github.com/fredrikpersson92/minihass/assets/105781178/4ce74cd0-1e09-4c9e-80d5-47e45cf5cb62)



*Please be aware that this project is still evolving. Some elements, especially the backend theme, may not be perfect. :)

If you feel this is useful for your own Home Assistant dashboard, feel free to support my work by "Buying me a coffee" or just give a thumbs up on the community forum thread. I love to see how you adapt to your own projects!

<a href="https://www.buymeacoffee.com/fredrik_persson_" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

