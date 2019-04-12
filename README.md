# VSIssue531237
Reproduction of [Visual Studio issue 531237](https://developercommunity.visualstudio.com/content/problem/531237/nodejs-debugger-launches-wrong-startup-script.html)

Steps to reproduce:

1. Clone this repository
2. Run `npm install` in the [/VSIssue531237](/VSIssue531237) project folder
3. Open the solution in VS2017 and add a breakpoint on the `console.log('Hello world');` line of `index.js`
4. Start debugging

Instead of the breakpoint being hit in `index.js`, a breakpoint is hit in `node_modules/axios/dist/axios.js` instead, as the debugger incorrectly determines that `axios.js` should be the startup script instead of `index.js`, as seen in the output in `vscode-node-debug2.txt`:

> Launch: program 'D:\Projects\VSIssue531237\VSIssue531237\index.js' seems to be the source; launch the generated file 'd:\Projects\VSIssue531237\VSIssue531237\node_modules\axios\dist\axios.js' instead
