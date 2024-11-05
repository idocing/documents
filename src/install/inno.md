# inno setup

## kill task
```
[Code]
procedure KillTask();
var ResultCode: Integer;
begin
    Exec('taskkill', '/f /im task.exe', '', SW_HIDE, ewWaitUntilTerminated, ResultCode);
end;
```

```
#define MyAppName "task"
#define MyAppExeName "task.exe"

[Code]
procedure KillTask();
var ResultCode: Integer;
begin
    Exec(ExpandConstant('{sys}\taskkill.exe'), '/f /im "{#MyAppExeName}"', '', SW_HIDE, ewWaitUntilTerminated, ResultCode);
end;
```

## event functions

### install
```
function InitializeSetup(): Boolean;
procedure InitializeWizard();
procedure DeinitializeSetup();
procedure CurStepChanged(CurStep: TSetupStep);
procedure CurInstallProgressChanged(CurProgress, MaxProgress: Integer);
function NextButtonClick(CurPageID: Integer): Boolean;
function BackButtonClick(CurPageID: Integer): Boolean;
procedure CancelButtonClick(CurPageID: Integer; var Cancel, Confirm: Boolean);
function ShouldSkipPage(PageID: Integer): Boolean;
procedure CurPageChanged(CurPageID: Integer);
function CheckPassword(Password: String): Boolean;
function NeedRestart(): Boolean;
function UpdateReadyMemo(Space, NewLine, MemoUserInfoInfo, MemoDirInfo, MemoTypeInfo, MemoComponentsInfo, MemoGroupInfo, MemoTasksInfo: String): String;
procedure RegisterPreviousData(PreviousDataKey: Integer);
function CheckSerial(Serial: String): Boolean;
function GetCustomSetupExitCode: Integer;
function PrepareToInstall(var NeedsRestart: Boolean): String;
procedure RegisterExtraCloseApplicationsResources;
```

### uninstall
```
function InitializeUninstall(): Boolean;
procedure InitializeUninstallProgressForm();
procedure DeinitializeUninstall();
procedure CurUninstallStepChanged(CurUninstallStep: TUninstallStep);
function UninstallNeedRestart(): Boolean;
```
