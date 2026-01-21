# Tool Instructions  

1. In the **VS Code Marketplace**, install the extension **Copilot Interaction Archiver**: https://marketplace.visualstudio.com/items?itemName=Copilot-Archiver.copilot-archiver.

To ensure the archiver only runs on your homework assignments:

2. Remote SSH into your homework folder (**workspace**) in VS Code.
3. The extension will ask you to give **workspace access** whenever you open a new workspace.
4. Enable it by clicking "Yes" **only for your homework projects** (so we don’t collect usage data for other Copilot use).
5. If you see a pop-up message saying "GitHub Copilot Chat must be in Debug mode", click **Open Menu** -> Select **GitHub Copilot Chat** -> Select **Debug** log level 
   * These steps are shown in this video 0:42 -> 54: https://drive.google.com/file/d/18tCphUyFp4M1Gzj-G31jVM62Y9F_9vY2/view?usp=sharing

## How to Log In
The extension requires authentication to securely upload your data.

- Enter your **Andrew ID** when prompted (we will only store the **hashed ID**), **or**
  - Press:
    - `Cmd + Shift + P` (Mac)  
    - `Ctrl + Shift + P` (Windows)  
    to open the **Command Palette**.
  - Type and run:  
    **Copilot Archiver: Login**
- Enter the password:  
  **`CMU_2026!`**

> **Note:** Check the status of your extension is logged in. Your login status will be shown in the bottom-right corner of the IDE. You only need to log in once every 6 months. If your session expires, the extension will prompt you to log in again.

## Tool Support
If you run into any questions during this tool setup, post in Slack channel #copilot_archiver_support. 

## Not using GitHub Copilot
If you use AI tools other than GitHub Copilot, please collect logs of your prompts/chat history in the directory `ai_logs`. Most tools have an obvious export feature (e.g., [ChatGPT](https://help.openai.com/en/articles/7925741-chatgpt-shared-links-faq), [Cursor](https://cursor.com/docs/agent/chat/export)).



# FAQ

## Setup & Requirements

### Q: What version of VS Code do I need?

A: Make sure your VS Code version is up to date (\>= **1.108**). You can check by going to `Code → About Visual Studio Code` (Mac) or `Help → About` (Windows / Linux). To update, go to `Code → Check for Updates`.  


## Troubleshooting

### Q: The extension is taking up too much disk space / my `.archiver_shadow` folder is very large.

A: We identified and fixed a bug that could cause the shadow repository to grow unexpectedly. Please update to the latest version:

1. Open VS Code Extensions panel (`Cmd+Shift+X` / `Ctrl+Shift+X`).  
2. Search `“Copilot Interaction Archiver”`.  
3. Click “Update” if available, then reload the window.

After reloading, the `.archiver_shadow` folder should shrink automatically (shadow repos over 1GB are reset).  
If the issue persists:

1. Delete the `.archiver_shadow` folder in your project.  
2. Reload the window (`Cmd+Shift+P` → `"Reload Window"`).  
3. The extension will create a fresh, smaller repository.

Still having problems? Contact us on Slack #copilot_archiver_support!

### Q: I accidentally activated the extension on the wrong repository (e.g., from another class).

A: You can disable the extension for that workspace:

1. Open the Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`).  
2. Search `"Copilot Archiver: Disable for this Workspace"`.  
3. The extension will stop tracking that project.

You can also delete the `.archiver_shadow` folder and the `.snapshots` folder if you want to remove the tracked data.

### Q: I forgot to activate the extension on my project repository.

A: Enable it by:

1. Open your project folder in VS Code.  
2. Open the Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`).  
3. Search `"Copilot Archiver: Enable for this Workspace"`.  
4. The extension will start tracking your files.

### Q: How do I know if the extension is working?

A: Check for these signs:

- On the right of VS Code status bar, you should see “⎷ Archiver: \<your\_andrew\_id\>”.  
- A `.archiver_shadow` folder and a .snapshots folder exists in your project root.  
- In the Output panel (View → Output), select "Copilot Archiver" from the dropdown to see logs.  
- You should see messages like "ShadowGit: Committed..." when you save files.

### Q: Will this extension affect my normal git workflow?

A: No. The extension creates a separate `.archiver_shadow` folder which is automatically added to your `.gitignore`. Your main git repository is not affected.

### Q: Does this track sensitive files like passwords or API keys?

A: The extension automatically excludes .env files and other common sensitive file patterns. However, you should still follow best practices and never commit secrets to any repository.

### Q: What happens if I work offline?

A: The extension continues to track your changes locally in `.archiver_shadow`. When you're back online, it will sync to the server on the next upload cycle (every 5 minutes).  
But if you're offline, you can't chat with Copilot anyway, so there won't be much to archive.

### Q: Can I use this extension on multiple projects?

A: Yes. Each project is tracked independently. Just make sure to enable the extension for each workspace where you want tracking.

### Q: How do I completely uninstall the extension after class ends?

A: To uninstall the extension:

1. Open Extensions panel (`Cmd+Shift+X`).  
2. Find "Copilot Interaction Archiver" and click "Uninstall".  
3. Optionally, delete the `.archiver_shadow` and .snapshots folder from your projects.
