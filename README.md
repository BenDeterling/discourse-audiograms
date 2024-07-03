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

## Development in a Github Codespace

- **Creating a Discourse Codespace:** To start using Codespaces to make changes to this plugin, you'll need to fork discourse from `https://github.com/discourse/discourse`. From the top-right dialogue option in Github, create a new Codespace and open it a new window. Next, grab this discourse-audiograms plugin and place it in the Plugins folder located at `/discourse/plugins`. Create a new bash shell using the options in the bottom right of your Codespace. Now, cd into your `/workspace/discourse/` directory. Install everything from the Gemfile using:
  ```sh
  bundle install --gemfile ./Gemfile
  ```
  You'll also need to add the a new config.hosts to the `development.rb` file located at `.../discourse/config/environments/development.rb`. At the bottom of this file directly underneath the line that says `config.hosts << /\A(([a-z0-9-]+)\.)*localhost(\:\d+)?\Z/`, add the following:
  ```sh
  config.hosts << /^(.*)\.app\.github\.dev$/
  ```
  Finally, you'll need to create an admin account from the same `.../workspace/discourse/` directory using:
  ```sh
  bundle exec rake admin:create
  ```
 Follow the onscreen prompts. Now, you can start your server using `bin/ember-cli -u` from your `.../workspace/discourse/` directory. Once this is complete, you may navigate to the Ports tab in your Codespace and open the Forwarded Address for Port 4200. You'll only need to start the server for future uses of your Codespace.
