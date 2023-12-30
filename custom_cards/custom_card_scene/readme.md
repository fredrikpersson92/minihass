For the card to work with the current entity, you will need to create a Dropdown Helper.
Name it *input_select.scene_card* and add the following options: None, Office Mood, Movie Time, Night.
The options can of course be whatever you would like, just remember to also change the occuring states in the card template file.

You will also need to create the following Scripts:

```
alias: Scene Movie Time
sequence:
  - service: input_select.select_option
    data:
      option: Movie Time
    target:
      entity_id: input_select.scene_card
mode: single
icon: mdi:movie-roll
```

```
alias: Scene Night
sequence:
  - service: input_select.select_option
    data:
      option: Night
    target:
      entity_id: input_select.scene_card
mode: single
icon: mdi:weather-night
```

```
alias: Scene Night
sequence:
  - service: input_select.select_option
    data:
      option: Night
    target:
      entity_id: input_select.scene_card
mode: single
icon: mdi:weather-night
```

```
alias: Scene None
sequence:
  - service: input_select.select_option
    data:
      option: None
    target:
      entity_id: input_select.scene_card
mode: single
icon: mdi:auto-fix
```

See screenshot below for what it should look like in the visual editor:
![Scripts](https://github.com/fredrikpersson92/minihass/assets/105781178/828ef1e1-4925-4831-8de1-2769d124f130)

Ps. Don't forget to change the colors and fonts to your liking.
