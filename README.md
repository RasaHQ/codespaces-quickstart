# codespaces-quickstart
Get started with Rasa Pro in the browser using GitHub Codespaces.

### Steps

1. **Create a Codespace:**
   - Click on the green "Code" button on this page, then scroll down to "Codespaces".
   - Click on "Create codespace on main".

2. **Set Up Environment:**
   - In the codespace, open the `.env` file from this repo and add the required keys to that file.
     ```
     RASA_PRO_LICENSE='your_rasa_pro_license_key_here'
     OPENAI_API_KEY='your_openai_api_key_here'
     ```
   - Set these environment variables by running 
     ```
     source .env
     ```
   - Activate your python environment by running
     ```
     source .venv/bin/activate
     ```

3. **Initialize a New Project:**
   - In the terminal, run:
     ```
     rasa init --template tutorial
     ```
     and follow the instructions.

4. **Train the Model:**
   - In the terminal, run:
     ```
     rasa train
     ```

5. **Talk to your Bot:**
   - In the terminal, run
     ```
     rasa inspect
     ```
     GitHub will show a notification, click on the green button to view the inspector where you can chat with your assistant.

6. **Run Custom Actions:**
   If your bot uses custom actions, you will need to run an action server. To do this:
   - Create a secnd terminal window in the codespace
   - load the env vars and activate your virtual environment: `source .env && source .venv/bin/activate`
   - start the action server by running `rasa run actions`
