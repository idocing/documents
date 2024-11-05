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

## support functions

### Setup or Uninstall Info functions
```
function GetCmdTail: String;
function ParamCount: Integer;
function ParamStr(Index: Integer): String;

function ActiveLanguage: String;

function CustomMessage(const MsgName: String): String;
function FmtMessage(const S: String; const Args: array of String): String;
function SetupMessage(const ID: TSetupMessageID): String;

function WizardDirValue: String;
function WizardGroupValue: String;
function WizardNoIcons: Boolean;
function WizardSetupType(const Description: Boolean): String;
function WizardSelectedComponents(const Descriptions: Boolean): String;
function WizardIsComponentSelected(const Components: String): Boolean;
procedure WizardSelectComponents(const Components: String);
function WizardSelectedTasks(const Descriptions: Boolean): String;
function WizardIsTaskSelected(const Tasks: String): Boolean;
procedure WizardSelectTasks(const Tasks: String);
function WizardSilent: Boolean;

function IsUninstaller: Boolean;
function UninstallSilent: Boolean;

function CurrentFilename: String;
function CurrentSourceFilename: String;

function ExpandConstant(const S: String): String;
function ExpandConstantEx(const S: String; const CustomConst, CustomValue: String): String;

function GetPreviousData(const ValueName, DefaultValueData: String): String;
function SetPreviousData(const PreviousDataKey: Integer; const ValueName, ValueData: String): Boolean;

function Terminated: Boolean;

function RegisterExtraCloseApplicationsResource(const DisableFsRedir: Boolean; const AFilename: String): Boolean;
function RmSessionStarted: Boolean;

function GetWizardForm: TWizardForm;
function GetUninstallProgressForm: TUninstallProgressForm;
function GetMainForm: TMainForm;
```

### Exception functions
```
procedure Abort;
procedure RaiseException(const Msg: String);

function GetExceptionMessage: String;
procedure ShowExceptionMessage;
```

### System functions
```
function IsAdmin: Boolean;
function IsAdminInstallMode: Boolean;
function GetWindowsVersion: Cardinal;
procedure GetWindowsVersionEx(var Version: TWindowsVersion);
function GetWindowsVersionString: String;

function IsWin64: Boolean;
function Is64BitInstallMode: Boolean;
function ProcessorArchitecture: TSetupProcessorArchitecture;
function IsArm32Compatible: Boolean;
function IsArm64: Boolean;
function IsX64Compatible: Boolean;
function IsX64OS: Boolean;
function IsX86Compatible: Boolean;
function IsX86OS: Boolean;

function InstallOnThisVersion(const MinVersion, OnlyBelowVersion: String): Boolean;
function IsDotNetInstalled(const MinVersion: TDotNetVersion; const MinServicePack: Cardinal): Boolean;
function IsMsiProductInstalled(const UpgradeCode: String; const PackedMinVersion: Int64): Boolean;

function GetEnv(const EnvVar: String): String;
function GetUserNameString: String;
function GetComputerNameString: String;

function GetUILanguage: Integer;

function FontExists(const FaceName: String): Boolean;

function FindWindowByClassName(const ClassName: String): HWND;
function FindWindowByWindowName(const WindowName: String): HWND;
function SendMessage(const Wnd: HWND; const Msg, WParam, LParam: Longint): Longint;
function PostMessage(const Wnd: HWND; const Msg, WParam, LParam: Longint): Boolean;
function SendNotifyMessage(const Wnd: HWND; const Msg, WParam, LParam: Longint): Boolean;
function RegisterWindowMessage(const Name: String): Longint;
function SendBroadcastMessage(const Msg, WParam, LParam: Longint): Longint;
function PostBroadcastMessage(const Msg, WParam, LParam: Longint): Boolean;
function SendBroadcastNotifyMessage(const Msg, WParam, LParam: Longint): Boolean;

procedure CreateMutex(const Name: String);
function CheckForMutexes(Mutexes: String): Boolean;

procedure MakePendingFileRenameOperationsChecksum: String;

function CreateCallback(Method: AnyMethod): Longword;
procedure UnloadDLL(Filename: String);
function DLLGetLastError(): Longint;
```

### String functions
```
function Chr(B: Byte): Char;
function Ord(C: Char): Byte;
function Copy(S: String; Index, Count: Integer): String;
function Length(s: String): Longint;
function Lowercase(S: String): String;
function Uppercase(S: String): String;
function AnsiLowercase(S: String): String;
function AnsiUppercase(S: String): String;
function StringOfChar(c: Char; I : Longint): String;
procedure Delete(var S: String; Index, Count: Integer);
procedure Insert(Source: String; var Dest: String; Index: Integer);
function StringChange(var S: String; const FromStr, ToStr: String): Integer;
function StringChangeEx(var S: String; const FromStr, ToStr: String; const SupportDBCS: Boolean): Integer;
function Pos(SubStr, S: String): Integer;
function AddQuotes(const S: String): String;
function RemoveQuotes(const S: String): String;
function ConvertPercentStr(var S: String): Boolean;

function CompareText(const S1, S2: string): Integer;
function CompareStr(const S1, S2: string): Integer;
function SameText(const S1, S2: string): Boolean;
function SameStr(const S1, S2: string): Boolean;
function IsWildcard(const Pattern: String): Boolean;
function WildcardMatch(const Text, Pattern: String): Boolean;

function Format(const Format: string; const Args: array of const): string;

function Trim(const S: string): String;
function TrimLeft(const S: string): String;
function TrimRight(const S: string): String;

function StrToIntDef(s: string; def: Longint): Longint;
function StrToInt(s: string): Longint;
function StrToInt64Def(s: string; def: Int64): Int64;
function StrToInt64(s: string): Int64;
function StrToFloat(s: string): Extended;
function IntToStr(i: Int64): String;
function FloatToStr(e: extended): String;

function CharLength(const S: String; const Index: Integer): Integer;

function AddBackslash(const S: String): String;
function RemoveBackslashUnlessRoot(const S: String): String;
function RemoveBackslash(const S: String): String;
function AddPeriod(const S: String): String;
function ChangeFileExt(const FileName, Extension: string): String;
function ExtractFileExt(const FileName: string): String;
function ExtractFileDir(const FileName: string): String;
function ExtractFilePath(const FileName: string): String;
function ExtractFileName(const FileName: string): String;
function ExtractFileDrive(const FileName: string): String;
function ExtractRelativePath(const BaseName, DestName: String): String;
function ExpandFileName(const FileName: string): String;
function ExpandUNCFileName(const FileName: string): String;

function GetDateTimeString(const DateTimeFormat: String; const DateSeparator, TimeSeparator: Char): String;

procedure SetLength(var S: String; L: Longint);
procedure CharToOemBuff(var S: AnsiString);
procedure OemToCharBuff(var S: AnsiString);
function Utf8Encode(const S: String): AnsiString;
function Utf8Decode(const S: AnsiString): String;

function GetMD5OfString(const S: AnsiString): String;
function GetMD5OfUnicodeString(const S: String): String;
function GetSHA1OfString(const S: AnsiString): String;
function GetSHA1OfUnicodeString(const S: String): String;
function GetSHA256OfString(const S: AnsiString): String;
function GetSHA256OfUnicodeString(const S: String): String;

function SysErrorMessage(ErrorCode: Integer): String;

function MinimizePathName(const Filename: String; const Font: TFont; MaxLen: Integer): String;
```

### Array functions
```
function GetArrayLength(var Arr: Array): Longint;
procedure SetArrayLength(var Arr: Array; I: Longint);
```

### Variant functions
```
function Null: Variant;
function Unassigned: Variant;

function VarIsEmpty(const V: Variant): Boolean;
function VarIsClear(const V: Variant): Boolean;
function VarIsNull(const V: Variant): Boolean;
function VarType(const V: Variant): TVarType;
```

### File System functions
```
function DirExists(const Name: String): Boolean;
function FileExists(const Name: String): Boolean;
function FileOrDirExists(const Name: String): Boolean;
function FileSize(const Name: String; var Size: Integer): Boolean;
function FileSize64(const Name: String; var Size: Int64): Boolean;
function GetSpaceOnDisk(const Path: String; const InMegabytes: Boolean; var Free, Total: Cardinal): Boolean;
function GetSpaceOnDisk64(const Path: String; var Free, Total: Int64): Boolean;

function FileSearch(const Name, DirList: string): String;
function FindFirst(const FileName: String; var FindRec: TFindRec): Boolean;
function FindNext(var FindRec: TFindRec): Boolean;
procedure FindClose(var FindRec: TFindRec);

function GetCurrentDir: String;
function SetCurrentDir(const Dir: string): Boolean;
function GetWinDir: String;
function GetSystemDir: String;
function GetSysWow64Dir: String;
function GetTempDir: String;
function GetShellFolderByCSIDL(const Folder: Integer; const Create: Boolean): String;

function GetShortName(const LongName: String): String;
function GenerateUniqueName(Path: String; const Extension: String): String;

function IsProtectedSystemFile(const Filename: String): Boolean;

function GetMD5OfFile(const Filename: String): String;
function GetSHA1OfFile(const Filename: String): String;
function GetSHA256OfFile(const Filename: String): String;

function EnableFsRedirection(const Enable: Boolean): Boolean;
```

### File functions
```
function Exec(const Filename, Params, WorkingDir: String; const ShowCmd: Integer; const Wait: TExecWait; var ResultCode: Integer): Boolean;
function ExecAsOriginalUser(const Filename, Params, WorkingDir: String; const ShowCmd: Integer; const Wait: TExecWait; var ResultCode: Integer): Boolean;
function ShellExec(const Verb, Filename, Params, WorkingDir: String; const ShowCmd: Integer; const Wait: TExecWait; var ErrorCode: Integer): Boolean;
function ShellExecAsOriginalUser(const Verb, Filename, Params, WorkingDir: String; const ShowCmd: Integer; const Wait: TExecWait; var ErrorCode: Integer): Boolean;

procedure ExtractTemporaryFile(const FileName: String);
function ExtractTemporaryFiles(const Pattern: String): Integer;
function DownloadTemporaryFile(const Url, FileName, RequiredSHA256OfFile: String; const OnDownloadProgress: TOnDownloadProgress): Int64;
procedure SetDownloadCredentials(const User, Pass: String);
function DownloadTemporaryFileSize(const Url): Int64;
function DownloadTemporaryFileDate(const Url): String;

function RenameFile(const OldName, NewName: string): Boolean;
function FileCopy(const ExistingFile, NewFile: String; const FailIfExists: Boolean): Boolean;
function DeleteFile(const FileName: string): Boolean;
procedure DelayDeleteFile(const Filename: String; const Tries: Integer);
function SetNTFSCompression(const FileOrDir: String; Compress: Boolean): Boolean;

function LoadStringFromFile(const FileName: String; var S: AnsiString): Boolean;
function LoadStringFromLockedFile(const FileName: String; var S: AnsiString): Boolean;
function LoadStringsFromFile(const FileName: String; var S: TArrayOfString): Boolean;
function LoadStringsFromLockedFile(const FileName: String; var S: TArrayOfString): Boolean;
function SaveStringToFile(const FileName: String; const S: AnsiString; const Append: Boolean): Boolean;
function SaveStringsToFile(const FileName: String; const S: TArrayOfString; const Append: Boolean): Boolean;
function SaveStringsToUTF8File(const FileName: String; const S: TArrayOfString; const Append: Boolean): Boolean;
function SaveStringsToUTF8FileWithoutBOM(const FileName: String; const S: TArrayOfString; const Append: Boolean): Boolean;

function CreateDir(const Dir: string): Boolean;
function ForceDirectories(Dir: string): Boolean;
function RemoveDir(const Dir: string): Boolean;
function DelTree(const Path: String; const IsDir, DeleteFiles, DeleteSubdirsAlso: Boolean): Boolean;

function CreateShellLink(const Filename, Description, ShortcutTo, Parameters, WorkingDir, IconFilename: String; const IconIndex, ShowCmd: Integer): String;
function UnpinShellLink(const Filename: String): Boolean;

procedure RegisterServer(const Is64Bit: Boolean; const Filename: String; const FailCriticalErrors: Boolean);
function UnregisterServer(const Is64Bit: Boolean; const Filename: String; const FailCriticalErrors: Boolean): Boolean;
procedure RegisterTypeLibrary(const Is64Bit: Boolean; const Filename: String);
function UnregisterTypeLibrary(const Is64Bit: Boolean; const Filename: String): Boolean
procedure IncrementSharedCount(const Is64Bit: Boolean; const Filename: String; const AlreadyExisted: Boolean);
function DecrementSharedCount(const Is64Bit: Boolean; const Filename: String): Boolean;
procedure RestartReplace(const TempFile, DestFile: String);
procedure UnregisterFont(const FontName, FontFilename: String; const PerUserFont: Boolean);
function ModifyPifFile(const Filename: String; const CloseOnExit: Boolean): Boolean;
```

### File Version functions
```
function GetVersionNumbers(const Filename: String; var VersionMS, VersionLS: Cardinal): Boolean;
function GetVersionComponents(const Filename: String; var Major, Minor, Revision, Build: Word): Boolean;
function GetVersionNumbersString(const Filename: String; var Version: String): Boolean;
function GetPackedVersion(const Filename: String; var Version: Int64): Boolean;

function PackVersionNumbers(const VersionMS, VersionLS: Cardinal): Int64;
function PackVersionComponents(const Major, Minor, Revision, Build: Word): Int64;

function ComparePackedVersion(const Version1, Version2: Int64): Integer;
function SamePackedVersion(const Version1, Version2: Int64): Boolean;

procedure UnpackVersionNumbers(const Version: Int64; var VersionMS, VersionLS: Cardinal);
procedure UnpackVersionComponents(const Version: Int64; var Major, Minor, Revision, Build: Word);

function VersionToStr(const Version: Int64): String;
function StrToVersion(const Version: String; var Version: Int64): Boolean;
```

### Registry functions
```
function RegKeyExists(const RootKey: Integer; const SubKeyName: String): Boolean;
function RegValueExists(const RootKey: Integer; const SubKeyName, ValueName: String): Boolean;

function RegGetSubkeyNames(const RootKey: Integer; const SubKeyName: String; var Names: TArrayOfString): Boolean;
function RegGetValueNames(const RootKey: Integer; const SubKeyName: String; var Names: TArrayOfString): Boolean;

function RegQueryStringValue(const RootKey: Integer; const SubKeyName, ValueName: String; var ResultStr: String): Boolean;
function RegQueryMultiStringValue(const RootKey: Integer; const SubKeyName, ValueName: String; var ResultStr: String): Boolean;
function RegQueryDWordValue(const RootKey: Integer; const SubKeyName, ValueName: String; var ResultDWord: Cardinal): Boolean;
function RegQueryBinaryValue(const RootKey: Integer; const SubKeyName, ValueName: String; var ResultStr: AnsiString): Boolean;

function RegWriteStringValue(const RootKey: Integer; const SubKeyName, ValueName, Data: String): Boolean;
function RegWriteExpandStringValue(const RootKey: Integer; const SubKeyName, ValueName, Data: String): Boolean;
function RegWriteMultiStringValue(const RootKey: Integer; const SubKeyName, ValueName, Data: String): Boolean;
function RegWriteDWordValue(const RootKey: Integer; const SubKeyName, ValueName: String; const Data: Cardinal): Boolean;
function RegWriteBinaryValue(const RootKey: Integer; const SubKeyName, ValueName: String; const Data: AnsiString): Boolean;

function RegDeleteKeyIncludingSubkeys(const RootKey: Integer; const SubkeyName: String): Boolean;
function RegDeleteKeyIfEmpty(const RootKey: Integer; const SubkeyName: String): Boolean;
function RegDeleteValue(const RootKey: Integer; const SubKeyName, ValueName: String): Boolean;
```

### INI File functions
```
function IniKeyExists(const Section, Key, Filename: String): Boolean;
function IsIniSectionEmpty(const Section, Filename: String): Boolean;

function GetIniBool(const Section, Key: String; const Default: Boolean; const Filename: String): Boolean
function GetIniInt(const Section, Key: String; const Default, Min, Max: Longint; const Filename: String): Longint;
function GetIniString(const Section, Key, Default, Filename: String): String;

function SetIniBool(const Section, Key: String; const Value: Boolean; const Filename: String): Boolean;
function SetIniInt(const Section, Key: String; const Value: Longint; const Filename: String): Boolean;
function SetIniString(const Section, Key, Value, Filename: String): Boolean;

procedure DeleteIniSection(const Section, Filename: String);
procedure DeleteIniEntry(const Section, Key, Filename: String);
```

### Custom Setup Wizard Page functions
```
function CreateInputQueryPage(const AfterID: Integer; const ACaption, ADescription, ASubCaption: String): TInputQueryWizardPage;
function CreateInputOptionPage(const AfterID: Integer; const ACaption, ADescription, ASubCaption: String; Exclusive, ListBox: Boolean): TInputOptionWizardPage;
function CreateInputDirPage(const AfterID: Integer; const ACaption, ADescription, ASubCaption: String; AAppendDir: Boolean; ANewFolderName: String): TInputDirWizardPage;
function CreateInputFilePage(const AfterID: Integer; const ACaption, ADescription, ASubCaption: String): TInputFileWizardPage;
function CreateOutputMsgPage(const AfterID: Integer; const ACaption, ADescription, AMsg: String): TOutputMsgWizardPage;
function CreateOutputMsgMemoPage(const AfterID: Integer; const ACaption, ADescription, ASubCaption: String; const AMsg: AnsiString): TOutputMsgMemoWizardPage;
function CreateOutputProgressPage(const ACaption, ADescription: String): TOutputProgressWizardPage;
function CreateOutputMarqueeProgressPage(const ACaption, ADescription: String): TOutputMarqueeProgressWizardPage;
function CreateDownloadPage(const ACaption, ADescription: String; const OnDownloadProgress: TOnDownloadProgress): TDownloadWizardPage;
function CreateCustomPage(const AfterID: Integer; const ACaption, ADescription: String): TWizardPage;

function CreateCustomForm: TSetupForm;

function PageFromID(const ID: Integer): TWizardPage;
function PageIndexFromID(const ID: Integer): Integer;
function ScaleX(X: Integer): Integer;
function ScaleY(Y: Integer): Integer;
function InitializeBitmapImageFromIcon(const BitmapImage: TBitmapImage; const IconFilename: String; const BkColor: TColor; const AscendingTrySizes: TArrayOfInteger): Boolean;
```

### Dialog functions
```
function MsgBox(const Text: String; const Typ: TMsgBoxType; const Buttons: Integer): Integer;
function SuppressibleMsgBox(const Text: String; const Typ: TMsgBoxType; const Buttons, Default: Integer): Integer;
function TaskDialogMsgBox(const Instruction, Text: String; const Typ: TMsgBoxType; const Buttons: Cardinal; const ButtonLabels: TArrayOfString; const ShieldButton: Integer): Integer;
function SuppressibleTaskDialogMsgBox(const Instruction, Text: String; const Typ: TMsgBoxType; const Buttons: Cardinal; const ButtonLabels: TArrayOfString; const ShieldButton: Integer; const Default: Integer): Integer;
function GetOpenFileName(const Prompt: String; var FileName: String; const InitialDirectory, Filter, DefaultExtension: String): Boolean;
function GetOpenFileNameMulti(const Prompt: String; var FileNameList: TStrings; const InitialDirectory, Filter, DefaultExtension: String): Boolean;
function GetSaveFileName(const Prompt: String; var FileName: String; const InitialDirectory, Filter, DefaultExtension: String): Boolean;
function BrowseForFolder(const Prompt: String; var Directory: String; const NewFolderButton: Boolean): Boolean;
function ExitSetupMsgBox: Boolean;
function SelectDisk(const DiskNumber: Integer; const AFilename: String; var Path: String): Boolean;
```

### COM Automation objects support functions
```
function CreateOleObject(const ClassName: string): Variant;
function GetActiveOleObject(const ClassName: string): Variant;
function IDispatchInvoke(Self: IDispatch; PropertySet: Boolean; const Name: String; Par: array of Variant): Variant;
function CreateComObject(const ClassID: TGUID): IUnknown;
function StringToGUID(const S: String): TGUID;
procedure OleCheck(Result: HResult);
procedure CoFreeUnusedLibraries;
```

### Setup logging functions
```
procedure Log(const S: String);
function ExecAndLogOutput(const Filename, Params, WorkingDir: String; const ShowCmd: Integer; const Wait: TExecWait; var ResultCode: Integer; const OnLog: TOnLog): Boolean;
```

### Other functions
```
procedure Sleep(const Milliseconds: LongInt);
function Random(const Range: Integer): Integer;
procedure Beep;
procedure Set8087CW(NewCW: Word);
function Get8087CW: Word;
procedure BringToFrontAndRestore;
```
