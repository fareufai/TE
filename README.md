# Tablacus Explorer 個人設定

```
/**
 * エクスプローラー('explorer.exe)の起動を行う
 */
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
SHELL.ShellExecute('explorer.exe', '/e /root,' + DIR, '', 'open', 1);

/**
 * コマンドプロンプト(cmd.exe)の起動を行う
 */
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
SHELL.ShellExecute('cmd.exe', '/k cd ' + DIR, '', 'open', 1);

/**
 * コマンドプロンプト(cmd.exe)の起動を行う ※管理者権限
 */
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
SHELL.ShellExecute('cmd.exe', '/k cd ' + DIR, '', 'RunAs', 1);

/**
 * PowerShell(powershell.exe)の起動を行う
 */
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
SHELL.ShellExecute('powershell.exe', '-NoExit -Command cd ' + DIR, '', 'open', 1);

/**
 * PowerShell(powershell.exe)の起動を行う ※管理者権限
 */
const SHELL = new ActiveXObject('Shell.Application');
const FV = GetFolderView(Ctrl, pt);
const DIR = api.GetDisplayNameOf(FV, SHGDN_FORPARSING);
SHELL.ShellExecute('powershell.exe', '-NoExit -Command cd ' + DIR, '', 'RunAs', 1);

/**
 * タブプラス(tabplus)の切り替えを行う ※左
 */
const TC = te.Ctrl(CTRL_TC);
if (TC)  {
    ChangeTab(TC, -1);
    return S_OK;
}
return S_FALSE;

/**
 * タブプラス(tabplus)の切り替えを行う ※右
 */
const TC = te.Ctrl(CTRL_TC);
if (TC)  {
    ChangeTab(TC, 1);
    return S_OK;
}
return S_FALSE;

/**
 * 分割(split)の切り替えを行う ※左
 */
const TC = [await te.Ctrl(CTRL_TC)];
await Addons.Split.Exec2(3, TC);
const FV = await TC[0].Selected;
FV.Focus();
ChangeView(FV);

/**
 * 分割(split)の切り替えを行う ※真ん中
 */
const TC = [await te.Ctrl(CTRL_TC)];
await Addons.Split.Exec2(3, TC);
const FV = await TC[1].Selected;
FV.Focus();
ChangeView(FV);

/**
 * 分割(split)の切り替えを行う ※右
 */
const TC = [await te.Ctrl(CTRL_TC)];
await Addons.Split.Exec2(3, TC);
const FV = await TC[2].Selected;
FV.Focus();
ChangeView(FV);

/**
 * タブグループ(tabgroups)の切り替えを行う ※左
 */
const TD = te.Data;
const TG = Addons.Tabgroups;
if (TD && TG) {
  const CURRENT = await TD.Tabgroups.Click;
  const LENGTH  = await GetLength(await TD.Tabgroups.Data);
  if (CURRENT !== 1){
    TG.Change(CURRENT - 1)
  } else {
    TG.Change(LENGTH)
  }
  return S_OK;
}
return S_FALSE;

/**
 * タブグループ(tabgroups)の切り替えを行う ※右
 */
const TD = te.Data;
const TG = Addons.Tabgroups;
if (TD && TG) {
  const CURRENT = await TD.Tabgroups.Click;
  const LENGTH  = await GetLength(await TD.Tabgroups.Data);
  if (CURRENT < LENGTH){
    TG.Change(CURRENT + 1)
  } else {
    TG.Change(1)
  }
  return S_OK;
}
return S_FALSE;
```
