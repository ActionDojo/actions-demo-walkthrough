# Actions Demo Walkthrough

This VS Code extension is for testing and building the Actions Playground (MVP) walkthroughs. It'll have the most up-to-date content for the Actions Playground demo.

Current state: The rough draft workflow steps are all there (Simple workflow, CI and CD) – they will need some editing to actually work

Remaining work:
- [ ] Add a final step to the "Workflows" walkthrough signifiying the demo completion
- [ ] Add a walkthrough for "Optional Challenges"

To test the plugin:
1. Open the repo in a Codespace
2. Click the "Run and Debug" icon in the sidebar
    <img width="55" alt="Screenshot 2023-01-09 at 9 24 10 PM" src="https://user-images.githubusercontent.com/26313262/211468570-0aa8c15a-79e8-4131-95f9-b865c7add0d0.png">
3. Click the green play icon at the top to run the extension for debugging 
    <img width="346" alt="Screenshot 2023-01-09 at 9 24 53 PM" src="https://user-images.githubusercontent.com/26313262/211468675-38fc68c7-27e1-427d-b831-bc411efc8f14.png">
    
Once the extension is complete, we'll need to export it as a package (vsix file) to be uploaded into the demo repository

Note: This was forked an IBM extension so it'll have a lot of unneccessary remnant code. We should recreate the extension repo from scratch.
Keep: The key files are the "package.json" file, and all of the ".md" and ".png" files in the /content folder.
