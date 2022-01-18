# Tablacus Explorer 個人設定
## コマンドプロンプト 実行
| キー | タイプ |
----|---- 
| Ctrl+Shift+C | JavaScript |
```
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
const RESULT = window.confirm(管理者権限で起動を行う場合は、キャンセルを押下してください。');
if (RESULT) {
  SHELL.ShellExecute('cmd.exe', '/k cd ' + DIR, '', 'open', 1);
} else {
  SHELL.ShellExecute('cmd.exe', '/k cd ' + DIR, '', 'RunAs', 1);
}
```
## PowerShell 実行
| キー | タイプ |
----|---- 
| Ctrl+Shift+P | JavaScript |
```
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
const RESULT = window.confirm('管理者権限で起動を行う場合は、キャンセルを押下してください。');
if (RESULT) {
  SHELL.ShellExecute('powershell.exe', '-NoExit -Command cd ' + DIR, '', 'open', 1);
} else {
  SHELL.ShellExecute('powershell.exe', '-NoExit -Command cd ' + DIR, '', 'RunAs', 1);
}
```
