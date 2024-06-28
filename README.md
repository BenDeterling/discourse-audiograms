# Discourse-Audiograms

## Overview

A Discourse plugin to add the ability for users to create custom audiograms via a form input on the User Preferences page and have their audiograms appear as a link next to their username on posts for other users to see.

### Prerequisites

- Discourse

## Installation

1. **Clone Repository:**
    ```sh
    git clone https://github.com/BenDeterling/discourse-audiograms
    ```

2. **Install Plugin:**
    Copy the plugin directory `discourse-audiograms` to the Discourse plugins directory: `/var/discourse/plugins/`.

3. **Restart Discourse:**
    Rebuild your Discourse application to install the plugin:
    ```sh
    cd /var/discourse
    ./launcher rebuild app
    ```

4. **Enable Plugin:**
    Navigate to your Discourse Admin Panel (`http://your-discourse-site/admin/plugins`) and enable the plugin.

## Configuration

Enable/disable the plugin via the Discourse Admin Panel.

## Usage

Users can input their results from hearing tests by navigating to `User Preferences -> Profile` and clicking the "Create Audiogram" button. The audiogram will appear as a link next to the user's name on their posts and can be clicked to display the audiogram.

## Development

- **Editing the Audiogram Form:** The audiogram form is defined in `/audiograms/assets/javascripts/discourse/templates/connectors/user-custom-preferences/audiogram-preferences.hbs`. This file can be edited like any other HTML file.
  
- **Styling the Audiogram Form:** The styling for the audiogram form is defined in `/audiograms/assets/stylesheets/audiograms.scss` and can be edited like any other CSS file.
  
- **Editing the Audiogram:** The audiogram is generated in `/audiograms/assets/javascripts/discourse/initializers/extend-for-audiograms.js`. The plot is generated in `buildAudiogram()` and displayed in `displayAudiogram()`. Input fields are defined in `displayAudiogram()`.
  
- **Editing the Audiogram Link:** The audiogram link is generated in `/audiograms/assets/javascripts/discourse/initializers/extend-for-audiograms.js`. The audiogram link uses the "poster-name:after" PluginOutlet to show users' audiograms next to their username on posts and replies. The format and contents of the link are defined in `attachAudiogramLink()`.
  
- **Editing the Custom Header:** The custom HearingTracker header is defined in `/audiograms/assets/javascripts/discourse/connectors/extra-nav-item/extra-nav-item.hbs`. This file can be edited like any other HTML file.
