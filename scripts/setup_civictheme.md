## CivicTheme Setup Script for GovCMS

This script automates the installation and configuration of CivicTheme, the `civictheme_govcms` support module, and a new custom subtheme within your GovCMS project.

### Prerequisites

1.  **GovCMS Project:** You must have a GovCMS project already set up.
2.  **Ahoy:** `ahoy` must be installed and configured for your project (i.e., you can run `ahoy` commands).
3.  **Docker:** Docker must be running, as `ahoy` typically interacts with Docker containers.
4.  **`wget` and `tar`:** These command-line utilities must be available in your shell environment where you run the script.
5.  **Bash:** The script is written for Bash.

### How to Use

1.  **Save the Script:**
    Save the script content to a file in your GovCMS project root (or a `scripts` subdirectory), for example, `setup_civictheme.sh`.

2.  **Make it Executable:**
    Open your terminal, navigate to the directory where you saved the script, and run:
    ```bash
    chmod +x setup_civictheme.sh
    ```

3.  **Run the Script:**
    Execute the script from your GovCMS project's root directory. You'll need to provide values for all the required arguments.

    **Command Structure:**
    ```bash
    ./setup_civictheme.sh -c <civictheme_version> \
                          -g <govcms_module_ref> \
                          -m <subtheme_machine_name> \
                          -u "<subtheme_human_name>" \
                          -d "<subtheme_description>"
    ```

    **Arguments:**

  *   `-c <civictheme_version>`: **(Required)** The version of the CivicTheme base theme to download (e.g., "1.11.0").
  *   `-g <govcms_module_ref>`: **(Required)** The Git reference (branch or tag) for the `civictheme_govcms` module.
    *   For a branch: e.g., "main"
    *   For a tag: e.g., "1.0.1" or "v1.0.1"
  *   `-m <subtheme_machine_name>`: **(Required)** The machine-readable name for your new subtheme. Use lowercase letters, numbers, and hyphens/underscores (e.g., "my_custom_site_theme").
  *   `-u "<subtheme_human_name>"`: **(Required)** The human-readable name for your new subtheme. Enclose in quotes if it contains spaces (e.g., "My Custom Site Theme").
  *   `-d "<subtheme_description>"`: **(Required)** A short description for your new subtheme. Enclose in quotes (e.g., "A custom theme for My Awesome GovCMS Project").

4.  **Example:**

    ```bash
    ./setup_civictheme.sh -c "1.11.0" \
                          -g "main" \
                          -m "my_gov_project_theme" \
                          -u "My Gov Project Theme" \
                          -d "Custom theme for the My Gov Project website on GovCMS."
    ```

5.  **View Help:**
    For a reminder of the options and usage:
    ```bash
    ./setup_civictheme.sh -h
    ```

### What the Script Does

The script will perform the following actions:
1.  Download and extract the specified CivicTheme version into `themes/custom/civictheme`.
2.  Run initial CivicTheme provisioning commands.
3.  Clear Drupal caches.
4.  Enable CivicTheme and set it as the default theme temporarily.
5.  Download, install, configure, and then uninstall and remove the `civictheme_govcms` module (as per the specified workflow).
6.  Generate a new subtheme based on CivicTheme using the provided names and description.
7.  Enable the new subtheme and set it as the site's default theme.

After the script completes successfully, your new subtheme will be active and ready for customisation in `themes/custom/<your_subtheme_machine_name>`.
