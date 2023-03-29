# Lovelace-radio

The radio card is combined out of a few cards: [stack-in-card (HACS)](https://github.com/custom-cards/stack-in-card), button-cards in a horizontal-stack, and two times a [mini-media-player](https://github.com/kalkih/mini-media-player). 
You will require [spotcast (HACS)[(https://github.com/fondberg/spotcast) for this to work. 

```
type: custom:stack-in-card
cards:
  - type: custom:mini-media-player
    entity: media_player.music_flow_h7_d6_3e #### Change into your own media player
    name: Music Flow
    toggle_power: true
    volume_stateless: false
    volume_step: '2'
    group: false
    source: full
    artwork: material
    info: scroll
    hide:
      mute: true
      power: true
      name: true
      progress: true
      info: true
      volume_level: false
      jump: false
      icon_state: false
      runtime: true
      icon: false
      play_stop: true
      play_pause: false
      runtime_remaining: true
    sound_mode: icon
    icon: mdi:radio
    max_volume: '50'
  - type: horizontal-stack
    cards:
      - type: custom:button-card
        styles:
          card:
            - height: 30px
        name: SLAM!
        tap_action:
          action: call-service
          service: media_player.play_media
          service_data:
            media_content_id: media-source://radio_browser/962e7e22-0601-11e8-ae97-52543be04c81
            media_content_type: audio/mpeg
            entity_id: media_player.music_flow_h7_d6_3e #### Change into your own media player
      - type: custom:button-card
        styles:
          card:
            - height: 30px
        name: 538
        tap_action:
          action: call-service
          service: media_player.play_media
          service_data:
            media_content_id: media-source://radio_browser/68861777-8f09-4221-ae8f-56aa658060c0
            media_content_type: audio/mpeg
            entity_id: media_player.music_flow_h7_d6_3e #### Change into your own media player
      - type: custom:button-card
        styles:
          card:
            - height: 30px
        name: Sky Radio
        tap_action:
          action: call-service
          service: media_player.play_media
          service_data:
            media_content_id: media-source://radio_browser/ea6de4cc-53de-4b2d-8a1b-e92d0c575dff
            media_content_type: audio/mpeg
            entity_id: media_player.music_flow_h7_d6_3e #### Change into your own media player
      - type: custom:button-card
        styles:
          card:
            - height: 30px
        name: Radio 10
        tap_action:
          action: call-service
          service: media_player.play_media
          service_data:
            media_content_id: media-source://radio_browser/d227990c-2385-4419-8159-1c73a33a58dd
            media_content_type: audio/mpeg
            entity_id: media_player.music_flow_h7_d6_3e #### Change into your own media player
    always_play_random_song: true
    hide_currently_playing: false
    hide_playback_controls: false
    hide_top_header: true
    hide_chromecast_devices: true
    height: 270
    limit: 50
    known_connect_devices:
      - id: #### Redacted id ####
        name: Music Flow
  - type: custom:mini-media-player
    entity: media_player.spotify_**** #### Use your Spotify mediaplayer entity
    artwork: material
    hide:
      shuffle: false
      name: true
      volume: true
      progress: true
      icon: true
      power: true
    data:
      source: #### Put your media player name here ####
      media_content_id: >-
        #### put your playlist here ####
card_mod:
  style: |
    ha-card {
      {% if not is_state('entity.entity', 'off') and not is_state('entity.entity', 'idle') %}
        background: url( '{{ state_attr("entity.entity", "entity_picture") }}' ), linear-gradient(to left, transparent, rgb(var(--rgb-card-background-color)) 50%);

        {% if state_attr('entity.entity', 'media_content_type') == 'tvshow' %}
          background-size: auto 100%, cover;
        {% else %}
          background-size: 115% auto, cover;
        {% endif %}

        background-position: right;
        background-repeat: no-repeat;
        background-blend-mode: saturation;
      {% endif %}
    }

```
