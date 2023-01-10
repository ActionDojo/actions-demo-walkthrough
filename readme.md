# Actions Demo Walkthrough

This VS Code extension is for testing and building the VS Code walkthrough extension for the Actions Playground MVP. It'll have the most up-to-date content for task list in the Actions Playground.

Current state: The rough draft workflow steps are all there (Simple workflow, CI and CD) – CD will need more editing to actually work

Remaining work:
- [ ] Add instructions for deploying to GitHub Pages (CD)
- [ ] Add a final step to the "Workflows" walkthrough for the demo completion step
- [ ] Add a walkthrough for "Optional Challenges"

To test the plugin:
1. Open the repo in Codespaces
2. Click the "Run and Debug" icon in the sidebar
    
    <img width="55" alt="Screenshot 2023-01-09 at 9 24 10 PM" src="https://user-images.githubusercontent.com/26313262/211468570-0aa8c15a-79e8-4131-95f9-b865c7add0d0.png">
3. Click the green play icon at the top to run the extension for debugging
    
    <img width="346" alt="Screenshot 2023-01-09 at 9 24 53 PM" src="https://user-images.githubusercontent.com/26313262/211468675-38fc68c7-27e1-427d-b831-bc411efc8f14.png">
4. Click the green refresh button to see any changes made to the extension 
    
    <img width="196" alt="Screenshot 2023-01-09 at 9 49 26 PM" src="https://user-images.githubusercontent.com/26313262/211471666-00c9eb56-5d57-4c35-8709-002f66e94592.png">

Once the extension is ready, we'll need to export it as a package (vsix file) to be uploaded into the demo repository

Notes to eng:
- This was forked an IBM extension so it'll have a lot of unneccessary remnant code. We should recreate this extension repo from scratch.
- Keep the "package.json" file and the "/content" folder. Everything else can be scrapped.
