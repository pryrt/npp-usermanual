---
title: Macros - Task Automation
linktitle: Macros
weight: 90
---

Notepad++ is capable of recording some of your actions you perform while editing
a document, and replaying those later on to avoid having to repeat that sequence
of actions. This is called a macro and can save a great deal of time. Macros
can be played once, or multiple times, even as long as is required to run through
an entire document. You can save them for later use and assign keystrokes to
them for fast access (See [Shortcut Mapper](../preferences/#shortcut-mapper)).
Macros are sensitive to the current position of the [caret](../editing/#caret-and-cursor "typing/insertion cursor") and will (normally
speaking) operate relative to it.


## Record a macro

To record a macro, select **Macro > Start Recording** or press the  button on the
toolbar. Notepad++ will now keep track of the changes you make on a document or
certain actions you perform.

To stop recording, select **Macro > Stop Recording** or select the  button on the
toolbar. As an exception to most commands, you can toggle this behavior with a
special shortcut combination that is not listed in the menu but solely in the
Shortcut mapper (see [Shortcut Mapper](../preferences/#shortcut-mapper)).
By default, this is the combination Ctrl-Shift-R.

After the recording is stopped, it will be stored in a temporary buffer. If you
haven't performed any actions during the recording, this buffer will be cleared. If you start
recording another macro without saving your earlier work, it will be lost.

### Macro Recording Limitations

Not all commands are macro recordable.  The following commands or actions should be recordable
(based on investigations in the source code, looking for the menu commands and underlying editor
commands that are in respective lookups for menu-recordable items).

{{< details "show menu items that should be macro-recordable" >}}

```
TODO: remove cmdID and internal constant columns
https://github.com/notepad-plus-plus/notepad-plus-plus/blob/9fccb48e547d412c0b5d0a6d49068a6b02fe303b/PowerEditor/src/Notepad_plus.rc#L445
```


cmdID | internal constant                                                       | Menu                                                              | Menu Text
------|-------------------------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------
10001 | IDM_VIEW_GOTO_ANOTHER_VIEW                                              | View > Move/Clone Current Document                                | Move to Other View
10002 | IDM_VIEW_CLONE_TO_ANOTHER_VIEW                                          | View > Move/Clone Current Document                                | Clone to Other View
10003 | IDM_VIEW_GOTO_NEW_INSTANCE                                              | View > Move/Clone Current Document                                | Move to New Instance
10004 | IDM_VIEW_LOAD_IN_NEW_INSTANCE                                           | View > Move/Clone Current Document                                | Open in New Instance
10005 | IDM_VIEW_GOTO_START                                                     | View > Tab                                                        | Move to Start
10006 | IDM_VIEW_GOTO_END                                                       | View > Tab                                                        | Move to End
41001 | IDM_FILE_NEW                                                            | File                                                              | New
41003 | IDM_FILE_CLOSE                                                          | File                                                              | Close
41004 | IDM_FILE_CLOSEALL                                                       | File                                                              | Close All
41005 | IDM_FILE_CLOSEALL_BUT_CURRENT                                           | File > Close Multiple Documents                                   | Close All BUT Current Document
41006 | IDM_FILE_SAVE                                                           | File                                                              | Save
41007 | IDM_FILE_SAVEALL                                                        | File                                                              | Save All
41009 | IDM_FILE_CLOSEALL_TOLEFT                                                | File > Close Multiple Documents                                   | Close All to the Left
41014 | IDM_FILE_RELOAD                                                         | File                                                              | Reload from Disk
41018 | IDM_FILE_CLOSEALL_TORIGHT                                               | File > Close Multiple Documents                                   | Close All to the Right
41024 | IDM_FILE_CLOSEALL_UNCHANGED                                             | File > Close Multiple Documents                                   | Close All Unchanged
41026 | IDM_FILE_CLOSEALL_BUT_PINNED                                            | File > Close Multiple Documents                                   | Close All BUT Pinned Documents
42001 | IDM_EDIT_CUT                                                            | Edit                                                              | Cut
42002 | IDM_EDIT_COPY                                                           | Edit                                                              | Copy
42003 | IDM_EDIT_UNDO                                                           | Edit                                                              | Undo
42004 | IDM_EDIT_REDO                                                           | Edit                                                              | Redo
42005 | IDM_EDIT_PASTE                                                          | Edit                                                              | Paste
42006 | IDM_EDIT_DELETE                                                         | Edit                                                              | Delete
42007 | IDM_EDIT_SELECTALL                                                      | Edit                                                              | Select All
42008 | IDM_EDIT_INS_TAB                                                        | Edit > Indent                                                     | Increase Line Indent
42009 | IDM_EDIT_RMV_TAB                                                        | Edit > Indent                                                     | Decrease Line Indent
42010 | IDM_EDIT_DUP_LINE                                                       |                                                                   | Duplicate Current Line
42011 | IDM_EDIT_TRANSPOSE_LINE                                                 |                                                                   | Transpose Line
42012 | IDM_EDIT_SPLIT_LINES                                                    |                                                                   | Split Lines
42013 | IDM_EDIT_JOIN_LINES                                                     |                                                                   | Join Lines
42014 | IDM_EDIT_LINE_UP                                                        |                                                                   | Move Up Current Line
42015 | IDM_EDIT_LINE_DOWN                                                      |                                                                   | Move Down Current Line
42016 | IDM_EDIT_UPPERCASE                                                      |                                                                   | UPPERCASE
42017 | IDM_EDIT_LOWERCASE                                                      |                                                                   | lowercase
42020 | IDM_EDIT_BEGINENDSELECT                                                 |                                                                   | Begin/End Select
42022 | IDM_EDIT_BLOCK_COMMENT                                                  |                                                                   | Toggle Single Line Comment
42023 | IDM_EDIT_STREAM_COMMENT                                                 |                                                                   | Block Comment
42024 | IDM_EDIT_TRIMTRAILING                                                   |                                                                   | Trim Trailing Space
42026 | IDM_EDIT_RTL                                                            |                                                                   | Text Direction RTL
42027 | IDM_EDIT_LTR                                                            |                                                                   | Text Direction LTR
42028 | IDM_EDIT_TOGGLEREADONLY                                                 |                                                                   | Read-Only on Current Document
42029 | IDM_EDIT_FULLPATHTOCLIP                                                 |                                                                   | Copy Current File Path
42030 | IDM_EDIT_FILENAMETOCLIP                                                 |                                                                   | Copy Current Filename
42031 | IDM_EDIT_CURRENTDIRTOCLIP                                               |                                                                   | Copy Current Dir. Path
42033 | IDM_EDIT_TOGGLESYSTEMREADONLY                                           |                                                                   | Read-Only Attribute in Windows
42035 | IDM_EDIT_BLOCK_COMMENT_SET                                              |                                                                   | Single Line Comment
42036 | IDM_EDIT_BLOCK_UNCOMMENT                                                |                                                                   | Single Line Uncomment
42042 | IDM_EDIT_TRIMLINEHEAD                                                   |                                                                   | Trim Leading Space
42043 | IDM_EDIT_TRIM_BOTH                                                      |                                                                   | Trim Leading and Trailing Space
42044 | IDM_EDIT_EOL2WS                                                         |                                                                   | EOL to Space
42045 | IDM_EDIT_TRIMALL                                                        |                                                                   | Trim both and EOL to Space
42046 | IDM_EDIT_TAB2SW                                                         |                                                                   | TAB to Space
42053 | IDM_EDIT_SW2TAB_LEADING                                                 |                                                                   | Space to TAB (Leading)
42054 | IDM_EDIT_SW2TAB_ALL                                                     |                                                                   | Space to TAB (All)
42055 | IDM_EDIT_REMOVEEMPTYLINES                                               |                                                                   | Remove Empty Lines
42056 | IDM_EDIT_REMOVEEMPTYLINESWITHBLANK                                      |                                                                   | Remove Empty Lines (Containing Blank characters)
42057 | IDM_EDIT_BLANKLINEABOVECURRENT                                          |                                                                   | Insert Blank Line Above Current
42058 | IDM_EDIT_BLANKLINEBELOWCURRENT                                          |                                                                   | Insert Blank Line Below Current
42059 | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING                              |                                                                   | Sort Lines Lexicographically Ascending
42060 | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING                             |                                                                   | Sort Lines Lexicographically Descending
42061 | IDM_EDIT_SORTLINES_INTEGER_ASCENDING                                    |                                                                   | Sort Lines As Integers Ascending
42062 | IDM_EDIT_SORTLINES_INTEGER_DESCENDING                                   |                                                                   | Sort Lines As Integers Descending
42063 | IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING                               |                                                                   | Sort Lines As Decimals (Comma) Ascending
42064 | IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING                              |                                                                   | Sort Lines As Decimals (Comma) Descending
42065 | IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING                                 |                                                                   | Sort Lines As Decimals (Dot) Ascending
42066 | IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING                                |                                                                   | Sort Lines As Decimals (Dot) Descending
42067 | IDM_EDIT_PROPERCASE_FORCE                                               |                                                                   | Proper Case
42068 | IDM_EDIT_PROPERCASE_BLEND                                               |                                                                   | Proper Case (blend)
42069 | IDM_EDIT_SENTENCECASE_FORCE                                             |                                                                   | Sentence case
42070 | IDM_EDIT_SENTENCECASE_BLEND                                             |                                                                   | Sentence case (blend)
42071 | IDM_EDIT_INVERTCASE                                                     |                                                                   | iNVERT cASE
42072 | IDM_EDIT_RANDOMCASE                                                     |                                                                   | ranDOm CasE
42077 | IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES                                   |                                                                   | Remove Consecutive Duplicate Lines
42078 | IDM_EDIT_SORTLINES_RANDOMLY                                             |                                                                   | Randomize Line Order
42079 | IDM_EDIT_REMOVE_ANY_DUP_LINES                                           |                                                                   | Remove Duplicate Lines
42080 | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING                         |                                                                   | Sort Lines Lex. Ascending Ignoring Case
42081 | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING                        |                                                                   | Sort Lines Lex. Descending Ignoring Case
42083 | IDM_EDIT_SORTLINES_REVERSE_ORDER                                        |                                                                   | Reverse Line Order
42084 | IDM_EDIT_INSERT_DATETIME_SHORT                                          |                                                                   | Date Time (short)
42085 | IDM_EDIT_INSERT_DATETIME_LONG                                           |                                                                   | Date Time (long)
42086 | IDM_EDIT_INSERT_DATETIME_CUSTOMIZED                                     |                                                                   | Date Time (customized)
42087 | IDM_EDIT_COPY_ALL_NAMES                                                 |                                                                   | Copy All Filenames
42088 | IDM_EDIT_COPY_ALL_PATHS                                                 |                                                                   | Copy All File Paths
42089 | IDM_EDIT_BEGINENDSELECT_COLUMNMODE                                      |                                                                   | Begin/End Select in Column Mode
42092 | IDM_EDIT_MULTISELECTALLWHOLEWORD                                        |                                                                   | Match Whole Word Only
42093 | IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD                               |                                                                   | Match Case  Whole Word
42094 | IDM_EDIT_MULTISELECTNEXT                                                |                                                                   | Ignore Case  Whole Word
42095 | IDM_EDIT_MULTISELECTNEXTMATCHCASE                                       |                                                                   | Match Case Only
42096 | IDM_EDIT_MULTISELECTNEXTWHOLEWORD                                       |                                                                   | Match Whole Word Only
42097 | IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD                              |                                                                   | Match Case  Whole Word
42098 | IDM_EDIT_MULTISELECTUNDO                                                |                                                                   | Undo the Latest Added Multi-Select
42099 | IDM_EDIT_MULTISELECTSSKIP                                               |                                                                   | Skip Current  Go to Next Multi-select
42100 | IDM_EDIT_SORTLINES_LOCALE_ASCENDING                                     |                                                                   | Sort Lines In Locale Order Ascending
42101 | IDM_EDIT_SORTLINES_LOCALE_DESCENDING                                    |                                                                   | Sort Lines In Locale Order Descending
42102 | IDM_EDIT_SETREADONLYFORALLDOCS                                          |                                                                   | Read-Only for All Documents
42103 | IDM_EDIT_CLEARREADONLYFORALLDOCS                                        |                                                                   | Clear Read-Only for All Documents
42104 | IDM_EDIT_SORTLINES_LENGTH_ASCENDING                                     |                                                                   | Sort Lines By Length Ascending
42105 | IDM_EDIT_SORTLINES_LENGTH_DESCENDING                                    |                                                                   | Sort Lines By Length Descending
42106 | IDM_EDIT_REDACT_SELECTION                                               |                                                                   | Redact Selection █ (Shift: ●)
43002 | IDM_SEARCH_FINDNEXT                                                     |                                                                   | Find Next
43005 | IDM_SEARCH_TOGGLE_BOOKMARK                                              |                                                                   | Toggle Bookmark
43006 | IDM_SEARCH_NEXT_BOOKMARK                                                |                                                                   | Next Bookmark
43007 | IDM_SEARCH_PREV_BOOKMARK                                                |                                                                   | Previous Bookmark
43008 | IDM_SEARCH_CLEAR_BOOKMARKS                                              |                                                                   | Clear All Bookmarks
43009 | IDM_SEARCH_GOTOMATCHINGBRACE                                            |                                                                   | Go to Matching Brace
43010 | IDM_SEARCH_FINDPREV                                                     |                                                                   | Find Previous
43014 | IDM_SEARCH_VOLATILE_FINDNEXT                                            |                                                                   | Find (Volatile) Next
43015 | IDM_SEARCH_VOLATILE_FINDPREV                                            |                                                                   | Find (Volatile) Previous
43018 | IDM_SEARCH_CUTMARKEDLINES                                               |                                                                   | Cut Bookmarked Lines
43019 | IDM_SEARCH_COPYMARKEDLINES                                              |                                                                   | Copy Bookmarked Lines
43020 | IDM_SEARCH_PASTEMARKEDLINES                                             |                                                                   | Paste to (Replace) Bookmarked Lines
43021 | IDM_SEARCH_DELETEMARKEDLINES                                            |                                                                   | Remove Bookmarked Lines
43022 | IDM_SEARCH_MARKALLEXT1                                                  |                                                                   | Using 1st Style
43023 | IDM_SEARCH_UNMARKALLEXT1                                                |                                                                   | Clear 1st Style
43024 | IDM_SEARCH_MARKALLEXT2                                                  |                                                                   | Using 2nd Style
43025 | IDM_SEARCH_UNMARKALLEXT2                                                |                                                                   | Clear 2nd Style
43026 | IDM_SEARCH_MARKALLEXT3                                                  |                                                                   | Using 3rd Style
43027 | IDM_SEARCH_UNMARKALLEXT3                                                |                                                                   | Clear 3rd Style
43028 | IDM_SEARCH_MARKALLEXT4                                                  |                                                                   | Using 4th Style
43029 | IDM_SEARCH_UNMARKALLEXT4                                                |                                                                   | Clear 4th Style
43030 | IDM_SEARCH_MARKALLEXT5                                                  |                                                                   | Using 5th Style
43031 | IDM_SEARCH_UNMARKALLEXT5                                                |                                                                   | Clear 5th Style
43032 | IDM_SEARCH_CLEARALLMARKS                                                |                                                                   | Clear All Styles
43033 | IDM_SEARCH_GOPREVMARKER1                                                |                                                                   | 1st style
43034 | IDM_SEARCH_GOPREVMARKER2                                                |                                                                   | 2nd style
43035 | IDM_SEARCH_GOPREVMARKER3                                                |                                                                   | 3rd style
43036 | IDM_SEARCH_GOPREVMARKER4                                                |                                                                   | 4th style
43037 | IDM_SEARCH_GOPREVMARKER5                                                |                                                                   | 5th style
43038 | IDM_SEARCH_GOPREVMARKER_DEF                                             |                                                                   | Find Mark Style
43039 | IDM_SEARCH_GONEXTMARKER1                                                |                                                                   | 1st style
43040 | IDM_SEARCH_GONEXTMARKER2                                                |                                                                   | 2nd style
43041 | IDM_SEARCH_GONEXTMARKER3                                                |                                                                   | 3rd style
43042 | IDM_SEARCH_GONEXTMARKER4                                                |                                                                   | 4th style
43043 | IDM_SEARCH_GONEXTMARKER5                                                |                                                                   | 5th style
43044 | IDM_SEARCH_GONEXTMARKER_DEF                                             |                                                                   | Find Mark Style
43048 | IDM_SEARCH_SETANDFINDNEXT                                               |                                                                   | Select and Find Next
43049 | IDM_SEARCH_SETANDFINDPREV                                               |                                                                   | Select and Find Previous
43050 | IDM_SEARCH_INVERSEMARKS                                                 |                                                                   | Inverse Bookmarks
43051 | IDM_SEARCH_DELETEUNMARKEDLINES                                          |                                                                   | Remove Non-Bookmarked Lines
43053 | IDM_SEARCH_SELECTMATCHINGBRACES                                         |                                                                   | Select All In-between {} [] or ()
43055 | IDM_SEARCH_STYLE1TOCLIP                                                 |                                                                   | 1st Style
43056 | IDM_SEARCH_STYLE2TOCLIP                                                 |                                                                   | 2nd Style
43057 | IDM_SEARCH_STYLE3TOCLIP                                                 |                                                                   | 3rd Style
43058 | IDM_SEARCH_STYLE4TOCLIP                                                 |                                                                   | 4th Style
43059 | IDM_SEARCH_STYLE5TOCLIP                                                 |                                                                   | 5th Style
43060 | IDM_SEARCH_ALLSTYLESTOCLIP                                              |                                                                   | All Styles
43061 | IDM_SEARCH_MARKEDTOCLIP                                                 |                                                                   | Find Mark Style
43062 | IDM_SEARCH_MARKONEEXT1                                                  |                                                                   | Using 1st Style
43063 | IDM_SEARCH_MARKONEEXT2                                                  |                                                                   | Using 2nd Style
43064 | IDM_SEARCH_MARKONEEXT3                                                  |                                                                   | Using 3rd Style
43065 | IDM_SEARCH_MARKONEEXT4                                                  |                                                                   | Using 4th Style
43066 | IDM_SEARCH_MARKONEEXT5                                                  |                                                                   | Using 5th Style
44010 | IDM_VIEW_FOLDALL                                                        |                                                                   | Fold All
44022 | IDM_VIEW_WRAP                                                           |                                                                   | Word wrap
44029 | IDM_VIEW_UNFOLDALL                                                      |                                                                   | Unfold All
44030 | IDM_VIEW_FOLD_CURRENT                                                   |                                                                   | Fold Current Level
44031 | IDM_VIEW_UNFOLD_CURRENT                                                 |                                                                   | Unfold Current Level
44032 | IDM_VIEW_FULLSCREENTOGGLE                                               |                                                                   | Toggle Full Screen Mode
44034 | IDM_VIEW_ALWAYSONTOP                                                    |                                                                   | Always on Top
44035 | IDM_VIEW_SYNSCROLLV                                                     |                                                                   | Synchronise Vertical Scrolling
44036 | IDM_VIEW_SYNSCROLLH                                                     |                                                                   | Synchronise Horizontal Scrolling
44051 | IDM_VIEW_FOLD_1                                                         |                                                                   | Fold Level 1
44052 | IDM_VIEW_FOLD_2                                                         |                                                                   | Fold Level 2
44053 | IDM_VIEW_FOLD_3                                                         |                                                                   | Fold Level 3
44054 | IDM_VIEW_FOLD_4                                                         |                                                                   | Fold Level 4
44055 | IDM_VIEW_FOLD_5                                                         |                                                                   | Fold Level 5
44056 | IDM_VIEW_FOLD_6                                                         |                                                                   | Fold Level 6
44057 | IDM_VIEW_FOLD_7                                                         |                                                                   | Fold Level 7
44058 | IDM_VIEW_FOLD_8                                                         |                                                                   | Fold Level 8
44061 | IDM_VIEW_UNFOLD_1                                                       |                                                                   | Unfold Level 1
44062 | IDM_VIEW_UNFOLD_2                                                       |                                                                   | Unfold Level 2
44063 | IDM_VIEW_UNFOLD_3                                                       |                                                                   | Unfold Level 3
44064 | IDM_VIEW_UNFOLD_4                                                       |                                                                   | Unfold Level 4
44065 | IDM_VIEW_UNFOLD_5                                                       |                                                                   | Unfold Level 5
44066 | IDM_VIEW_UNFOLD_6                                                       |                                                                   | Unfold Level 6
44067 | IDM_VIEW_UNFOLD_7                                                       |                                                                   | Unfold Level 7
44068 | IDM_VIEW_UNFOLD_8                                                       |                                                                   | Unfold Level 8
44086 | IDM_VIEW_TAB1                                                           |                                                                   | 1st Tab
44087 | IDM_VIEW_TAB2                                                           |                                                                   | 2nd Tab
44088 | IDM_VIEW_TAB3                                                           |                                                                   | 3rd Tab
44089 | IDM_VIEW_TAB4                                                           |                                                                   | 4th Tab
44090 | IDM_VIEW_TAB5                                                           |                                                                   | 5th Tab
44091 | IDM_VIEW_TAB6                                                           |                                                                   | 6th Tab
44092 | IDM_VIEW_TAB7                                                           |                                                                   | 7th Tab
44093 | IDM_VIEW_TAB8                                                           |                                                                   | 8th Tab
44094 | IDM_VIEW_TAB9                                                           |                                                                   | 9th Tab
44095 | IDM_VIEW_TAB_NEXT                                                       |                                                                   | Next Tab
44096 | IDM_VIEW_TAB_PREV                                                       |                                                                   | Previous Tab
44098 | IDM_VIEW_TAB_MOVEFORWARD                                                |                                                                   | Move Tab Forward
44099 | IDM_VIEW_TAB_MOVEBACKWARD                                               |                                                                   | Move Tab Backward
44100 | IDM_VIEW_IN_FIREFOX                                                     |                                                                   | View in Firefox
44101 | IDM_VIEW_IN_CHROME                                                      |                                                                   | View in Chrome
44102 | IDM_VIEW_IN_EDGE                                                        |                                                                   | View in Edge
44103 | IDM_VIEW_IN_IE                                                          |                                                                   | View in IE
45001 | IDM_FORMAT_TODOS                                                        |                                                                   | Windows (CR LF)
45002 | IDM_FORMAT_TOUNIX                                                       |                                                                   | Unix (LF)
45003 | IDM_FORMAT_TOMAC                                                        |                                                                   | Macintosh (CR)
50003 | IDC_PREV_DOC                                                            |                                                                   | Switch to previous document
50004 | IDC_NEXT_DOC                                                            |                                                                   | Switch to next document


```
TODO NEXT:
UNFORTUNATELY, A LOT OF THE ONES FROM THE MENUCMDID.H DIDN'T END UP IN MY ORIGINAL TABLE
(I DON'T KNOW WHETHER THERE WAS A REGEX PROBLEM OR A COPY/PASTE ISSUE OR WHAT, BECAUSE THEY SHOULD HAVE ALL BEEN THERE....)
SAVE THIS FOR NOW, AND COME BACK... WILL HAVE TO REGRAB THE NAMES FROM ENGLISH.XML AS WELL :-(

FIND = ^(?=(IDM_\w+)\b :: MENUITEM(?s).*(?-s)(^\d{5} . \b\1\b.*$))
REPL = $2

POPUP "&File"
41001 | IDM_FILE_NEW                                                            | File                                                              | New                                                                                       |     IDM_FILE_NEW :: MENUITEM "&New",                             IDM_FILE_NEW
41001 | IDM_FILE_OPEN                                                           | File                                                              | Open                                                                                      | IDM_FILE_OPEN :: MENUITEM "&Open...",                         IDM_FILE_OPEN
POPUP "Open Containing &Folder"
IDM_FILE_OPEN_FOLDER :: MENUITEM "Explorer",       IDM_FILE_OPEN_FOLDER
IDM_FILE_OPEN_CMD :: MENUITEM "cmd",            IDM_FILE_OPEN_CMD
IDM_FILE_OPEN_POWERSHELL :: MENUITEM "PowerShell",     IDM_FILE_OPEN_POWERSHELL
IDM_FILE_CONTAININGFOLDERASWORKSPACE :: MENUITEM "Folder as Workspace", IDM_FILE_CONTAININGFOLDERASWORKSPACE
IDM_FILE_OPEN_DEFAULT_VIEWER :: MENUITEM "Open in &Default Viewer",          IDM_FILE_OPEN_DEFAULT_VIEWER
IDM_FILE_OPENFOLDERASWORKSPACE :: MENUITEM "Open Folder as &Workspace...",     IDM_FILE_OPENFOLDERASWORKSPACE
41014 | IDM_FILE_RELOAD                                                         | File                                                              | Reload from Disk                                                                          |     IDM_FILE_RELOAD :: MENUITEM "Re&load from Disk",                IDM_FILE_RELOAD
41006 | IDM_FILE_SAVE                                                           | File                                                              | Save                                                                                      |     IDM_FILE_SAVE :: MENUITEM "&Save",                            IDM_FILE_SAVE
IDM_FILE_SAVEAS :: MENUITEM "Save &As...",                      IDM_FILE_SAVEAS
IDM_FILE_SAVECOPYAS :: MENUITEM "Save a Cop&y As...",               IDM_FILE_SAVECOPYAS
41007 | IDM_FILE_SAVEALL                                                        | File                                                              | Save All                                                                                  |     IDM_FILE_SAVEALL :: MENUITEM "Sa&ve All",                        IDM_FILE_SAVEALL
IDM_FILE_RENAME :: MENUITEM "&Rename...",                       IDM_FILE_RENAME
41003 | IDM_FILE_CLOSE                                                          | File                                                              | Close                                                                                     |     IDM_FILE_CLOSE :: MENUITEM "&Close",                           IDM_FILE_CLOSE
41004 | IDM_FILE_CLOSEALL                                                       | File                                                              | Close All                                                                                 |     IDM_FILE_CLOSEALL :: MENUITEM "Clos&e All",                       IDM_FILE_CLOSEALL
POPUP "Close &Multiple Documents"
41005 | IDM_FILE_CLOSEALL_BUT_CURRENT                                           | File > Close Multiple Documents                                   | Close All BUT Current Document                                                            |         IDM_FILE_CLOSEALL_BUT_CURRENT :: MENUITEM "Close All but Active Document",    IDM_FILE_CLOSEALL_BUT_CURRENT
41026 | IDM_FILE_CLOSEALL_BUT_PINNED                                            | File > Close Multiple Documents                                   | Close All BUT Pinned Documents                                                            |         IDM_FILE_CLOSEALL_BUT_PINNED :: MENUITEM "Close All but Pinned Documents",   IDM_FILE_CLOSEALL_BUT_PINNED
41009 | IDM_FILE_CLOSEALL_TOLEFT                                                | File > Close Multiple Documents                                   | Close All to the Left                                                                     |         IDM_FILE_CLOSEALL_TOLEFT :: MENUITEM "Close All to the Left",            IDM_FILE_CLOSEALL_TOLEFT
41018 | IDM_FILE_CLOSEALL_TORIGHT                                               | File > Close Multiple Documents                                   | Close All to the Right                                                                    |         IDM_FILE_CLOSEALL_TORIGHT :: MENUITEM "Close All to the Right",           IDM_FILE_CLOSEALL_TORIGHT
41024 | IDM_FILE_CLOSEALL_UNCHANGED                                             | File > Close Multiple Documents                                   | Close All Unchanged                                                                       |         IDM_FILE_CLOSEALL_UNCHANGED :: MENUITEM "Close All Unchanged",              IDM_FILE_CLOSEALL_UNCHANGED
IDM_FILE_DELETE :: MENUITEM "Move to Recycle &Bin",             IDM_FILE_DELETE
IDM_FILE_LOADSESSION :: MENUITEM "Load Sess&ion...",                 IDM_FILE_LOADSESSION
IDM_FILE_SAVESESSION :: MENUITEM "Save Sess&ion...",                 IDM_FILE_SAVESESSION
IDM_FILE_PRINT :: MENUITEM "&Print...",                        IDM_FILE_PRINT
IDM_FILE_PRINTNOW :: MENUITEM "Print No&w",                       IDM_FILE_PRINTNOW
IDM_FILE_EXIT :: MENUITEM "E&xit",                            IDM_FILE_EXIT
POPUP "&Edit"
42003 | IDM_EDIT_UNDO                                                           | Edit                                                              | Undo                                                                                      |     IDM_EDIT_UNDO :: MENUITEM "&Undo",                            IDM_EDIT_UNDO
42004 | IDM_EDIT_REDO                                                           | Edit                                                              | Redo                                                                                      |     IDM_EDIT_REDO :: MENUITEM "&Redo",                            IDM_EDIT_REDO
42001 | IDM_EDIT_CUT                                                            | Edit                                                              | Cut                                                                                       |     IDM_EDIT_CUT :: MENUITEM "Cu&t",                             IDM_EDIT_CUT
42002 | IDM_EDIT_COPY                                                           | Edit                                                              | Copy                                                                                      |     IDM_EDIT_COPY :: MENUITEM "&Copy",                            IDM_EDIT_COPY
42005 | IDM_EDIT_PASTE                                                          | Edit                                                              | Paste                                                                                     |     IDM_EDIT_PASTE :: MENUITEM "&Paste",                           IDM_EDIT_PASTE
42006 | IDM_EDIT_DELETE                                                         | Edit                                                              | Delete                                                                                    |     IDM_EDIT_DELETE :: MENUITEM "&Delete",                          IDM_EDIT_DELETE
42007 | IDM_EDIT_SELECTALL                                                      | Edit                                                              | Select All                                                                                |     IDM_EDIT_SELECTALL :: MENUITEM "&Select All",                      IDM_EDIT_SELECTALL
42020 | IDM_EDIT_BEGINENDSELECT                                                 |                                                                   | Begin/End Select                                                                          |     IDM_EDIT_BEGINENDSELECT :: MENUITEM "Begin/End &Select",                IDM_EDIT_BEGINENDSELECT
42089 | IDM_EDIT_BEGINENDSELECT_COLUMNMODE                                      |                                                                   | Begin/End Select in Column Mode                                                           |     IDM_EDIT_BEGINENDSELECT_COLUMNMODE :: MENUITEM "Begin/End Select in Column Mode",  IDM_EDIT_BEGINENDSELECT_COLUMNMODE
POPUP "Insert"
42084 | IDM_EDIT_INSERT_DATETIME_SHORT                                          |                                                                   | Date Time (short)                                                                         |             IDM_EDIT_INSERT_DATETIME_SHORT :: MENUITEM "Date Time (short)",        IDM_EDIT_INSERT_DATETIME_SHORT
42085 | IDM_EDIT_INSERT_DATETIME_LONG                                           |                                                                   | Date Time (long)                                                                          |             IDM_EDIT_INSERT_DATETIME_LONG :: MENUITEM "Date Time (long)",         IDM_EDIT_INSERT_DATETIME_LONG
42086 | IDM_EDIT_INSERT_DATETIME_CUSTOMIZED                                     |                                                                   | Date Time (customized)                                                                    |             IDM_EDIT_INSERT_DATETIME_CUSTOMIZED :: MENUITEM "Date Time (customized)",   IDM_EDIT_INSERT_DATETIME_CUSTOMIZED
POPUP "Cop&y to Clipboard"
42029 | IDM_EDIT_FULLPATHTOCLIP                                                 |                                                                   | Copy Current File Path                                                                    |             IDM_EDIT_FULLPATHTOCLIP :: MENUITEM "Copy Current Full File path",    IDM_EDIT_FULLPATHTOCLIP
42030 | IDM_EDIT_FILENAMETOCLIP                                                 |                                                                   | Copy Current Filename                                                                     |             IDM_EDIT_FILENAMETOCLIP :: MENUITEM "Copy Current Filename",          IDM_EDIT_FILENAMETOCLIP
42031 | IDM_EDIT_CURRENTDIRTOCLIP                                               |                                                                   | Copy Current Dir. Path                                                                    |             IDM_EDIT_CURRENTDIRTOCLIP :: MENUITEM "Copy Current Dir. Path",         IDM_EDIT_CURRENTDIRTOCLIP
42087 | IDM_EDIT_COPY_ALL_NAMES                                                 |                                                                   | Copy All Filenames                                                                        |             IDM_EDIT_COPY_ALL_NAMES :: MENUITEM "Copy All Filenames",             IDM_EDIT_COPY_ALL_NAMES
42088 | IDM_EDIT_COPY_ALL_PATHS                                                 |                                                                   | Copy All File Paths                                                                       |             IDM_EDIT_COPY_ALL_PATHS :: MENUITEM "Copy All File Paths",            IDM_EDIT_COPY_ALL_PATHS
POPUP "&Indent"
42008 | IDM_EDIT_INS_TAB                                                        | Edit > Indent                                                     | Increase Line Indent                                                                      |         IDM_EDIT_INS_TAB :: MENUITEM "Increase Line Indent",    IDM_EDIT_INS_TAB
42009 | IDM_EDIT_RMV_TAB                                                        | Edit > Indent                                                     | Decrease Line Indent                                                                      |         IDM_EDIT_RMV_TAB :: MENUITEM "Decrease Line Indent",    IDM_EDIT_RMV_TAB
POPUP "Con&vert Case to"
42016 | IDM_EDIT_UPPERCASE                                                      |                                                                   | UPPERCASE                                                                                 |         IDM_EDIT_UPPERCASE :: MENUITEM "&UPPERCASE",              IDM_EDIT_UPPERCASE
42017 | IDM_EDIT_LOWERCASE                                                      |                                                                   | lowercase                                                                                 |         IDM_EDIT_LOWERCASE :: MENUITEM "&lowercase",              IDM_EDIT_LOWERCASE
42067 | IDM_EDIT_PROPERCASE_FORCE                                               |                                                                   | Proper Case                                                                               |         IDM_EDIT_PROPERCASE_FORCE :: MENUITEM "&Proper Case",            IDM_EDIT_PROPERCASE_FORCE
42068 | IDM_EDIT_PROPERCASE_BLEND                                               |                                                                   | Proper Case (blend)                                                                       |         IDM_EDIT_PROPERCASE_BLEND :: MENUITEM "Proper Case (blend)",      IDM_EDIT_PROPERCASE_BLEND
42069 | IDM_EDIT_SENTENCECASE_FORCE                                             |                                                                   | Sentence case                                                                             |         IDM_EDIT_SENTENCECASE_FORCE :: MENUITEM "&Sentence case",          IDM_EDIT_SENTENCECASE_FORCE
42070 | IDM_EDIT_SENTENCECASE_BLEND                                             |                                                                   | Sentence case (blend)                                                                     |         IDM_EDIT_SENTENCECASE_BLEND :: MENUITEM "Sentence case (blend)",   IDM_EDIT_SENTENCECASE_BLEND
42071 | IDM_EDIT_INVERTCASE                                                     |                                                                   | iNVERT cASE                                                                               |         IDM_EDIT_INVERTCASE :: MENUITEM "&iNVERT cASE",             IDM_EDIT_INVERTCASE
42072 | IDM_EDIT_RANDOMCASE                                                     |                                                                   | ranDOm CasE                                                                               |         IDM_EDIT_RANDOMCASE :: MENUITEM "&ranDOm CasE",             IDM_EDIT_RANDOMCASE
POPUP "&Line Operations"
42010 | IDM_EDIT_DUP_LINE                                                       |                                                                   | Duplicate Current Line                                                                    |         IDM_EDIT_DUP_LINE :: MENUITEM "Duplicate Current Line",                           IDM_EDIT_DUP_LINE
42079 | IDM_EDIT_REMOVE_ANY_DUP_LINES                                           |                                                                   | Remove Duplicate Lines                                                                    |         IDM_EDIT_REMOVE_ANY_DUP_LINES :: MENUITEM "Remove Duplicate Lines",                           IDM_EDIT_REMOVE_ANY_DUP_LINES
42077 | IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES                                   |                                                                   | Remove Consecutive Duplicate Lines                                                        |         IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES :: MENUITEM "Remove Consecutive Duplicate Lines",               IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES
42012 | IDM_EDIT_SPLIT_LINES                                                    |                                                                   | Split Lines                                                                               |         IDM_EDIT_SPLIT_LINES :: MENUITEM "Split Lines",                                      IDM_EDIT_SPLIT_LINES
42013 | IDM_EDIT_JOIN_LINES                                                     |                                                                   | Join Lines                                                                                |         IDM_EDIT_JOIN_LINES :: MENUITEM "Join Lines",                                       IDM_EDIT_JOIN_LINES
42014 | IDM_EDIT_LINE_UP                                                        |                                                                   | Move Up Current Line                                                                      |         IDM_EDIT_LINE_UP :: MENUITEM "Move Up Current Line",                             IDM_EDIT_LINE_UP
42015 | IDM_EDIT_LINE_DOWN                                                      |                                                                   | Move Down Current Line                                                                    |         IDM_EDIT_LINE_DOWN :: MENUITEM "Move Down Current Line",                           IDM_EDIT_LINE_DOWN
42055 | IDM_EDIT_REMOVEEMPTYLINES                                               |                                                                   | Remove Empty Lines                                                                        |         IDM_EDIT_REMOVEEMPTYLINES :: MENUITEM "Remove Empty Lines",                               IDM_EDIT_REMOVEEMPTYLINES
42056 | IDM_EDIT_REMOVEEMPTYLINESWITHBLANK                                      |                                                                   | Remove Empty Lines (Containing Blank characters)                                          |         IDM_EDIT_REMOVEEMPTYLINESWITHBLANK :: MENUITEM "Remove Empty Lines (Containing Blank characters)", IDM_EDIT_REMOVEEMPTYLINESWITHBLANK
42057 | IDM_EDIT_BLANKLINEABOVECURRENT                                          |                                                                   | Insert Blank Line Above Current                                                           |         IDM_EDIT_BLANKLINEABOVECURRENT :: MENUITEM "Insert Blank Line Above Current",                  IDM_EDIT_BLANKLINEABOVECURRENT
42058 | IDM_EDIT_BLANKLINEBELOWCURRENT                                          |                                                                   | Insert Blank Line Below Current                                                           |         IDM_EDIT_BLANKLINEBELOWCURRENT :: MENUITEM "Insert Blank Line Below Current",                  IDM_EDIT_BLANKLINEBELOWCURRENT
42083 | IDM_EDIT_SORTLINES_REVERSE_ORDER                                        |                                                                   | Reverse Line Order                                                                        |         IDM_EDIT_SORTLINES_REVERSE_ORDER :: MENUITEM "Reverse Line Order",                               IDM_EDIT_SORTLINES_REVERSE_ORDER
42078 | IDM_EDIT_SORTLINES_RANDOMLY                                             |                                                                   | Randomize Line Order                                                                      |         IDM_EDIT_SORTLINES_RANDOMLY :: MENUITEM "Randomize Line Order",                             IDM_EDIT_SORTLINES_RANDOMLY
42059 | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING                              |                                                                   | Sort Lines Lexicographically Ascending                                                    |         IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING :: MENUITEM "Sort Lines Lexicographically Ascending",           IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING
42080 | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING                         |                                                                   | Sort Lines Lex. Ascending Ignoring Case                                                   |         IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING :: MENUITEM "Sort Lines Lex. Ascending Ignoring Case",          IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING
42100 | IDM_EDIT_SORTLINES_LOCALE_ASCENDING                                     |                                                                   | Sort Lines In Locale Order Ascending                                                      |         IDM_EDIT_SORTLINES_LOCALE_ASCENDING :: MENUITEM "Sort Lines In Locale Order Ascending",             IDM_EDIT_SORTLINES_LOCALE_ASCENDING
42061 | IDM_EDIT_SORTLINES_INTEGER_ASCENDING                                    |                                                                   | Sort Lines As Integers Ascending                                                          |         IDM_EDIT_SORTLINES_INTEGER_ASCENDING :: MENUITEM "Sort Lines As Integers Ascending",                 IDM_EDIT_SORTLINES_INTEGER_ASCENDING
42063 | IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING                               |                                                                   | Sort Lines As Decimals (Comma) Ascending                                                  |         IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING :: MENUITEM "Sort Lines As Decimals (Comma) Ascending",         IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING
42065 | IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING                                 |                                                                   | Sort Lines As Decimals (Dot) Ascending                                                    |         IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING :: MENUITEM "Sort Lines As Decimals (Dot) Ascending",           IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING
42104 | IDM_EDIT_SORTLINES_LENGTH_ASCENDING                                     |                                                                   | Sort Lines By Length Ascending                                                            |         IDM_EDIT_SORTLINES_LENGTH_ASCENDING :: MENUITEM "Sort Lines By Length Ascending",                   IDM_EDIT_SORTLINES_LENGTH_ASCENDING
42060 | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING                             |                                                                   | Sort Lines Lexicographically Descending                                                   |         IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING :: MENUITEM "Sort Lines Lexicographically Descending",          IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING
42081 | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING                        |                                                                   | Sort Lines Lex. Descending Ignoring Case                                                  |         IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING :: MENUITEM "Sort Lines Lex. Descending Ignoring Case",         IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING
42101 | IDM_EDIT_SORTLINES_LOCALE_DESCENDING                                    |                                                                   | Sort Lines In Locale Order Descending                                                     |         IDM_EDIT_SORTLINES_LOCALE_DESCENDING :: MENUITEM "Sort Lines In Locale Order Descending",            IDM_EDIT_SORTLINES_LOCALE_DESCENDING
42062 | IDM_EDIT_SORTLINES_INTEGER_DESCENDING                                   |                                                                   | Sort Lines As Integers Descending                                                         |         IDM_EDIT_SORTLINES_INTEGER_DESCENDING :: MENUITEM "Sort Lines As Integers Descending",                IDM_EDIT_SORTLINES_INTEGER_DESCENDING
42064 | IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING                              |                                                                   | Sort Lines As Decimals (Comma) Descending                                                 |         IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING :: MENUITEM "Sort Lines As Decimals (Comma) Descending",        IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING
42066 | IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING                                |                                                                   | Sort Lines As Decimals (Dot) Descending                                                   |         IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING :: MENUITEM "Sort Lines As Decimals (Dot) Descending",          IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING
42105 | IDM_EDIT_SORTLINES_LENGTH_DESCENDING                                    |                                                                   | Sort Lines By Length Descending                                                           |         IDM_EDIT_SORTLINES_LENGTH_DESCENDING :: MENUITEM "Sort Lines By Length Descending",                  IDM_EDIT_SORTLINES_LENGTH_DESCENDING
POPUP "Co&mment/Uncomment"
42022 | IDM_EDIT_BLOCK_COMMENT                                                  |                                                                   | Toggle Single Line Comment                                                                |         IDM_EDIT_BLOCK_COMMENT :: MENUITEM "Toggle Single Line Comment",    IDM_EDIT_BLOCK_COMMENT
42035 | IDM_EDIT_BLOCK_COMMENT_SET                                              |                                                                   | Single Line Comment                                                                       |         IDM_EDIT_BLOCK_COMMENT_SET :: MENUITEM "Single Line Comment",           IDM_EDIT_BLOCK_COMMENT_SET
42036 | IDM_EDIT_BLOCK_UNCOMMENT                                                |                                                                   | Single Line Uncomment                                                                     |         IDM_EDIT_BLOCK_UNCOMMENT :: MENUITEM "Single Line Uncomment",         IDM_EDIT_BLOCK_UNCOMMENT
42023 | IDM_EDIT_STREAM_COMMENT                                                 |                                                                   | Block Comment                                                                             |         IDM_EDIT_STREAM_COMMENT :: MENUITEM "Block Comment",          IDM_EDIT_STREAM_COMMENT
IDM_EDIT_STREAM_UNCOMMENT :: MENUITEM "Block Uncomment",        IDM_EDIT_STREAM_UNCOMMENT
POPUP "&Auto-Completion"
IDM_EDIT_AUTOCOMPLETE :: MENUITEM "Function Completion",         IDM_EDIT_AUTOCOMPLETE
IDM_EDIT_AUTOCOMPLETE_CURRENTFILE :: MENUITEM "Word Completion",             IDM_EDIT_AUTOCOMPLETE_CURRENTFILE
IDM_EDIT_FUNCCALLTIP :: MENUITEM "Function Parameters Hint",    IDM_EDIT_FUNCCALLTIP
IDM_EDIT_FUNCCALLTIP_PREVIOUS :: MENUITEM "Function Parameters Previous Hint", IDM_EDIT_FUNCCALLTIP_PREVIOUS
IDM_EDIT_FUNCCALLTIP_NEXT :: MENUITEM "Function Parameters Next Hint",     IDM_EDIT_FUNCCALLTIP_NEXT
IDM_EDIT_AUTOCOMPLETE_PATH :: MENUITEM "Path Completion",             IDM_EDIT_AUTOCOMPLETE_PATH
POPUP "&EOL Conversion"
45001 | IDM_FORMAT_TODOS                                                        |                                                                   | Windows (CR LF)                                                                           |         IDM_FORMAT_TODOS :: MENUITEM "Windows (CR LF)",             IDM_FORMAT_TODOS
45002 | IDM_FORMAT_TOUNIX                                                       |                                                                   | Unix (LF)                                                                                 |         IDM_FORMAT_TOUNIX :: MENUITEM "Unix (LF)",                   IDM_FORMAT_TOUNIX
45003 | IDM_FORMAT_TOMAC                                                        |                                                                   | Macintosh (CR)                                                                            |         IDM_FORMAT_TOMAC :: MENUITEM "Macintosh (CR)",              IDM_FORMAT_TOMAC
POPUP "&Blank Operations"
42024 | IDM_EDIT_TRIMTRAILING                                                   |                                                                   | Trim Trailing Space                                                                       |         IDM_EDIT_TRIMTRAILING :: MENUITEM "Trim Trailing Space",                IDM_EDIT_TRIMTRAILING
42042 | IDM_EDIT_TRIMLINEHEAD                                                   |                                                                   | Trim Leading Space                                                                        |         IDM_EDIT_TRIMLINEHEAD :: MENUITEM "Trim Leading Space",                 IDM_EDIT_TRIMLINEHEAD
42043 | IDM_EDIT_TRIM_BOTH                                                      |                                                                   | Trim Leading and Trailing Space                                                           |         IDM_EDIT_TRIM_BOTH :: MENUITEM "Trim Leading and Trailing Space",    IDM_EDIT_TRIM_BOTH
42044 | IDM_EDIT_EOL2WS                                                         |                                                                   | EOL to Space                                                                              |         IDM_EDIT_EOL2WS :: MENUITEM "EOL to Space",                       IDM_EDIT_EOL2WS
42045 | IDM_EDIT_TRIMALL                                                        |                                                                   | Trim both and EOL to Space                                                                |         IDM_EDIT_TRIMALL :: MENUITEM "Trim both and EOL to Space",         IDM_EDIT_TRIMALL
42046 | IDM_EDIT_TAB2SW                                                         |                                                                   | TAB to Space                                                                              |         IDM_EDIT_TAB2SW :: MENUITEM "TAB to Space",                       IDM_EDIT_TAB2SW
42054 | IDM_EDIT_SW2TAB_ALL                                                     |                                                                   | Space to TAB (All)                                                                        |         IDM_EDIT_SW2TAB_ALL :: MENUITEM "Space to TAB (All)",                 IDM_EDIT_SW2TAB_ALL
42053 | IDM_EDIT_SW2TAB_LEADING                                                 |                                                                   | Space to TAB (Leading)                                                                    |         IDM_EDIT_SW2TAB_LEADING :: MENUITEM "Space to TAB (Leading)",             IDM_EDIT_SW2TAB_LEADING
POPUP "&Paste Special"
IDM_EDIT_PASTE_AS_HTML :: MENUITEM "Paste HTML Content",                 IDM_EDIT_PASTE_AS_HTML
IDM_EDIT_PASTE_AS_RTF :: MENUITEM "Paste RTF Content",                  IDM_EDIT_PASTE_AS_RTF
IDM_EDIT_COPY_BINARY :: MENUITEM "Copy Binary Content",                IDM_EDIT_COPY_BINARY
IDM_EDIT_CUT_BINARY :: MENUITEM "Cut Binary Content",                 IDM_EDIT_CUT_BINARY
IDM_EDIT_PASTE_BINARY :: MENUITEM "Paste Binary Content",               IDM_EDIT_PASTE_BINARY
POPUP "&On Selection"
IDM_EDIT_OPENSELECTEDFILETOEDIT :: MENUITEM "Open File", IDM_EDIT_OPENSELECTEDFILETOEDIT
IDM_EDIT_OPENSELECTEDFILEFOLDERINEXPLORER :: MENUITEM "Open Containing Folder in Explorer", IDM_EDIT_OPENSELECTEDFILEFOLDERINEXPLORER
42106 | IDM_EDIT_REDACT_SELECTION                                               |                                                                   | Redact Selection █ (Shift: ●)                                                             |         IDM_EDIT_REDACT_SELECTION :: MENUITEM "&Redact Selection █ (Shift: ●)", IDM_EDIT_REDACT_SELECTION
IDM_EDIT_SEARCHONINTERNET :: MENUITEM "Search on Internet", IDM_EDIT_SEARCHONINTERNET
IDM_EDIT_CHANGESEARCHENGINE :: MENUITEM "Change Search Engine...", IDM_EDIT_CHANGESEARCHENGINE
POPUP "Multi-select All"
IDM_EDIT_MULTISELECTALL :: MENUITEM "Ignore Case && Whole Word",   IDM_EDIT_MULTISELECTALL
IDM_EDIT_MULTISELECTALLMATCHCASE :: MENUITEM "Match Case Only",              IDM_EDIT_MULTISELECTALLMATCHCASE
42092 | IDM_EDIT_MULTISELECTALLWHOLEWORD                                        |                                                                   | Match Whole Word Only                                                                     |         IDM_EDIT_MULTISELECTALLWHOLEWORD :: MENUITEM "Match Whole Word Only",        IDM_EDIT_MULTISELECTALLWHOLEWORD
42093 | IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD                               |                                                                   | Match Case  Whole Word                                                                    |         IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD :: MENUITEM "Match Case && Whole Word",    IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD
POPUP "Multi-select Next"
42094 | IDM_EDIT_MULTISELECTNEXT                                                |                                                                   | Ignore Case  Whole Word                                                                   |         IDM_EDIT_MULTISELECTNEXT :: MENUITEM "Ignore Case && Whole Word",   IDM_EDIT_MULTISELECTNEXT
42095 | IDM_EDIT_MULTISELECTNEXTMATCHCASE                                       |                                                                   | Match Case Only                                                                           |         IDM_EDIT_MULTISELECTNEXTMATCHCASE :: MENUITEM "Match Case Only",              IDM_EDIT_MULTISELECTNEXTMATCHCASE
42096 | IDM_EDIT_MULTISELECTNEXTWHOLEWORD                                       |                                                                   | Match Whole Word Only                                                                     |         IDM_EDIT_MULTISELECTNEXTWHOLEWORD :: MENUITEM "Match Whole Word Only",        IDM_EDIT_MULTISELECTNEXTWHOLEWORD
42097 | IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD                              |                                                                   | Match Case  Whole Word                                                                    |         IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD :: MENUITEM "Match Case && Whole Word",    IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD
42098 | IDM_EDIT_MULTISELECTUNDO                                                |                                                                   | Undo the Latest Added Multi-Select                                                        |     IDM_EDIT_MULTISELECTUNDO :: MENUITEM "Undo the Latest Added Multi-Select",   IDM_EDIT_MULTISELECTUNDO
42099 | IDM_EDIT_MULTISELECTSSKIP                                               |                                                                   | Skip Current  Go to Next Multi-select                                                     |     IDM_EDIT_MULTISELECTSSKIP :: MENUITEM "Skip Current && Go to Next Multi-select",IDM_EDIT_MULTISELECTSSKIP
IDM_EDIT_COLUMNMODETIP :: MENUITEM "Column Mode...",           IDM_EDIT_COLUMNMODETIP
IDM_EDIT_COLUMNMODE :: MENUITEM "Colum&n Editor...",        IDM_EDIT_COLUMNMODE
IDM_EDIT_CHAR_PANEL :: MENUITEM "Character &Panel",         IDM_EDIT_CHAR_PANEL
IDM_EDIT_CLIPBOARDHISTORY_PANEL :: MENUITEM "Clipboard &History",       IDM_EDIT_CLIPBOARDHISTORY_PANEL
POPUP "Read-&Only in Notepad++"
42028 | IDM_EDIT_TOGGLEREADONLY                                                 |                                                                   | Read-Only on Current Document                                                             |         IDM_EDIT_TOGGLEREADONLY :: MENUITEM "Read-Only on Current Document",     IDM_EDIT_TOGGLEREADONLY
42102 | IDM_EDIT_SETREADONLYFORALLDOCS                                          |                                                                   | Read-Only for All Documents                                                               |         IDM_EDIT_SETREADONLYFORALLDOCS :: MENUITEM "Read-Only for All Documents",       IDM_EDIT_SETREADONLYFORALLDOCS
42103 | IDM_EDIT_CLEARREADONLYFORALLDOCS                                        |                                                                   | Clear Read-Only for All Documents                                                         |         IDM_EDIT_CLEARREADONLYFORALLDOCS :: MENUITEM "Clear Read-Only for All Documents", IDM_EDIT_CLEARREADONLYFORALLDOCS
42033 | IDM_EDIT_TOGGLESYSTEMREADONLY                                           |                                                                   | Read-Only Attribute in Windows                                                            |     IDM_EDIT_TOGGLESYSTEMREADONLY :: MENUITEM "Read-Only Attribute in Windows",    IDM_EDIT_TOGGLESYSTEMREADONLY
POPUP "&Search"
IDM_SEARCH_FIND :: MENUITEM "&Find...",                    IDM_SEARCH_FIND
IDM_SEARCH_FINDINFILES :: MENUITEM "Find in Fi&les...",           IDM_SEARCH_FINDINFILES
43002 | IDM_SEARCH_FINDNEXT                                                     |                                                                   | Find Next                                                                                 |     IDM_SEARCH_FINDNEXT :: MENUITEM "Find &Next",                  IDM_SEARCH_FINDNEXT
43010 | IDM_SEARCH_FINDPREV                                                     |                                                                   | Find Previous                                                                             |     IDM_SEARCH_FINDPREV :: MENUITEM "Find &Previous",              IDM_SEARCH_FINDPREV
43048 | IDM_SEARCH_SETANDFINDNEXT                                               |                                                                   | Select and Find Next                                                                      |     IDM_SEARCH_SETANDFINDNEXT :: MENUITEM "&Select and Find Next",       IDM_SEARCH_SETANDFINDNEXT
43049 | IDM_SEARCH_SETANDFINDPREV                                               |                                                                   | Select and Find Previous                                                                  |     IDM_SEARCH_SETANDFINDPREV :: MENUITEM "&Select and Find Previous",   IDM_SEARCH_SETANDFINDPREV
43014 | IDM_SEARCH_VOLATILE_FINDNEXT                                            |                                                                   | Find (Volatile) Next                                                                      |     IDM_SEARCH_VOLATILE_FINDNEXT :: MENUITEM "Find (&Volatile) Next",       IDM_SEARCH_VOLATILE_FINDNEXT
43015 | IDM_SEARCH_VOLATILE_FINDPREV                                            |                                                                   | Find (Volatile) Previous                                                                  |     IDM_SEARCH_VOLATILE_FINDPREV :: MENUITEM "Find (&Volatile) Previous",   IDM_SEARCH_VOLATILE_FINDPREV
IDM_SEARCH_REPLACE :: MENUITEM "&Replace...",                 IDM_SEARCH_REPLACE
IDM_SEARCH_FINDINCREMENT :: MENUITEM "&Incremental Search",         IDM_SEARCH_FINDINCREMENT
IDM_FOCUS_ON_FOUND_RESULTS :: MENUITEM "Search Results &Window",      IDM_FOCUS_ON_FOUND_RESULTS
IDM_SEARCH_GOTONEXTFOUND :: MENUITEM "Next Search Resul&t",         IDM_SEARCH_GOTONEXTFOUND
IDM_SEARCH_GOTOPREVFOUND :: MENUITEM "Previous Search Resul&t",     IDM_SEARCH_GOTOPREVFOUND
IDM_SEARCH_GOTOLINE :: MENUITEM "&Go to...",                   IDM_SEARCH_GOTOLINE
43009 | IDM_SEARCH_GOTOMATCHINGBRACE                                            |                                                                   | Go to Matching Brace                                                                      |     IDM_SEARCH_GOTOMATCHINGBRACE :: MENUITEM "Go to &Matching Brace",       IDM_SEARCH_GOTOMATCHINGBRACE
43053 | IDM_SEARCH_SELECTMATCHINGBRACES                                         |                                                                   | Select All In-between {} [] or ()                                                         |     IDM_SEARCH_SELECTMATCHINGBRACES :: MENUITEM "Select All In-betw&een {} [] or ()", IDM_SEARCH_SELECTMATCHINGBRACES
IDM_SEARCH_MARK :: MENUITEM "Mar&k...",                    IDM_SEARCH_MARK
POPUP "Change History"
IDM_SEARCH_CHANGED_NEXT :: MENUITEM "Go to Next Change",           IDM_SEARCH_CHANGED_NEXT
IDM_SEARCH_CHANGED_PREV :: MENUITEM "Go to Previous Change",       IDM_SEARCH_CHANGED_PREV
IDM_SEARCH_CLEAR_CHANGE_HISTORY :: MENUITEM "Clear Change History",        IDM_SEARCH_CLEAR_CHANGE_HISTORY
POPUP "Style &All Occurrences of Token"
43022 | IDM_SEARCH_MARKALLEXT1                                                  |                                                                   | Using 1st Style                                                                           |         IDM_SEARCH_MARKALLEXT1 :: MENUITEM "Using 1st Style",    IDM_SEARCH_MARKALLEXT1
43024 | IDM_SEARCH_MARKALLEXT2                                                  |                                                                   | Using 2nd Style                                                                           |         IDM_SEARCH_MARKALLEXT2 :: MENUITEM "Using 2nd Style",    IDM_SEARCH_MARKALLEXT2
43026 | IDM_SEARCH_MARKALLEXT3                                                  |                                                                   | Using 3rd Style                                                                           |         IDM_SEARCH_MARKALLEXT3 :: MENUITEM "Using 3rd Style",    IDM_SEARCH_MARKALLEXT3
43028 | IDM_SEARCH_MARKALLEXT4                                                  |                                                                   | Using 4th Style                                                                           |         IDM_SEARCH_MARKALLEXT4 :: MENUITEM "Using 4th Style",    IDM_SEARCH_MARKALLEXT4
43030 | IDM_SEARCH_MARKALLEXT5                                                  |                                                                   | Using 5th Style                                                                           |         IDM_SEARCH_MARKALLEXT5 :: MENUITEM "Using 5th Style",    IDM_SEARCH_MARKALLEXT5
POPUP "Style &One Token"
43062 | IDM_SEARCH_MARKONEEXT1                                                  |                                                                   | Using 1st Style                                                                           |         IDM_SEARCH_MARKONEEXT1 :: MENUITEM "Using 1st Style",    IDM_SEARCH_MARKONEEXT1
43063 | IDM_SEARCH_MARKONEEXT2                                                  |                                                                   | Using 2nd Style                                                                           |         IDM_SEARCH_MARKONEEXT2 :: MENUITEM "Using 2nd Style",    IDM_SEARCH_MARKONEEXT2
43064 | IDM_SEARCH_MARKONEEXT3                                                  |                                                                   | Using 3rd Style                                                                           |         IDM_SEARCH_MARKONEEXT3 :: MENUITEM "Using 3rd Style",    IDM_SEARCH_MARKONEEXT3
43065 | IDM_SEARCH_MARKONEEXT4                                                  |                                                                   | Using 4th Style                                                                           |         IDM_SEARCH_MARKONEEXT4 :: MENUITEM "Using 4th Style",    IDM_SEARCH_MARKONEEXT4
43066 | IDM_SEARCH_MARKONEEXT5                                                  |                                                                   | Using 5th Style                                                                           |         IDM_SEARCH_MARKONEEXT5 :: MENUITEM "Using 5th Style",    IDM_SEARCH_MARKONEEXT5
POPUP "Clear Style"
43023 | IDM_SEARCH_UNMARKALLEXT1                                                |                                                                   | Clear 1st Style                                                                           |         IDM_SEARCH_UNMARKALLEXT1 :: MENUITEM "Clear 1st Style",     IDM_SEARCH_UNMARKALLEXT1
43025 | IDM_SEARCH_UNMARKALLEXT2                                                |                                                                   | Clear 2nd Style                                                                           |         IDM_SEARCH_UNMARKALLEXT2 :: MENUITEM "Clear 2nd Style",     IDM_SEARCH_UNMARKALLEXT2
43027 | IDM_SEARCH_UNMARKALLEXT3                                                |                                                                   | Clear 3rd Style                                                                           |         IDM_SEARCH_UNMARKALLEXT3 :: MENUITEM "Clear 3rd Style",     IDM_SEARCH_UNMARKALLEXT3
43029 | IDM_SEARCH_UNMARKALLEXT4                                                |                                                                   | Clear 4th Style                                                                           |         IDM_SEARCH_UNMARKALLEXT4 :: MENUITEM "Clear 4th Style",     IDM_SEARCH_UNMARKALLEXT4
43031 | IDM_SEARCH_UNMARKALLEXT5                                                |                                                                   | Clear 5th Style                                                                           |         IDM_SEARCH_UNMARKALLEXT5 :: MENUITEM "Clear 5th Style",     IDM_SEARCH_UNMARKALLEXT5
43032 | IDM_SEARCH_CLEARALLMARKS                                                |                                                                   | Clear All Styles                                                                          |         IDM_SEARCH_CLEARALLMARKS :: MENUITEM "Clear all Styles",    IDM_SEARCH_CLEARALLMARKS
POPUP "&Jump Up"
43033 | IDM_SEARCH_GOPREVMARKER1                                                |                                                                   | 1st style                                                                                 |         IDM_SEARCH_GOPREVMARKER1 :: MENUITEM "1st Style",     IDM_SEARCH_GOPREVMARKER1
43034 | IDM_SEARCH_GOPREVMARKER2                                                |                                                                   | 2nd style                                                                                 |         IDM_SEARCH_GOPREVMARKER2 :: MENUITEM "2nd Style",     IDM_SEARCH_GOPREVMARKER2
43035 | IDM_SEARCH_GOPREVMARKER3                                                |                                                                   | 3rd style                                                                                 |         IDM_SEARCH_GOPREVMARKER3 :: MENUITEM "3rd Style",     IDM_SEARCH_GOPREVMARKER3
43036 | IDM_SEARCH_GOPREVMARKER4                                                |                                                                   | 4th style                                                                                 |         IDM_SEARCH_GOPREVMARKER4 :: MENUITEM "4th Style",     IDM_SEARCH_GOPREVMARKER4
43037 | IDM_SEARCH_GOPREVMARKER5                                                |                                                                   | 5th style                                                                                 |         IDM_SEARCH_GOPREVMARKER5 :: MENUITEM "5th Style",     IDM_SEARCH_GOPREVMARKER5
43038 | IDM_SEARCH_GOPREVMARKER_DEF                                             |                                                                   | Find Mark Style                                                                           |         IDM_SEARCH_GOPREVMARKER_DEF :: MENUITEM "Find Mark Style",    IDM_SEARCH_GOPREVMARKER_DEF
POPUP "Jump &Down"
43039 | IDM_SEARCH_GONEXTMARKER1                                                |                                                                   | 1st style                                                                                 |         IDM_SEARCH_GONEXTMARKER1 :: MENUITEM "1st Style",      IDM_SEARCH_GONEXTMARKER1
43040 | IDM_SEARCH_GONEXTMARKER2                                                |                                                                   | 2nd style                                                                                 |         IDM_SEARCH_GONEXTMARKER2 :: MENUITEM "2nd Style",      IDM_SEARCH_GONEXTMARKER2
43041 | IDM_SEARCH_GONEXTMARKER3                                                |                                                                   | 3rd style                                                                                 |         IDM_SEARCH_GONEXTMARKER3 :: MENUITEM "3rd Style",      IDM_SEARCH_GONEXTMARKER3
43042 | IDM_SEARCH_GONEXTMARKER4                                                |                                                                   | 4th style                                                                                 |         IDM_SEARCH_GONEXTMARKER4 :: MENUITEM "4th Style",      IDM_SEARCH_GONEXTMARKER4
43043 | IDM_SEARCH_GONEXTMARKER5                                                |                                                                   | 5th style                                                                                 |         IDM_SEARCH_GONEXTMARKER5 :: MENUITEM "5th Style",      IDM_SEARCH_GONEXTMARKER5
43044 | IDM_SEARCH_GONEXTMARKER_DEF                                             |                                                                   | Find Mark Style                                                                           |         IDM_SEARCH_GONEXTMARKER_DEF :: MENUITEM "Find Mark Style",     IDM_SEARCH_GONEXTMARKER_DEF
POPUP "&Copy Styled Text"
43055 | IDM_SEARCH_STYLE1TOCLIP                                                 |                                                                   | 1st Style                                                                                 |         IDM_SEARCH_STYLE1TOCLIP :: MENUITEM "1st Style",               IDM_SEARCH_STYLE1TOCLIP
43056 | IDM_SEARCH_STYLE2TOCLIP                                                 |                                                                   | 2nd Style                                                                                 |         IDM_SEARCH_STYLE2TOCLIP :: MENUITEM "2nd Style",               IDM_SEARCH_STYLE2TOCLIP
43057 | IDM_SEARCH_STYLE3TOCLIP                                                 |                                                                   | 3rd Style                                                                                 |         IDM_SEARCH_STYLE3TOCLIP :: MENUITEM "3rd Style",               IDM_SEARCH_STYLE3TOCLIP
43058 | IDM_SEARCH_STYLE4TOCLIP                                                 |                                                                   | 4th Style                                                                                 |         IDM_SEARCH_STYLE4TOCLIP :: MENUITEM "4th Style",               IDM_SEARCH_STYLE4TOCLIP
43059 | IDM_SEARCH_STYLE5TOCLIP                                                 |                                                                   | 5th Style                                                                                 |         IDM_SEARCH_STYLE5TOCLIP :: MENUITEM "5th Style",               IDM_SEARCH_STYLE5TOCLIP
43060 | IDM_SEARCH_ALLSTYLESTOCLIP                                              |                                                                   | All Styles                                                                                |         IDM_SEARCH_ALLSTYLESTOCLIP :: MENUITEM "All Styles",              IDM_SEARCH_ALLSTYLESTOCLIP
43061 | IDM_SEARCH_MARKEDTOCLIP                                                 |                                                                   | Find Mark Style                                                                           |         IDM_SEARCH_MARKEDTOCLIP :: MENUITEM "Find Mark Style",     IDM_SEARCH_MARKEDTOCLIP
POPUP "&Bookmark"
43005 | IDM_SEARCH_TOGGLE_BOOKMARK                                              |                                                                   | Toggle Bookmark                                                                           |         IDM_SEARCH_TOGGLE_BOOKMARK :: MENUITEM "Toggle Bookmark" ,                       IDM_SEARCH_TOGGLE_BOOKMARK
43006 | IDM_SEARCH_NEXT_BOOKMARK                                                |                                                                   | Next Bookmark                                                                             |         IDM_SEARCH_NEXT_BOOKMARK :: MENUITEM "Next Bookmark",                          IDM_SEARCH_NEXT_BOOKMARK
43007 | IDM_SEARCH_PREV_BOOKMARK                                                |                                                                   | Previous Bookmark                                                                         |         IDM_SEARCH_PREV_BOOKMARK :: MENUITEM "Previous Bookmark",                      IDM_SEARCH_PREV_BOOKMARK
43008 | IDM_SEARCH_CLEAR_BOOKMARKS                                              |                                                                   | Clear All Bookmarks                                                                       |         IDM_SEARCH_CLEAR_BOOKMARKS :: MENUITEM "Clear All Bookmarks",                    IDM_SEARCH_CLEAR_BOOKMARKS
43018 | IDM_SEARCH_CUTMARKEDLINES                                               |                                                                   | Cut Bookmarked Lines                                                                      |         IDM_SEARCH_CUTMARKEDLINES :: MENUITEM "Cut Bookmarked Lines",                   IDM_SEARCH_CUTMARKEDLINES
43019 | IDM_SEARCH_COPYMARKEDLINES                                              |                                                                   | Copy Bookmarked Lines                                                                     |         IDM_SEARCH_COPYMARKEDLINES :: MENUITEM "Copy Bookmarked Lines",                  IDM_SEARCH_COPYMARKEDLINES
43020 | IDM_SEARCH_PASTEMARKEDLINES                                             |                                                                   | Paste to (Replace) Bookmarked Lines                                                       |         IDM_SEARCH_PASTEMARKEDLINES :: MENUITEM "Paste to (Replace) Bookmarked Lines",    IDM_SEARCH_PASTEMARKEDLINES
43021 | IDM_SEARCH_DELETEMARKEDLINES                                            |                                                                   | Remove Bookmarked Lines                                                                   |         IDM_SEARCH_DELETEMARKEDLINES :: MENUITEM "Remove Bookmarked Lines",                IDM_SEARCH_DELETEMARKEDLINES
43051 | IDM_SEARCH_DELETEUNMARKEDLINES                                          |                                                                   | Remove Non-Bookmarked Lines                                                               |         IDM_SEARCH_DELETEUNMARKEDLINES :: MENUITEM "Remove Non-Bookmarked Lines",            IDM_SEARCH_DELETEUNMARKEDLINES
43050 | IDM_SEARCH_INVERSEMARKS                                                 |                                                                   | Inverse Bookmarks                                                                         |         IDM_SEARCH_INVERSEMARKS :: MENUITEM "Inverse Bookmarks",                      IDM_SEARCH_INVERSEMARKS
IDM_SEARCH_FINDCHARINRANGE :: MENUITEM "Find characters in rang&e...",       IDM_SEARCH_FINDCHARINRANGE
POPUP "&View"
44034 | IDM_VIEW_ALWAYSONTOP                                                    |                                                                   | Always on Top                                                                             |     IDM_VIEW_ALWAYSONTOP :: MENUITEM "Always on &Top",              IDM_VIEW_ALWAYSONTOP
44032 | IDM_VIEW_FULLSCREENTOGGLE                                               |                                                                   | Toggle Full Screen Mode                                                                   |     IDM_VIEW_FULLSCREENTOGGLE :: MENUITEM "To&ggle Full Screen Mode",    IDM_VIEW_FULLSCREENTOGGLE
IDM_VIEW_POSTIT :: MENUITEM "&Post-It",                    IDM_VIEW_POSTIT
IDM_VIEW_DISTRACTIONFREE :: MENUITEM "D&istraction Free Mode",      IDM_VIEW_DISTRACTIONFREE
POPUP "&View Current File in"
44100 | IDM_VIEW_IN_FIREFOX                                                     |                                                                   | View in Firefox                                                                           |         IDM_VIEW_IN_FIREFOX :: MENUITEM "&Firefox",                IDM_VIEW_IN_FIREFOX
44101 | IDM_VIEW_IN_CHROME                                                      |                                                                   | View in Chrome                                                                            |         IDM_VIEW_IN_CHROME :: MENUITEM "&Chrome",                 IDM_VIEW_IN_CHROME
44102 | IDM_VIEW_IN_EDGE                                                        |                                                                   | View in Edge                                                                              |         IDM_VIEW_IN_EDGE :: MENUITEM "&Edge",                   IDM_VIEW_IN_EDGE
44103 | IDM_VIEW_IN_IE                                                          |                                                                   | View in IE                                                                                |         IDM_VIEW_IN_IE :: MENUITEM "&IE",                     IDM_VIEW_IN_IE
POPUP "Show S&ymbol"
IDM_VIEW_TAB_SPACE :: MENUITEM "Show Space and Tab",                     IDM_VIEW_TAB_SPACE
IDM_VIEW_EOL :: MENUITEM "Show End of Line",                       IDM_VIEW_EOL
IDM_VIEW_NPC :: MENUITEM "Show Non-Printing Characters",           IDM_VIEW_NPC
IDM_VIEW_NPC_CCUNIEOL :: MENUITEM "Show Control Characters && Unicode EOL", IDM_VIEW_NPC_CCUNIEOL
IDM_VIEW_ALL_CHARACTERS :: MENUITEM "Show All Characters",                    IDM_VIEW_ALL_CHARACTERS
IDM_VIEW_INDENT_GUIDE :: MENUITEM "Show Indent Guide",                      IDM_VIEW_INDENT_GUIDE
IDM_VIEW_WRAP_SYMBOL :: MENUITEM "Show Wrap Symbol",                       IDM_VIEW_WRAP_SYMBOL
POPUP "&Zoom"
IDM_VIEW_ZOOMIN :: MENUITEM "Zoom &In (Ctrl+Mouse Wheel Up)",       IDM_VIEW_ZOOMIN
IDM_VIEW_ZOOMOUT :: MENUITEM "Zoom &Out (Ctrl+Mouse Wheel Down)",    IDM_VIEW_ZOOMOUT
IDM_VIEW_ZOOMRESTORE :: MENUITEM "&Restore Default Zoom",                IDM_VIEW_ZOOMRESTORE
IDM_VIEW_ZOOM_SYNC :: MENUITEM "&Synchronize Across Views",            IDM_VIEW_ZOOM_SYNC
POPUP "&Move/Clone Current Document"
10001 | IDM_VIEW_GOTO_ANOTHER_VIEW                                              | View > Move/Clone Current Document                                | Move to Other View                                                                        |         IDM_VIEW_GOTO_ANOTHER_VIEW :: MENUITEM "&Move to Other View",      IDM_VIEW_GOTO_ANOTHER_VIEW
10002 | IDM_VIEW_CLONE_TO_ANOTHER_VIEW                                          | View > Move/Clone Current Document                                | Clone to Other View                                                                       |         IDM_VIEW_CLONE_TO_ANOTHER_VIEW :: MENUITEM "&Clone to Other View",     IDM_VIEW_CLONE_TO_ANOTHER_VIEW
10003 | IDM_VIEW_GOTO_NEW_INSTANCE                                              | View > Move/Clone Current Document                                | Move to New Instance                                                                      |         IDM_VIEW_GOTO_NEW_INSTANCE :: MENUITEM "Mo&ve to New Instance",    IDM_VIEW_GOTO_NEW_INSTANCE
10004 | IDM_VIEW_LOAD_IN_NEW_INSTANCE                                           | View > Move/Clone Current Document                                | Open in New Instance                                                                      |         IDM_VIEW_LOAD_IN_NEW_INSTANCE :: MENUITEM "&Open in New Instance",    IDM_VIEW_LOAD_IN_NEW_INSTANCE
POPUP "Ta&b"
44086 | IDM_VIEW_TAB1                                                           |                                                                   | 1st Tab                                                                                   |         IDM_VIEW_TAB1 :: MENUITEM "1st Tab",                 IDM_VIEW_TAB1
44087 | IDM_VIEW_TAB2                                                           |                                                                   | 2nd Tab                                                                                   |         IDM_VIEW_TAB2 :: MENUITEM "2nd Tab",                 IDM_VIEW_TAB2
44088 | IDM_VIEW_TAB3                                                           |                                                                   | 3rd Tab                                                                                   |         IDM_VIEW_TAB3 :: MENUITEM "3rd Tab",                 IDM_VIEW_TAB3
44089 | IDM_VIEW_TAB4                                                           |                                                                   | 4th Tab                                                                                   |         IDM_VIEW_TAB4 :: MENUITEM "4th Tab",                 IDM_VIEW_TAB4
44090 | IDM_VIEW_TAB5                                                           |                                                                   | 5th Tab                                                                                   |         IDM_VIEW_TAB5 :: MENUITEM "5th Tab",                 IDM_VIEW_TAB5
44091 | IDM_VIEW_TAB6                                                           |                                                                   | 6th Tab                                                                                   |         IDM_VIEW_TAB6 :: MENUITEM "6th Tab",                 IDM_VIEW_TAB6
44092 | IDM_VIEW_TAB7                                                           |                                                                   | 7th Tab                                                                                   |         IDM_VIEW_TAB7 :: MENUITEM "7th Tab",                 IDM_VIEW_TAB7
44093 | IDM_VIEW_TAB8                                                           |                                                                   | 8th Tab                                                                                   |         IDM_VIEW_TAB8 :: MENUITEM "8th Tab",                 IDM_VIEW_TAB8
44094 | IDM_VIEW_TAB9                                                           |                                                                   | 9th Tab                                                                                   |         IDM_VIEW_TAB9 :: MENUITEM "9th Tab",                 IDM_VIEW_TAB9
IDM_VIEW_TAB_START :: MENUITEM "First Tab",               IDM_VIEW_TAB_START
IDM_VIEW_TAB_END :: MENUITEM "Last Tab",                IDM_VIEW_TAB_END
44095 | IDM_VIEW_TAB_NEXT                                                       |                                                                   | Next Tab                                                                                  |         IDM_VIEW_TAB_NEXT :: MENUITEM "Next Tab",                IDM_VIEW_TAB_NEXT
44096 | IDM_VIEW_TAB_PREV                                                       |                                                                   | Previous Tab                                                                              |         IDM_VIEW_TAB_PREV :: MENUITEM "Previous Tab",            IDM_VIEW_TAB_PREV
10005 | IDM_VIEW_GOTO_START                                                     | View > Tab                                                        | Move to Start                                                                             |         IDM_VIEW_GOTO_START :: MENUITEM "Move to Start",           IDM_VIEW_GOTO_START
10006 | IDM_VIEW_GOTO_END                                                       | View > Tab                                                        | Move to End                                                                               |         IDM_VIEW_GOTO_END :: MENUITEM "Move to End",             IDM_VIEW_GOTO_END
44098 | IDM_VIEW_TAB_MOVEFORWARD                                                |                                                                   | Move Tab Forward                                                                          |         IDM_VIEW_TAB_MOVEFORWARD :: MENUITEM "Move Tab Forward",        IDM_VIEW_TAB_MOVEFORWARD
44099 | IDM_VIEW_TAB_MOVEBACKWARD                                               |                                                                   | Move Tab Backward                                                                         |         IDM_VIEW_TAB_MOVEBACKWARD :: MENUITEM "Move Tab Backward",       IDM_VIEW_TAB_MOVEBACKWARD
IDM_VIEW_TAB_COLOUR_1 :: MENUITEM "Apply Color 1",           IDM_VIEW_TAB_COLOUR_1
IDM_VIEW_TAB_COLOUR_2 :: MENUITEM "Apply Color 2",           IDM_VIEW_TAB_COLOUR_2
IDM_VIEW_TAB_COLOUR_3 :: MENUITEM "Apply Color 3",           IDM_VIEW_TAB_COLOUR_3
IDM_VIEW_TAB_COLOUR_4 :: MENUITEM "Apply Color 4",           IDM_VIEW_TAB_COLOUR_4
IDM_VIEW_TAB_COLOUR_5 :: MENUITEM "Apply Color 5",           IDM_VIEW_TAB_COLOUR_5
IDM_VIEW_TAB_COLOUR_NONE :: MENUITEM "Remove Color",            IDM_VIEW_TAB_COLOUR_NONE
44022 | IDM_VIEW_WRAP                                                           |                                                                   | Word wrap                                                                                 |     IDM_VIEW_WRAP :: MENUITEM "&Word wrap",                  IDM_VIEW_WRAP
IDM_VIEW_SWITCHTO_OTHER_VIEW :: MENUITEM "Focus on &Another View",      IDM_VIEW_SWITCHTO_OTHER_VIEW
IDM_VIEW_HIDELINES :: MENUITEM "&Hide Lines",                 IDM_VIEW_HIDELINES
44010 | IDM_VIEW_FOLDALL                                                        |                                                                   | Fold All                                                                                  |     IDM_VIEW_FOLDALL :: MENUITEM "Fold All",                    IDM_VIEW_FOLDALL
44029 | IDM_VIEW_UNFOLDALL                                                      |                                                                   | Unfold All                                                                                |     IDM_VIEW_UNFOLDALL :: MENUITEM "Unfold All",                  IDM_VIEW_UNFOLDALL
44030 | IDM_VIEW_FOLD_CURRENT                                                   |                                                                   | Fold Current Level                                                                        |     IDM_VIEW_FOLD_CURRENT :: MENUITEM "Fold Current Level",          IDM_VIEW_FOLD_CURRENT
44031 | IDM_VIEW_UNFOLD_CURRENT                                                 |                                                                   | Unfold Current Level                                                                      |     IDM_VIEW_UNFOLD_CURRENT :: MENUITEM "Unfold Current Level",        IDM_VIEW_UNFOLD_CURRENT
POPUP "Fold Level"
44051 | IDM_VIEW_FOLD_1                                                         |                                                                   | Fold Level 1                                                                              |         IDM_VIEW_FOLD_1 :: MENUITEM "1",   IDM_VIEW_FOLD_1
44052 | IDM_VIEW_FOLD_2                                                         |                                                                   | Fold Level 2                                                                              |         IDM_VIEW_FOLD_2 :: MENUITEM "2",   IDM_VIEW_FOLD_2
44053 | IDM_VIEW_FOLD_3                                                         |                                                                   | Fold Level 3                                                                              |         IDM_VIEW_FOLD_3 :: MENUITEM "3",   IDM_VIEW_FOLD_3
44054 | IDM_VIEW_FOLD_4                                                         |                                                                   | Fold Level 4                                                                              |         IDM_VIEW_FOLD_4 :: MENUITEM "4",   IDM_VIEW_FOLD_4
44055 | IDM_VIEW_FOLD_5                                                         |                                                                   | Fold Level 5                                                                              |         IDM_VIEW_FOLD_5 :: MENUITEM "5",   IDM_VIEW_FOLD_5
44056 | IDM_VIEW_FOLD_6                                                         |                                                                   | Fold Level 6                                                                              |         IDM_VIEW_FOLD_6 :: MENUITEM "6",   IDM_VIEW_FOLD_6
44057 | IDM_VIEW_FOLD_7                                                         |                                                                   | Fold Level 7                                                                              |         IDM_VIEW_FOLD_7 :: MENUITEM "7",   IDM_VIEW_FOLD_7
44058 | IDM_VIEW_FOLD_8                                                         |                                                                   | Fold Level 8                                                                              |         IDM_VIEW_FOLD_8 :: MENUITEM "8",   IDM_VIEW_FOLD_8
POPUP "Unfold Level"
44061 | IDM_VIEW_UNFOLD_1                                                       |                                                                   | Unfold Level 1                                                                            |         IDM_VIEW_UNFOLD_1 :: MENUITEM "1",    IDM_VIEW_UNFOLD_1
44062 | IDM_VIEW_UNFOLD_2                                                       |                                                                   | Unfold Level 2                                                                            |         IDM_VIEW_UNFOLD_2 :: MENUITEM "2",    IDM_VIEW_UNFOLD_2
44063 | IDM_VIEW_UNFOLD_3                                                       |                                                                   | Unfold Level 3                                                                            |         IDM_VIEW_UNFOLD_3 :: MENUITEM "3",    IDM_VIEW_UNFOLD_3
44064 | IDM_VIEW_UNFOLD_4                                                       |                                                                   | Unfold Level 4                                                                            |         IDM_VIEW_UNFOLD_4 :: MENUITEM "4",    IDM_VIEW_UNFOLD_4
44065 | IDM_VIEW_UNFOLD_5                                                       |                                                                   | Unfold Level 5                                                                            |         IDM_VIEW_UNFOLD_5 :: MENUITEM "5",    IDM_VIEW_UNFOLD_5
44066 | IDM_VIEW_UNFOLD_6                                                       |                                                                   | Unfold Level 6                                                                            |         IDM_VIEW_UNFOLD_6 :: MENUITEM "6",    IDM_VIEW_UNFOLD_6
44067 | IDM_VIEW_UNFOLD_7                                                       |                                                                   | Unfold Level 7                                                                            |         IDM_VIEW_UNFOLD_7 :: MENUITEM "7",    IDM_VIEW_UNFOLD_7
44068 | IDM_VIEW_UNFOLD_8                                                       |                                                                   | Unfold Level 8                                                                            |         IDM_VIEW_UNFOLD_8 :: MENUITEM "8",    IDM_VIEW_UNFOLD_8
IDM_VIEW_SUMMARY :: MENUITEM "&Summary...",  IDM_VIEW_SUMMARY
POPUP "Pro&ject Panels"
IDM_VIEW_PROJECT_PANEL_1 :: MENUITEM "Project Panel &1",          IDM_VIEW_PROJECT_PANEL_1
IDM_VIEW_PROJECT_PANEL_2 :: MENUITEM "Project Panel &2",          IDM_VIEW_PROJECT_PANEL_2
IDM_VIEW_PROJECT_PANEL_3 :: MENUITEM "Project Panel &3",          IDM_VIEW_PROJECT_PANEL_3
IDM_VIEW_FILEBROWSER :: MENUITEM "Folder as Wor&kspace",    IDM_VIEW_FILEBROWSER
IDM_VIEW_DOC_MAP :: MENUITEM "&Document Map",           IDM_VIEW_DOC_MAP
IDM_VIEW_DOCLIST :: MENUITEM "D&ocument List",          IDM_VIEW_DOCLIST
IDM_VIEW_FUNC_LIST :: MENUITEM "Function &List",          IDM_VIEW_FUNC_LIST
44035 | IDM_VIEW_SYNSCROLLV                                                     |                                                                   | Synchronise Vertical Scrolling                                                            |     IDM_VIEW_SYNSCROLLV :: MENUITEM "Sy&nchronize Vertical Scrolling",      IDM_VIEW_SYNSCROLLV
44036 | IDM_VIEW_SYNSCROLLH                                                     |                                                                   | Synchronise Horizontal Scrolling                                                          |     IDM_VIEW_SYNSCROLLH :: MENUITEM "Syn&chronize Horizontal Scrolling",    IDM_VIEW_SYNSCROLLH
42026 | IDM_EDIT_RTL                                                            |                                                                   | Text Direction RTL                                                                        |     IDM_EDIT_RTL :: MENUITEM "T&ext Direction RTL",                  IDM_EDIT_RTL
42027 | IDM_EDIT_LTR                                                            |                                                                   | Text Direction LTR                                                                        |     IDM_EDIT_LTR :: MENUITEM "Te&xt Direction LTR",                  IDM_EDIT_LTR
IDM_VIEW_MONITORING :: MENUITEM "Monito&ring (tail -f)",   IDM_VIEW_MONITORING
POPUP "E&ncoding"
IDM_FORMAT_ANSI :: MENUITEM "ANSI",                    IDM_FORMAT_ANSI
IDM_FORMAT_AS_UTF_8 :: MENUITEM "UTF-8",                   IDM_FORMAT_AS_UTF_8
IDM_FORMAT_UTF_8 :: MENUITEM "UTF-8-BOM",               IDM_FORMAT_UTF_8
IDM_FORMAT_UTF_16BE :: MENUITEM "UTF-16 BE BOM",           IDM_FORMAT_UTF_16BE
IDM_FORMAT_UTF_16LE :: MENUITEM "UTF-16 LE BOM",           IDM_FORMAT_UTF_16LE
POPUP "Character sets"
POPUP "Arabic"
IDM_FORMAT_ISO_8859_6 :: MENUITEM "ISO 8859-6",          IDM_FORMAT_ISO_8859_6
IDM_FORMAT_DOS_720 :: MENUITEM "OEM 720",             IDM_FORMAT_DOS_720
IDM_FORMAT_WIN_1256 :: MENUITEM "Windows-1256",        IDM_FORMAT_WIN_1256
POPUP "Baltic"
IDM_FORMAT_ISO_8859_4 :: MENUITEM "ISO 8859-4",          IDM_FORMAT_ISO_8859_4
IDM_FORMAT_ISO_8859_13 :: MENUITEM "ISO 8859-13",         IDM_FORMAT_ISO_8859_13
IDM_FORMAT_DOS_775 :: MENUITEM "OEM 775",             IDM_FORMAT_DOS_775
IDM_FORMAT_WIN_1257 :: MENUITEM "Windows-1257",        IDM_FORMAT_WIN_1257
POPUP "Celtic"
IDM_FORMAT_ISO_8859_14 :: MENUITEM "ISO 8859-14",         IDM_FORMAT_ISO_8859_14
POPUP "Cyrillic"
IDM_FORMAT_ISO_8859_5 :: MENUITEM "ISO 8859-5",          IDM_FORMAT_ISO_8859_5
IDM_FORMAT_KOI8R_CYRILLIC :: MENUITEM "KOI8-R",              IDM_FORMAT_KOI8R_CYRILLIC
IDM_FORMAT_KOI8U_CYRILLIC :: MENUITEM "KOI8-U",              IDM_FORMAT_KOI8U_CYRILLIC
IDM_FORMAT_MAC_CYRILLIC :: MENUITEM "Macintosh",           IDM_FORMAT_MAC_CYRILLIC
IDM_FORMAT_DOS_855 :: MENUITEM "OEM 855",             IDM_FORMAT_DOS_855
IDM_FORMAT_DOS_866 :: MENUITEM "OEM 866",             IDM_FORMAT_DOS_866
IDM_FORMAT_WIN_1251 :: MENUITEM "Windows-1251",        IDM_FORMAT_WIN_1251
POPUP "Central European"
IDM_FORMAT_DOS_852 :: MENUITEM "OEM 852",             IDM_FORMAT_DOS_852
IDM_FORMAT_WIN_1250 :: MENUITEM "Windows-1250",        IDM_FORMAT_WIN_1250
POPUP "Chinese"
IDM_FORMAT_BIG5 :: MENUITEM "Big5 (Traditional)",  IDM_FORMAT_BIG5
IDM_FORMAT_GB2312 :: MENUITEM "GB2312 (Simplified)", IDM_FORMAT_GB2312
POPUP "Eastern European"
IDM_FORMAT_ISO_8859_2 :: MENUITEM "ISO 8859-2",          IDM_FORMAT_ISO_8859_2
POPUP "Greek"
IDM_FORMAT_ISO_8859_7 :: MENUITEM "ISO 8859-7",          IDM_FORMAT_ISO_8859_7
IDM_FORMAT_DOS_737 :: MENUITEM "OEM 737",             IDM_FORMAT_DOS_737
IDM_FORMAT_DOS_869 :: MENUITEM "OEM 869",             IDM_FORMAT_DOS_869
IDM_FORMAT_WIN_1253 :: MENUITEM "Windows-1253",        IDM_FORMAT_WIN_1253
POPUP "Hebrew"
IDM_FORMAT_ISO_8859_8 :: MENUITEM "ISO 8859-8",          IDM_FORMAT_ISO_8859_8
IDM_FORMAT_DOS_862 :: MENUITEM "OEM 862",             IDM_FORMAT_DOS_862
IDM_FORMAT_WIN_1255 :: MENUITEM "Windows-1255",        IDM_FORMAT_WIN_1255
POPUP "Japanese"
IDM_FORMAT_SHIFT_JIS :: MENUITEM "Shift-JIS",           IDM_FORMAT_SHIFT_JIS
POPUP "Korean"
IDM_FORMAT_KOREAN_WIN :: MENUITEM "Windows 949",              IDM_FORMAT_KOREAN_WIN
IDM_FORMAT_EUC_KR :: MENUITEM "EUC-KR",              IDM_FORMAT_EUC_KR
POPUP "North European"
IDM_FORMAT_DOS_861 :: MENUITEM "OEM 861 : Icelandic",   IDM_FORMAT_DOS_861
IDM_FORMAT_DOS_865 :: MENUITEM "OEM 865 : Nordic",   IDM_FORMAT_DOS_865
POPUP "Thai"
IDM_FORMAT_TIS_620 :: MENUITEM "TIS-620",                 IDM_FORMAT_TIS_620
POPUP "Turkish"
IDM_FORMAT_ISO_8859_3 :: MENUITEM "ISO 8859-3",          IDM_FORMAT_ISO_8859_3
IDM_FORMAT_ISO_8859_9 :: MENUITEM "ISO 8859-9",          IDM_FORMAT_ISO_8859_9
IDM_FORMAT_DOS_857 :: MENUITEM "OEM 857",             IDM_FORMAT_DOS_857
IDM_FORMAT_WIN_1254 :: MENUITEM "Windows-1254",        IDM_FORMAT_WIN_1254
POPUP "Western European"
IDM_FORMAT_ISO_8859_1 :: MENUITEM "ISO 8859-1",          IDM_FORMAT_ISO_8859_1
//IDM_FORMAT_ISO_8859_10 :: MENUITEM "ISO 8859-10",         IDM_FORMAT_ISO_8859_10
IDM_FORMAT_ISO_8859_15 :: MENUITEM "ISO 8859-15",         IDM_FORMAT_ISO_8859_15
IDM_FORMAT_DOS_850 :: MENUITEM "OEM 850",             IDM_FORMAT_DOS_850
IDM_FORMAT_DOS_858 :: MENUITEM "OEM 858",             IDM_FORMAT_DOS_858
IDM_FORMAT_DOS_860 :: MENUITEM "OEM 860 : Portuguese",  IDM_FORMAT_DOS_860
IDM_FORMAT_DOS_863 :: MENUITEM "OEM 863 : French",      IDM_FORMAT_DOS_863
IDM_FORMAT_DOS_437 :: MENUITEM "OEM-US",              IDM_FORMAT_DOS_437
IDM_FORMAT_WIN_1252 :: MENUITEM "Windows-1252",        IDM_FORMAT_WIN_1252
POPUP "Vietnamese"
IDM_FORMAT_WIN_1258 :: MENUITEM "Windows-1258",        IDM_FORMAT_WIN_1258
IDM_FORMAT_CONV2_ANSI :: MENUITEM "Convert to ANSI",            IDM_FORMAT_CONV2_ANSI
IDM_FORMAT_CONV2_AS_UTF_8 :: MENUITEM "Convert to UTF-8",           IDM_FORMAT_CONV2_AS_UTF_8
IDM_FORMAT_CONV2_UTF_8 :: MENUITEM "Convert to UTF-8-BOM",       IDM_FORMAT_CONV2_UTF_8
IDM_FORMAT_CONV2_UTF_16BE :: MENUITEM "Convert to UTF-16 BE BOM",   IDM_FORMAT_CONV2_UTF_16BE
IDM_FORMAT_CONV2_UTF_16LE :: MENUITEM "Convert to UTF-16 LE BOM",   IDM_FORMAT_CONV2_UTF_16LE
POPUP "&Language"
IDM_LANG_TEXT :: MENUITEM "None (Normal Text)",      IDM_LANG_TEXT
IDM_LANG_FLASH :: MENUITEM "ActionScript",            IDM_LANG_FLASH
IDM_LANG_ADA :: MENUITEM "Ada",                     IDM_LANG_ADA
IDM_LANG_ASN1 :: MENUITEM "ASN.1",                   IDM_LANG_ASN1
IDM_LANG_ASP :: MENUITEM "ASP",                     IDM_LANG_ASP
IDM_LANG_ASM :: MENUITEM "Assembly",                IDM_LANG_ASM
IDM_LANG_AU3 :: MENUITEM "AutoIt",                  IDM_LANG_AU3
IDM_LANG_AVS :: MENUITEM "AviSynth",                IDM_LANG_AVS
IDM_LANG_BAANC :: MENUITEM "BaanC",                   IDM_LANG_BAANC
IDM_LANG_BATCH :: MENUITEM "Batch",                   IDM_LANG_BATCH
IDM_LANG_BLITZBASIC :: MENUITEM "Blitzbasic",              IDM_LANG_BLITZBASIC
IDM_LANG_C :: MENUITEM "C",                       IDM_LANG_C
IDM_LANG_CS :: MENUITEM "C#",                      IDM_LANG_CS
IDM_LANG_CPP :: MENUITEM "C++",                     IDM_LANG_CPP
IDM_LANG_CAML :: MENUITEM "Caml",                    IDM_LANG_CAML
IDM_LANG_CMAKE :: MENUITEM "CMake",                   IDM_LANG_CMAKE
IDM_LANG_COBOL :: MENUITEM "COBOL",                   IDM_LANG_COBOL
IDM_LANG_CSOUND :: MENUITEM "CSound",                  IDM_LANG_CSOUND
IDM_LANG_COFFEESCRIPT :: MENUITEM "CoffeeScript",            IDM_LANG_COFFEESCRIPT
IDM_LANG_CSS :: MENUITEM "CSS",                     IDM_LANG_CSS
IDM_LANG_D :: MENUITEM "D",                       IDM_LANG_D
IDM_LANG_DIFF :: MENUITEM "Diff",                    IDM_LANG_DIFF
IDM_LANG_ERLANG :: MENUITEM "Erlang",                  IDM_LANG_ERLANG
IDM_LANG_ERRORLIST :: MENUITEM "ErrorList",               IDM_LANG_ERRORLIST
IDM_LANG_ESCSEQ :: MENUITEM "Escape Sequence (ANSI)",  IDM_LANG_ESCSEQ
IDM_LANG_ESCRIPT :: MENUITEM "ESCRIPT",                 IDM_LANG_ESCRIPT
IDM_LANG_FORTH :: MENUITEM "Forth",                   IDM_LANG_FORTH
IDM_LANG_FORTRAN :: MENUITEM "Fortran (free form)",     IDM_LANG_FORTRAN
IDM_LANG_FORTRAN_77 :: MENUITEM "Fortran (fixed form)",    IDM_LANG_FORTRAN_77
IDM_LANG_FREEBASIC :: MENUITEM "Freebasic",               IDM_LANG_FREEBASIC
IDM_LANG_GDSCRIPT :: MENUITEM "GDScript",                IDM_LANG_GDSCRIPT
IDM_LANG_GOLANG :: MENUITEM "Go",                      IDM_LANG_GOLANG
IDM_LANG_GUI4CLI :: MENUITEM "Gui4Cli",                 IDM_LANG_GUI4CLI
IDM_LANG_HASKELL :: MENUITEM "Haskell",                 IDM_LANG_HASKELL
IDM_LANG_HOLLYWOOD :: MENUITEM "Hollywood",               IDM_LANG_HOLLYWOOD
IDM_LANG_HTML :: MENUITEM "HTML",                    IDM_LANG_HTML
IDM_LANG_INI :: MENUITEM "INI file",                IDM_LANG_INI
IDM_LANG_INNO :: MENUITEM "Inno Setup",              IDM_LANG_INNO
IDM_LANG_IHEX :: MENUITEM "Intel HEX",               IDM_LANG_IHEX
IDM_LANG_JAVA :: MENUITEM "Java",                    IDM_LANG_JAVA
IDM_LANG_JS :: MENUITEM "JavaScript",              IDM_LANG_JS
IDM_LANG_JSON :: MENUITEM "JSON",                    IDM_LANG_JSON
IDM_LANG_JSON5 :: MENUITEM "JSON5",                   IDM_LANG_JSON5
IDM_LANG_JSP :: MENUITEM "JSP",                     IDM_LANG_JSP
IDM_LANG_KIX :: MENUITEM "KIXtart",                 IDM_LANG_KIX
IDM_LANG_LISP :: MENUITEM "LISP",                    IDM_LANG_LISP
IDM_LANG_LATEX :: MENUITEM "LaTeX",                   IDM_LANG_LATEX
IDM_LANG_LUA :: MENUITEM "Lua",                     IDM_LANG_LUA
IDM_LANG_MAKEFILE :: MENUITEM "Makefile",                IDM_LANG_MAKEFILE
IDM_LANG_MATLAB :: MENUITEM "Matlab",                  IDM_LANG_MATLAB
IDM_LANG_MSSQL :: MENUITEM "Microsoft Transact-SQL",  IDM_LANG_MSSQL
IDM_LANG_MMIXAL :: MENUITEM "MMIXAL",                  IDM_LANG_MMIXAL
IDM_LANG_ASCII :: MENUITEM "MS-DOS Style",            IDM_LANG_ASCII
IDM_LANG_NIM :: MENUITEM "Nim",                     IDM_LANG_NIM
IDM_LANG_NNCRONTAB :: MENUITEM "Nncrontab",               IDM_LANG_NNCRONTAB
IDM_LANG_NSIS :: MENUITEM "NSIS",                    IDM_LANG_NSIS
IDM_LANG_OBJC :: MENUITEM "Objective-C",             IDM_LANG_OBJC
IDM_LANG_OSCRIPT :: MENUITEM "OScript",                 IDM_LANG_OSCRIPT
IDM_LANG_PASCAL :: MENUITEM "Pascal",                  IDM_LANG_PASCAL
IDM_LANG_PERL :: MENUITEM "Perl",                    IDM_LANG_PERL
IDM_LANG_PHP :: MENUITEM "PHP",                     IDM_LANG_PHP
IDM_LANG_PS :: MENUITEM "PostScript",              IDM_LANG_PS
IDM_LANG_POWERSHELL :: MENUITEM "PowerShell",              IDM_LANG_POWERSHELL
IDM_LANG_PROPS :: MENUITEM "Properties",              IDM_LANG_PROPS
IDM_LANG_PUREBASIC :: MENUITEM "Purebasic",               IDM_LANG_PUREBASIC
IDM_LANG_PYTHON :: MENUITEM "Python",                  IDM_LANG_PYTHON
IDM_LANG_R :: MENUITEM "R",                       IDM_LANG_R
IDM_LANG_RAKU :: MENUITEM "Raku",                    IDM_LANG_RAKU
IDM_LANG_REBOL :: MENUITEM "REBOL",                   IDM_LANG_REBOL
IDM_LANG_REGISTRY :: MENUITEM "Registry",                IDM_LANG_REGISTRY
IDM_LANG_RC :: MENUITEM "Resource file",           IDM_LANG_RC
IDM_LANG_RUBY :: MENUITEM "Ruby",                    IDM_LANG_RUBY
IDM_LANG_RUST :: MENUITEM "Rust",                    IDM_LANG_RUST
IDM_LANG_SAS :: MENUITEM "SAS",                     IDM_LANG_SAS
IDM_LANG_BASH :: MENUITEM "Shell",                   IDM_LANG_BASH
IDM_LANG_SCHEME :: MENUITEM "Scheme",                  IDM_LANG_SCHEME
IDM_LANG_SMALLTALK :: MENUITEM "Smalltalk",               IDM_LANG_SMALLTALK
IDM_LANG_SPICE :: MENUITEM "Spice",                   IDM_LANG_SPICE
IDM_LANG_SQL :: MENUITEM "SQL",                     IDM_LANG_SQL
IDM_LANG_SWIFT :: MENUITEM "Swift",                  IDM_LANG_SWIFT
IDM_LANG_SREC :: MENUITEM "S-Record",                IDM_LANG_SREC
IDM_LANG_TCL :: MENUITEM "TCL",                     IDM_LANG_TCL
IDM_LANG_TEHEX :: MENUITEM "Tektronix extended HEX",  IDM_LANG_TEHEX
IDM_LANG_TEX :: MENUITEM "TeX",                     IDM_LANG_TEX
IDM_LANG_TOML :: MENUITEM "TOML",                    IDM_LANG_TOML
IDM_LANG_TXT2TAGS :: MENUITEM "txt2tags",                IDM_LANG_TXT2TAGS
IDM_LANG_TYPESCRIPT :: MENUITEM "TypeScript",              IDM_LANG_TYPESCRIPT
IDM_LANG_VERILOG :: MENUITEM "Verilog",                 IDM_LANG_VERILOG
IDM_LANG_VHDL :: MENUITEM "VHDL",                    IDM_LANG_VHDL
IDM_LANG_VB :: MENUITEM "Visual Basic",            IDM_LANG_VB
IDM_LANG_VISUALPROLOG :: MENUITEM "Visual Prolog",           IDM_LANG_VISUALPROLOG
IDM_LANG_XML :: MENUITEM "XML",                     IDM_LANG_XML
IDM_LANG_YAML :: MENUITEM "YAML",                    IDM_LANG_YAML
IDM_LANG_USER_DLG :: MENUITEM "Define your language...", IDM_LANG_USER_DLG
IDM_LANG_OPENUDLDIR :: MENUITEM "Open User Defined Language folder...",      IDM_LANG_OPENUDLDIR
IDM_LANG_UDLCOLLECTION_PROJECT_SITE :: MENUITEM "Notepad++ User Defined Languages Collection", IDM_LANG_UDLCOLLECTION_PROJECT_SITE
IDM_LANG_USER :: MENUITEM "User-Defined",            IDM_LANG_USER
POPUP "&Language"
IDM_LANG_TEXT :: MENUITEM "None (Normal Text)",        IDM_LANG_TEXT
POPUP "A"
IDM_LANG_FLASH :: MENUITEM "ActionScript",          IDM_LANG_FLASH
IDM_LANG_ADA :: MENUITEM "Ada",                   IDM_LANG_ADA
IDM_LANG_ASN1 :: MENUITEM "ASN.1",                 IDM_LANG_ASN1
IDM_LANG_ASP :: MENUITEM "ASP",                   IDM_LANG_ASP
IDM_LANG_ASM :: MENUITEM "Assembly",              IDM_LANG_ASM
IDM_LANG_AU3 :: MENUITEM "AutoIt",                IDM_LANG_AU3
IDM_LANG_AVS :: MENUITEM "AviSynth",              IDM_LANG_AVS
POPUP "B"
IDM_LANG_BAANC :: MENUITEM "BaanC",                 IDM_LANG_BAANC
IDM_LANG_BATCH :: MENUITEM "Batch",                 IDM_LANG_BATCH
IDM_LANG_BLITZBASIC :: MENUITEM "Blitzbasic",            IDM_LANG_BLITZBASIC
POPUP "C"
IDM_LANG_C :: MENUITEM "C",                     IDM_LANG_C
IDM_LANG_CS :: MENUITEM "C#",                    IDM_LANG_CS
IDM_LANG_CPP :: MENUITEM "C++",                   IDM_LANG_CPP
IDM_LANG_CAML :: MENUITEM "Caml",                  IDM_LANG_CAML
IDM_LANG_CMAKE :: MENUITEM "CMake",                 IDM_LANG_CMAKE
IDM_LANG_COBOL :: MENUITEM "COBOL",                 IDM_LANG_COBOL
IDM_LANG_CSOUND :: MENUITEM "CSound",                IDM_LANG_CSOUND
IDM_LANG_COFFEESCRIPT :: MENUITEM "CoffeeScript",          IDM_LANG_COFFEESCRIPT
IDM_LANG_CSS :: MENUITEM "CSS",                   IDM_LANG_CSS
POPUP "D"
IDM_LANG_D :: MENUITEM "D",                     IDM_LANG_D
IDM_LANG_DIFF :: MENUITEM "Diff",                  IDM_LANG_DIFF
POPUP "E"
IDM_LANG_ERLANG :: MENUITEM "Erlang",                    IDM_LANG_ERLANG
IDM_LANG_ERRORLIST :: MENUITEM "ErrorList",                 IDM_LANG_ERRORLIST
IDM_LANG_ESCSEQ :: MENUITEM "Escape Sequence (ANSI)",    IDM_LANG_ESCSEQ
IDM_LANG_ESCRIPT :: MENUITEM "ESCRIPT",                   IDM_LANG_ESCRIPT
POPUP "F"
IDM_LANG_FORTH :: MENUITEM "Forth",                 IDM_LANG_FORTH
IDM_LANG_FORTRAN :: MENUITEM "Fortran (free form)",   IDM_LANG_FORTRAN
IDM_LANG_FORTRAN_77 :: MENUITEM "Fortran (fixed form)",  IDM_LANG_FORTRAN_77
IDM_LANG_FREEBASIC :: MENUITEM "Freebasic",             IDM_LANG_FREEBASIC
POPUP "G"
IDM_LANG_GDSCRIPT :: MENUITEM "GDScript",                  IDM_LANG_GDSCRIPT
IDM_LANG_GOLANG :: MENUITEM "Go",                        IDM_LANG_GOLANG
IDM_LANG_GUI4CLI :: MENUITEM "Gui4Cli",                   IDM_LANG_GUI4CLI
POPUP "H"
IDM_LANG_HASKELL :: MENUITEM "Haskell",               IDM_LANG_HASKELL
IDM_LANG_HOLLYWOOD :: MENUITEM "Hollywood",             IDM_LANG_HOLLYWOOD
IDM_LANG_HTML :: MENUITEM "HTML",                  IDM_LANG_HTML
POPUP "I"
IDM_LANG_INI :: MENUITEM "INI file",              IDM_LANG_INI
IDM_LANG_INNO :: MENUITEM "Inno Setup",            IDM_LANG_INNO
IDM_LANG_IHEX :: MENUITEM "Intel HEX",             IDM_LANG_IHEX
POPUP "J"
IDM_LANG_JAVA :: MENUITEM "Java",                  IDM_LANG_JAVA
IDM_LANG_JS :: MENUITEM "JavaScript",            IDM_LANG_JS
IDM_LANG_JSON :: MENUITEM "JSON",                  IDM_LANG_JSON
IDM_LANG_JSON5 :: MENUITEM "JSON5",                 IDM_LANG_JSON5
IDM_LANG_JSP :: MENUITEM "JSP",                   IDM_LANG_JSP
IDM_LANG_KIX :: MENUITEM "KIXtart",                   IDM_LANG_KIX
POPUP "L"
IDM_LANG_LATEX :: MENUITEM "LaTeX",                 IDM_LANG_LATEX
IDM_LANG_LISP :: MENUITEM "LISP",                  IDM_LANG_LISP
IDM_LANG_LUA :: MENUITEM "Lua",                   IDM_LANG_LUA
POPUP "M"
IDM_LANG_MAKEFILE :: MENUITEM "Makefile",              IDM_LANG_MAKEFILE
IDM_LANG_MATLAB :: MENUITEM "Matlab",                IDM_LANG_MATLAB
IDM_LANG_MSSQL :: MENUITEM "Microsoft Transact-SQL",IDM_LANG_MSSQL
IDM_LANG_MMIXAL :: MENUITEM "MMIXAL",                IDM_LANG_MMIXAL
IDM_LANG_ASCII :: MENUITEM "MS-DOS Style",          IDM_LANG_ASCII
POPUP "N"
IDM_LANG_NIM :: MENUITEM "Nim",                   IDM_LANG_NIM
IDM_LANG_NNCRONTAB :: MENUITEM "Nncrontab",             IDM_LANG_NNCRONTAB
IDM_LANG_NSIS :: MENUITEM "NSIS",                  IDM_LANG_NSIS
POPUP "O"
IDM_LANG_OBJC :: MENUITEM "Objective-C",           IDM_LANG_OBJC
IDM_LANG_OSCRIPT :: MENUITEM "OScript",               IDM_LANG_OSCRIPT
POPUP "P"
IDM_LANG_PASCAL :: MENUITEM "Pascal",                IDM_LANG_PASCAL
IDM_LANG_PERL :: MENUITEM "Perl",                  IDM_LANG_PERL
IDM_LANG_PHP :: MENUITEM "PHP",                   IDM_LANG_PHP
IDM_LANG_PS :: MENUITEM "PostScript",            IDM_LANG_PS
IDM_LANG_POWERSHELL :: MENUITEM "PowerShell",            IDM_LANG_POWERSHELL
IDM_LANG_PROPS :: MENUITEM "Properties",            IDM_LANG_PROPS
IDM_LANG_PUREBASIC :: MENUITEM "Purebasic",             IDM_LANG_PUREBASIC
IDM_LANG_PYTHON :: MENUITEM "Python",                IDM_LANG_PYTHON
POPUP "R"
IDM_LANG_R :: MENUITEM "R",                     IDM_LANG_R
IDM_LANG_RAKU :: MENUITEM "Raku",                  IDM_LANG_RAKU
IDM_LANG_REBOL :: MENUITEM "REBOL",                 IDM_LANG_REBOL
IDM_LANG_REGISTRY :: MENUITEM "Registry",              IDM_LANG_REGISTRY
IDM_LANG_RC :: MENUITEM "Resource file",         IDM_LANG_RC
IDM_LANG_RUBY :: MENUITEM "Ruby",                  IDM_LANG_RUBY
IDM_LANG_RUST :: MENUITEM "Rust",                  IDM_LANG_RUST
POPUP "S"
IDM_LANG_SAS :: MENUITEM "SAS",                   IDM_LANG_SAS
IDM_LANG_BASH :: MENUITEM "Shell",                 IDM_LANG_BASH
IDM_LANG_SCHEME :: MENUITEM "Scheme",                IDM_LANG_SCHEME
IDM_LANG_SMALLTALK :: MENUITEM "Smalltalk",             IDM_LANG_SMALLTALK
IDM_LANG_SPICE :: MENUITEM "Spice",                 IDM_LANG_SPICE
IDM_LANG_SQL :: MENUITEM "SQL",                   IDM_LANG_SQL
IDM_LANG_SWIFT :: MENUITEM "Swift",                IDM_LANG_SWIFT
IDM_LANG_SREC :: MENUITEM "S-Record",              IDM_LANG_SREC
POPUP "T"
IDM_LANG_TCL :: MENUITEM "TCL",                   IDM_LANG_TCL
IDM_LANG_TEHEX :: MENUITEM "Tektronix extended HEX",IDM_LANG_TEHEX
IDM_LANG_TEX :: MENUITEM "TeX",                   IDM_LANG_TEX
IDM_LANG_TOML :: MENUITEM "TOML",                  IDM_LANG_TOML
IDM_LANG_TXT2TAGS :: MENUITEM "txt2tags",              IDM_LANG_TXT2TAGS
IDM_LANG_TYPESCRIPT :: MENUITEM "TypeScript",            IDM_LANG_TYPESCRIPT
POPUP "V"
IDM_LANG_VB :: MENUITEM "Visual Basic",          IDM_LANG_VB
IDM_LANG_VISUALPROLOG :: MENUITEM "Visual Prolog",         IDM_LANG_VISUALPROLOG
IDM_LANG_VHDL :: MENUITEM "VHDL",                  IDM_LANG_VHDL
IDM_LANG_VERILOG :: MENUITEM "Verilog",               IDM_LANG_VERILOG
IDM_LANG_XML :: MENUITEM "XML",                       IDM_LANG_XML
IDM_LANG_YAML :: MENUITEM "YAML",                      IDM_LANG_YAML
POPUP "User Defined Language"
IDM_LANG_USER_DLG :: MENUITEM "Define your language...",   IDM_LANG_USER_DLG
IDM_LANG_OPENUDLDIR :: MENUITEM "Open User Defined Language folder...",        IDM_LANG_OPENUDLDIR
IDM_LANG_UDLCOLLECTION_PROJECT_SITE :: MENUITEM "Notepad++ User Defined Languages Collection", IDM_LANG_UDLCOLLECTION_PROJECT_SITE
IDM_LANG_USER :: MENUITEM "User-Defined",              IDM_LANG_USER
POPUP "Se&ttings"
IDM_SETTING_PREFERENCE :: MENUITEM "Preferences...",          IDM_SETTING_PREFERENCE
IDM_LANGSTYLE_CONFIG_DLG :: MENUITEM "Style Configurator...",   IDM_LANGSTYLE_CONFIG_DLG
IDM_SETTING_SHORTCUT_MAPPER :: MENUITEM "Shortcut Mapper...",      IDM_SETTING_SHORTCUT_MAPPER
POPUP "Import"
IDM_SETTING_IMPORTPLUGIN :: MENUITEM "Import plugin(s)...",         IDM_SETTING_IMPORTPLUGIN
IDM_SETTING_IMPORTSTYLETHEMES :: MENUITEM "Import style theme(s)...",    IDM_SETTING_IMPORTSTYLETHEMES
IDM_SETTING_EDITCONTEXTMENU :: MENUITEM "Edit Popup ContextMenu",      IDM_SETTING_EDITCONTEXTMENU
POPUP "T&ools"
POPUP "MD5"
IDM_TOOL_MD5_GENERATE :: MENUITEM "Generate...",                            IDM_TOOL_MD5_GENERATE
IDM_TOOL_MD5_GENERATEFROMFILE :: MENUITEM "Generate from files...",                 IDM_TOOL_MD5_GENERATEFROMFILE
IDM_TOOL_MD5_GENERATEINTOCLIPBOARD :: MENUITEM "Generate from selection into clipboard", IDM_TOOL_MD5_GENERATEINTOCLIPBOARD
POPUP "SHA-1"
IDM_TOOL_SHA1_GENERATE :: MENUITEM "Generate...", IDM_TOOL_SHA1_GENERATE
IDM_TOOL_SHA1_GENERATEFROMFILE :: MENUITEM "Generate from files...", IDM_TOOL_SHA1_GENERATEFROMFILE
IDM_TOOL_SHA1_GENERATEINTOCLIPBOARD :: MENUITEM "Generate from selection into clipboard", IDM_TOOL_SHA1_GENERATEINTOCLIPBOARD
POPUP "SHA-256"
IDM_TOOL_SHA256_GENERATE :: MENUITEM "Generate...", IDM_TOOL_SHA256_GENERATE
IDM_TOOL_SHA256_GENERATEFROMFILE :: MENUITEM "Generate from files...", IDM_TOOL_SHA256_GENERATEFROMFILE
IDM_TOOL_SHA256_GENERATEINTOCLIPBOARD :: MENUITEM "Generate from selection into clipboard", IDM_TOOL_SHA256_GENERATEINTOCLIPBOARD
POPUP "SHA-512"
IDM_TOOL_SHA512_GENERATE :: MENUITEM "Generate...", IDM_TOOL_SHA512_GENERATE
IDM_TOOL_SHA512_GENERATEFROMFILE :: MENUITEM "Generate from files...", IDM_TOOL_SHA512_GENERATEFROMFILE
IDM_TOOL_SHA512_GENERATEINTOCLIPBOARD :: MENUITEM "Generate from selection into clipboard", IDM_TOOL_SHA512_GENERATEINTOCLIPBOARD
POPUP "&Macro"
IDM_MACRO_STARTRECORDINGMACRO :: MENUITEM "Start Re&cording",                   IDM_MACRO_STARTRECORDINGMACRO
IDM_MACRO_STOPRECORDINGMACRO :: MENUITEM "S&top Recording",                    IDM_MACRO_STOPRECORDINGMACRO
IDM_MACRO_PLAYBACKRECORDEDMACRO :: MENUITEM "&Playback",                          IDM_MACRO_PLAYBACKRECORDEDMACRO
IDM_MACRO_SAVECURRENTMACRO :: MENUITEM "&Save Current Recorded Macro...",    IDM_MACRO_SAVECURRENTMACRO
IDM_MACRO_RUNMULTIMACRODLG :: MENUITEM "&Run a Macro Multiple Times...",     IDM_MACRO_RUNMULTIMACRODLG
POPUP "&Run"
IDM_EXECUTE :: MENUITEM "&Run...",    IDM_EXECUTE
IDM_EXECUTE_VALIDATE_SHORTCUTSXML :: MENUITEM "Validate shortcuts.xml",    IDM_EXECUTE_VALIDATE_SHORTCUTSXML
POPUP "&Plugins"
IDM_SETTING_OPENPLUGINSDIR :: MENUITEM "Open Plugins Folder...",    IDM_SETTING_OPENPLUGINSDIR
POPUP "&Window"
POPUP "Sort By"
IDM_WINDOW_SORT_FN_ASC :: MENUITEM "Name A to Z",                 IDM_WINDOW_SORT_FN_ASC
IDM_WINDOW_SORT_FN_DSC :: MENUITEM "Name Z to A",                 IDM_WINDOW_SORT_FN_DSC
IDM_WINDOW_SORT_FP_ASC :: MENUITEM "Path A to Z",                 IDM_WINDOW_SORT_FP_ASC
IDM_WINDOW_SORT_FP_DSC :: MENUITEM "Path Z to A",                 IDM_WINDOW_SORT_FP_DSC
IDM_WINDOW_SORT_FT_ASC :: MENUITEM "Type A to Z",                 IDM_WINDOW_SORT_FT_ASC
IDM_WINDOW_SORT_FT_DSC :: MENUITEM "Type Z to A",                 IDM_WINDOW_SORT_FT_DSC
IDM_WINDOW_SORT_FS_ASC :: MENUITEM "Content Length Ascending",    IDM_WINDOW_SORT_FS_ASC
IDM_WINDOW_SORT_FS_DSC :: MENUITEM "Content Length Descending",   IDM_WINDOW_SORT_FS_DSC
IDM_WINDOW_SORT_FD_ASC :: MENUITEM "Modified Time Ascending",     IDM_WINDOW_SORT_FD_ASC
IDM_WINDOW_SORT_FD_DSC :: MENUITEM "Modified Time Descending",    IDM_WINDOW_SORT_FD_DSC
IDM_WINDOW_WINDOWS :: MENUITEM "&Windows...",                 IDM_WINDOW_WINDOWS
MENUITEM "Recent Window",               IDM_WINDOW_MRU_FIRST, GRAYED
POPUP "&?"
IDM_CMDLINEARGUMENTS :: MENUITEM "Command Line Arguments...",      IDM_CMDLINEARGUMENTS
IDM_HOMESWEETHOME :: MENUITEM "Notepad++ Home",                 IDM_HOMESWEETHOME
IDM_PROJECTPAGE :: MENUITEM "Notepad++ Project Page",         IDM_PROJECTPAGE
IDM_ONLINEDOCUMENT :: MENUITEM "Notepad++ Online User Manual",   IDM_ONLINEDOCUMENT
IDM_FORUM :: MENUITEM "Notepad++ Community (Forum)",    IDM_FORUM
IDM_UPDATE_NPP :: MENUITEM "Update Notepad++",               IDM_UPDATE_NPP
IDM_CONFUPDATERPROXY :: MENUITEM "Set Updater Proxy...",           IDM_CONFUPDATERPROXY
IDM_DEBUGINFO :: MENUITEM "Debug Info...",                  IDM_DEBUGINFO
IDM_ABOUT :: MENUITEM "About Notepad++",                IDM_ABOUT
MENUITEM "＋",               IDM_FILE_NEW, HELP
POPUP "▼"
MENUITEM "Recent Window",               IDM_DROPLIST_LIST, GRAYED
MENUITEM "✕",               IDM_FILE_CLOSE, HELP

===============================

10001 | IDM_VIEW_GOTO_ANOTHER_VIEW                                              | View > Move/Clone Current Document                                | Move to Other View                                                                        |
10002 | IDM_VIEW_CLONE_TO_ANOTHER_VIEW                                          | View > Move/Clone Current Document                                | Clone to Other View                                                                       |
10003 | IDM_VIEW_GOTO_NEW_INSTANCE                                              | View > Move/Clone Current Document                                | Move to New Instance                                                                      |
10004 | IDM_VIEW_LOAD_IN_NEW_INSTANCE                                           | View > Move/Clone Current Document                                | Open in New Instance                                                                      |
10005 | IDM_VIEW_GOTO_START                                                     | View > Tab                                                        | Move to Start                                                                             |
10006 | IDM_VIEW_GOTO_END                                                       | View > Tab                                                        | Move to End                                                                               |
41001 | IDM_FILE_NEW                                                            | File                                                              | New                                                                                       |
41001 | IDM_FILE_OPEN                                                           | File                                                              | Open                                                                                      |
41003 | IDM_FILE_CLOSE                                                          | File                                                              | Close                                                                                     |
41004 | IDM_FILE_CLOSEALL                                                       | File                                                              | Close All                                                                                 |
41005 | IDM_FILE_CLOSEALL_BUT_CURRENT                                           | File > Close Multiple Documents                                   | Close All BUT Current Document                                                            |
41006 | IDM_FILE_SAVE                                                           | File                                                              | Save                                                                                      |
41007 | IDM_FILE_SAVEALL                                                        | File                                                              | Save All                                                                                  |
41009 | IDM_FILE_CLOSEALL_TOLEFT                                                | File > Close Multiple Documents                                   | Close All to the Left                                                                     |
41014 | IDM_FILE_RELOAD                                                         | File                                                              | Reload from Disk                                                                          |
41018 | IDM_FILE_CLOSEALL_TORIGHT                                               | File > Close Multiple Documents                                   | Close All to the Right                                                                    |
41024 | IDM_FILE_CLOSEALL_UNCHANGED                                             | File > Close Multiple Documents                                   | Close All Unchanged                                                                       |
41026 | IDM_FILE_CLOSEALL_BUT_PINNED                                            | File > Close Multiple Documents                                   | Close All BUT Pinned Documents                                                            |
42001 | IDM_EDIT_CUT                                                            | Edit                                                              | Cut                                                                                       |
42002 | IDM_EDIT_COPY                                                           | Edit                                                              | Copy                                                                                      |
42003 | IDM_EDIT_UNDO                                                           | Edit                                                              | Undo                                                                                      |
42004 | IDM_EDIT_REDO                                                           | Edit                                                              | Redo                                                                                      |
42005 | IDM_EDIT_PASTE                                                          | Edit                                                              | Paste                                                                                     |
42006 | IDM_EDIT_DELETE                                                         | Edit                                                              | Delete                                                                                    |
42007 | IDM_EDIT_SELECTALL                                                      | Edit                                                              | Select All                                                                                |
42008 | IDM_EDIT_INS_TAB                                                        | Edit > Indent                                                     | Increase Line Indent                                                                      |
42009 | IDM_EDIT_RMV_TAB                                                        | Edit > Indent                                                     | Decrease Line Indent                                                                      |
42010 | IDM_EDIT_DUP_LINE                                                       |                                                                   | Duplicate Current Line                                                                    |
42011 | IDM_EDIT_TRANSPOSE_LINE                                                 |                                                                   | Transpose Line                                                                            |
42012 | IDM_EDIT_SPLIT_LINES                                                    |                                                                   | Split Lines                                                                               |
42013 | IDM_EDIT_JOIN_LINES                                                     |                                                                   | Join Lines                                                                                |
42014 | IDM_EDIT_LINE_UP                                                        |                                                                   | Move Up Current Line                                                                      |
42015 | IDM_EDIT_LINE_DOWN                                                      |                                                                   | Move Down Current Line                                                                    |
42016 | IDM_EDIT_UPPERCASE                                                      |                                                                   | UPPERCASE                                                                                 |
42017 | IDM_EDIT_LOWERCASE                                                      |                                                                   | lowercase                                                                                 |
42020 | IDM_EDIT_BEGINENDSELECT                                                 |                                                                   | Begin/End Select                                                                          |
42022 | IDM_EDIT_BLOCK_COMMENT                                                  |                                                                   | Toggle Single Line Comment                                                                |
42023 | IDM_EDIT_STREAM_COMMENT                                                 |                                                                   | Block Comment                                                                             |
42024 | IDM_EDIT_TRIMTRAILING                                                   |                                                                   | Trim Trailing Space                                                                       |
42026 | IDM_EDIT_RTL                                                            |                                                                   | Text Direction RTL                                                                        |
42027 | IDM_EDIT_LTR                                                            |                                                                   | Text Direction LTR                                                                        |
42028 | IDM_EDIT_TOGGLEREADONLY                                                 |                                                                   | Read-Only on Current Document                                                             |
42029 | IDM_EDIT_FULLPATHTOCLIP                                                 |                                                                   | Copy Current File Path                                                                    |
42030 | IDM_EDIT_FILENAMETOCLIP                                                 |                                                                   | Copy Current Filename                                                                     |
42031 | IDM_EDIT_CURRENTDIRTOCLIP                                               |                                                                   | Copy Current Dir. Path                                                                    |
42033 | IDM_EDIT_TOGGLESYSTEMREADONLY                                           |                                                                   | Read-Only Attribute in Windows                                                            |
42035 | IDM_EDIT_BLOCK_COMMENT_SET                                              |                                                                   | Single Line Comment                                                                       |
42036 | IDM_EDIT_BLOCK_UNCOMMENT                                                |                                                                   | Single Line Uncomment                                                                     |
42042 | IDM_EDIT_TRIMLINEHEAD                                                   |                                                                   | Trim Leading Space                                                                        |
42043 | IDM_EDIT_TRIM_BOTH                                                      |                                                                   | Trim Leading and Trailing Space                                                           |
42044 | IDM_EDIT_EOL2WS                                                         |                                                                   | EOL to Space                                                                              |
42045 | IDM_EDIT_TRIMALL                                                        |                                                                   | Trim both and EOL to Space                                                                |
42046 | IDM_EDIT_TAB2SW                                                         |                                                                   | TAB to Space                                                                              |
42053 | IDM_EDIT_SW2TAB_LEADING                                                 |                                                                   | Space to TAB (Leading)                                                                    |
42054 | IDM_EDIT_SW2TAB_ALL                                                     |                                                                   | Space to TAB (All)                                                                        |
42055 | IDM_EDIT_REMOVEEMPTYLINES                                               |                                                                   | Remove Empty Lines                                                                        |
42056 | IDM_EDIT_REMOVEEMPTYLINESWITHBLANK                                      |                                                                   | Remove Empty Lines (Containing Blank characters)                                          |
42057 | IDM_EDIT_BLANKLINEABOVECURRENT                                          |                                                                   | Insert Blank Line Above Current                                                           |
42058 | IDM_EDIT_BLANKLINEBELOWCURRENT                                          |                                                                   | Insert Blank Line Below Current                                                           |
42059 | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING                              |                                                                   | Sort Lines Lexicographically Ascending                                                    |
42060 | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING                             |                                                                   | Sort Lines Lexicographically Descending                                                   |
42061 | IDM_EDIT_SORTLINES_INTEGER_ASCENDING                                    |                                                                   | Sort Lines As Integers Ascending                                                          |
42062 | IDM_EDIT_SORTLINES_INTEGER_DESCENDING                                   |                                                                   | Sort Lines As Integers Descending                                                         |
42063 | IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING                               |                                                                   | Sort Lines As Decimals (Comma) Ascending                                                  |
42064 | IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING                              |                                                                   | Sort Lines As Decimals (Comma) Descending                                                 |
42065 | IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING                                 |                                                                   | Sort Lines As Decimals (Dot) Ascending                                                    |
42066 | IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING                                |                                                                   | Sort Lines As Decimals (Dot) Descending                                                   |
42067 | IDM_EDIT_PROPERCASE_FORCE                                               |                                                                   | Proper Case                                                                               |
42068 | IDM_EDIT_PROPERCASE_BLEND                                               |                                                                   | Proper Case (blend)                                                                       |
42069 | IDM_EDIT_SENTENCECASE_FORCE                                             |                                                                   | Sentence case                                                                             |
42070 | IDM_EDIT_SENTENCECASE_BLEND                                             |                                                                   | Sentence case (blend)                                                                     |
42071 | IDM_EDIT_INVERTCASE                                                     |                                                                   | iNVERT cASE                                                                               |
42072 | IDM_EDIT_RANDOMCASE                                                     |                                                                   | ranDOm CasE                                                                               |
42077 | IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES                                   |                                                                   | Remove Consecutive Duplicate Lines                                                        |
42078 | IDM_EDIT_SORTLINES_RANDOMLY                                             |                                                                   | Randomize Line Order                                                                      |
42079 | IDM_EDIT_REMOVE_ANY_DUP_LINES                                           |                                                                   | Remove Duplicate Lines                                                                    |
42080 | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING                         |                                                                   | Sort Lines Lex. Ascending Ignoring Case                                                   |
42081 | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING                        |                                                                   | Sort Lines Lex. Descending Ignoring Case                                                  |
42083 | IDM_EDIT_SORTLINES_REVERSE_ORDER                                        |                                                                   | Reverse Line Order                                                                        |
42084 | IDM_EDIT_INSERT_DATETIME_SHORT                                          |                                                                   | Date Time (short)                                                                         |
42085 | IDM_EDIT_INSERT_DATETIME_LONG                                           |                                                                   | Date Time (long)                                                                          |
42086 | IDM_EDIT_INSERT_DATETIME_CUSTOMIZED                                     |                                                                   | Date Time (customized)                                                                    |
42087 | IDM_EDIT_COPY_ALL_NAMES                                                 |                                                                   | Copy All Filenames                                                                        |
42088 | IDM_EDIT_COPY_ALL_PATHS                                                 |                                                                   | Copy All File Paths                                                                       |
42089 | IDM_EDIT_BEGINENDSELECT_COLUMNMODE                                      |                                                                   | Begin/End Select in Column Mode                                                           |
42092 | IDM_EDIT_MULTISELECTALLWHOLEWORD                                        |                                                                   | Match Whole Word Only                                                                     |
42093 | IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD                               |                                                                   | Match Case  Whole Word                                                                    |
42094 | IDM_EDIT_MULTISELECTNEXT                                                |                                                                   | Ignore Case  Whole Word                                                                   |
42095 | IDM_EDIT_MULTISELECTNEXTMATCHCASE                                       |                                                                   | Match Case Only                                                                           |
42096 | IDM_EDIT_MULTISELECTNEXTWHOLEWORD                                       |                                                                   | Match Whole Word Only                                                                     |
42097 | IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD                              |                                                                   | Match Case  Whole Word                                                                    |
42098 | IDM_EDIT_MULTISELECTUNDO                                                |                                                                   | Undo the Latest Added Multi-Select                                                        |
42099 | IDM_EDIT_MULTISELECTSSKIP                                               |                                                                   | Skip Current  Go to Next Multi-select                                                     |
42100 | IDM_EDIT_SORTLINES_LOCALE_ASCENDING                                     |                                                                   | Sort Lines In Locale Order Ascending                                                      |
42101 | IDM_EDIT_SORTLINES_LOCALE_DESCENDING                                    |                                                                   | Sort Lines In Locale Order Descending                                                     |
42102 | IDM_EDIT_SETREADONLYFORALLDOCS                                          |                                                                   | Read-Only for All Documents                                                               |
42103 | IDM_EDIT_CLEARREADONLYFORALLDOCS                                        |                                                                   | Clear Read-Only for All Documents                                                         |
42104 | IDM_EDIT_SORTLINES_LENGTH_ASCENDING                                     |                                                                   | Sort Lines By Length Ascending                                                            |
42105 | IDM_EDIT_SORTLINES_LENGTH_DESCENDING                                    |                                                                   | Sort Lines By Length Descending                                                           |
42106 | IDM_EDIT_REDACT_SELECTION                                               |                                                                   | Redact Selection █ (Shift: ●)                                                             |
43002 | IDM_SEARCH_FINDNEXT                                                     |                                                                   | Find Next                                                                                 |
43005 | IDM_SEARCH_TOGGLE_BOOKMARK                                              |                                                                   | Toggle Bookmark                                                                           |
43006 | IDM_SEARCH_NEXT_BOOKMARK                                                |                                                                   | Next Bookmark                                                                             |
43007 | IDM_SEARCH_PREV_BOOKMARK                                                |                                                                   | Previous Bookmark                                                                         |
43008 | IDM_SEARCH_CLEAR_BOOKMARKS                                              |                                                                   | Clear All Bookmarks                                                                       |
43009 | IDM_SEARCH_GOTOMATCHINGBRACE                                            |                                                                   | Go to Matching Brace                                                                      |
43010 | IDM_SEARCH_FINDPREV                                                     |                                                                   | Find Previous                                                                             |
43014 | IDM_SEARCH_VOLATILE_FINDNEXT                                            |                                                                   | Find (Volatile) Next                                                                      |
43015 | IDM_SEARCH_VOLATILE_FINDPREV                                            |                                                                   | Find (Volatile) Previous                                                                  |
43018 | IDM_SEARCH_CUTMARKEDLINES                                               |                                                                   | Cut Bookmarked Lines                                                                      |
43019 | IDM_SEARCH_COPYMARKEDLINES                                              |                                                                   | Copy Bookmarked Lines                                                                     |
43020 | IDM_SEARCH_PASTEMARKEDLINES                                             |                                                                   | Paste to (Replace) Bookmarked Lines                                                       |
43021 | IDM_SEARCH_DELETEMARKEDLINES                                            |                                                                   | Remove Bookmarked Lines                                                                   |
43022 | IDM_SEARCH_MARKALLEXT1                                                  |                                                                   | Using 1st Style                                                                           |
43023 | IDM_SEARCH_UNMARKALLEXT1                                                |                                                                   | Clear 1st Style                                                                           |
43024 | IDM_SEARCH_MARKALLEXT2                                                  |                                                                   | Using 2nd Style                                                                           |
43025 | IDM_SEARCH_UNMARKALLEXT2                                                |                                                                   | Clear 2nd Style                                                                           |
43026 | IDM_SEARCH_MARKALLEXT3                                                  |                                                                   | Using 3rd Style                                                                           |
43027 | IDM_SEARCH_UNMARKALLEXT3                                                |                                                                   | Clear 3rd Style                                                                           |
43028 | IDM_SEARCH_MARKALLEXT4                                                  |                                                                   | Using 4th Style                                                                           |
43029 | IDM_SEARCH_UNMARKALLEXT4                                                |                                                                   | Clear 4th Style                                                                           |
43030 | IDM_SEARCH_MARKALLEXT5                                                  |                                                                   | Using 5th Style                                                                           |
43031 | IDM_SEARCH_UNMARKALLEXT5                                                |                                                                   | Clear 5th Style                                                                           |
43032 | IDM_SEARCH_CLEARALLMARKS                                                |                                                                   | Clear All Styles                                                                          |
43033 | IDM_SEARCH_GOPREVMARKER1                                                |                                                                   | 1st style                                                                                 |
43034 | IDM_SEARCH_GOPREVMARKER2                                                |                                                                   | 2nd style                                                                                 |
43035 | IDM_SEARCH_GOPREVMARKER3                                                |                                                                   | 3rd style                                                                                 |
43036 | IDM_SEARCH_GOPREVMARKER4                                                |                                                                   | 4th style                                                                                 |
43037 | IDM_SEARCH_GOPREVMARKER5                                                |                                                                   | 5th style                                                                                 |
43038 | IDM_SEARCH_GOPREVMARKER_DEF                                             |                                                                   | Find Mark Style                                                                           |
43039 | IDM_SEARCH_GONEXTMARKER1                                                |                                                                   | 1st style                                                                                 |
43040 | IDM_SEARCH_GONEXTMARKER2                                                |                                                                   | 2nd style                                                                                 |
43041 | IDM_SEARCH_GONEXTMARKER3                                                |                                                                   | 3rd style                                                                                 |
43042 | IDM_SEARCH_GONEXTMARKER4                                                |                                                                   | 4th style                                                                                 |
43043 | IDM_SEARCH_GONEXTMARKER5                                                |                                                                   | 5th style                                                                                 |
43044 | IDM_SEARCH_GONEXTMARKER_DEF                                             |                                                                   | Find Mark Style                                                                           |
43048 | IDM_SEARCH_SETANDFINDNEXT                                               |                                                                   | Select and Find Next                                                                      |
43049 | IDM_SEARCH_SETANDFINDPREV                                               |                                                                   | Select and Find Previous                                                                  |
43050 | IDM_SEARCH_INVERSEMARKS                                                 |                                                                   | Inverse Bookmarks                                                                         |
43051 | IDM_SEARCH_DELETEUNMARKEDLINES                                          |                                                                   | Remove Non-Bookmarked Lines                                                               |
43053 | IDM_SEARCH_SELECTMATCHINGBRACES                                         |                                                                   | Select All In-between {} [] or ()                                                         |
43055 | IDM_SEARCH_STYLE1TOCLIP                                                 |                                                                   | 1st Style                                                                                 |
43056 | IDM_SEARCH_STYLE2TOCLIP                                                 |                                                                   | 2nd Style                                                                                 |
43057 | IDM_SEARCH_STYLE3TOCLIP                                                 |                                                                   | 3rd Style                                                                                 |
43058 | IDM_SEARCH_STYLE4TOCLIP                                                 |                                                                   | 4th Style                                                                                 |
43059 | IDM_SEARCH_STYLE5TOCLIP                                                 |                                                                   | 5th Style                                                                                 |
43060 | IDM_SEARCH_ALLSTYLESTOCLIP                                              |                                                                   | All Styles                                                                                |
43061 | IDM_SEARCH_MARKEDTOCLIP                                                 |                                                                   | Find Mark Style                                                                           |
43062 | IDM_SEARCH_MARKONEEXT1                                                  |                                                                   | Using 1st Style                                                                           |
43063 | IDM_SEARCH_MARKONEEXT2                                                  |                                                                   | Using 2nd Style                                                                           |
43064 | IDM_SEARCH_MARKONEEXT3                                                  |                                                                   | Using 3rd Style                                                                           |
43065 | IDM_SEARCH_MARKONEEXT4                                                  |                                                                   | Using 4th Style                                                                           |
43066 | IDM_SEARCH_MARKONEEXT5                                                  |                                                                   | Using 5th Style                                                                           |
44010 | IDM_VIEW_FOLDALL                                                        |                                                                   | Fold All                                                                                  |
44022 | IDM_VIEW_WRAP                                                           |                                                                   | Word wrap                                                                                 |
44029 | IDM_VIEW_UNFOLDALL                                                      |                                                                   | Unfold All                                                                                |
44030 | IDM_VIEW_FOLD_CURRENT                                                   |                                                                   | Fold Current Level                                                                        |
44031 | IDM_VIEW_UNFOLD_CURRENT                                                 |                                                                   | Unfold Current Level                                                                      |
44032 | IDM_VIEW_FULLSCREENTOGGLE                                               |                                                                   | Toggle Full Screen Mode                                                                   |
44034 | IDM_VIEW_ALWAYSONTOP                                                    |                                                                   | Always on Top                                                                             |
44035 | IDM_VIEW_SYNSCROLLV                                                     |                                                                   | Synchronise Vertical Scrolling                                                            |
44036 | IDM_VIEW_SYNSCROLLH                                                     |                                                                   | Synchronise Horizontal Scrolling                                                          |
44051 | IDM_VIEW_FOLD_1                                                         |                                                                   | Fold Level 1                                                                              |
44052 | IDM_VIEW_FOLD_2                                                         |                                                                   | Fold Level 2                                                                              |
44053 | IDM_VIEW_FOLD_3                                                         |                                                                   | Fold Level 3                                                                              |
44054 | IDM_VIEW_FOLD_4                                                         |                                                                   | Fold Level 4                                                                              |
44055 | IDM_VIEW_FOLD_5                                                         |                                                                   | Fold Level 5                                                                              |
44056 | IDM_VIEW_FOLD_6                                                         |                                                                   | Fold Level 6                                                                              |
44057 | IDM_VIEW_FOLD_7                                                         |                                                                   | Fold Level 7                                                                              |
44058 | IDM_VIEW_FOLD_8                                                         |                                                                   | Fold Level 8                                                                              |
44061 | IDM_VIEW_UNFOLD_1                                                       |                                                                   | Unfold Level 1                                                                            |
44062 | IDM_VIEW_UNFOLD_2                                                       |                                                                   | Unfold Level 2                                                                            |
44063 | IDM_VIEW_UNFOLD_3                                                       |                                                                   | Unfold Level 3                                                                            |
44064 | IDM_VIEW_UNFOLD_4                                                       |                                                                   | Unfold Level 4                                                                            |
44065 | IDM_VIEW_UNFOLD_5                                                       |                                                                   | Unfold Level 5                                                                            |
44066 | IDM_VIEW_UNFOLD_6                                                       |                                                                   | Unfold Level 6                                                                            |
44067 | IDM_VIEW_UNFOLD_7                                                       |                                                                   | Unfold Level 7                                                                            |
44068 | IDM_VIEW_UNFOLD_8                                                       |                                                                   | Unfold Level 8                                                                            |
44086 | IDM_VIEW_TAB1                                                           |                                                                   | 1st Tab                                                                                   |
44087 | IDM_VIEW_TAB2                                                           |                                                                   | 2nd Tab                                                                                   |
44088 | IDM_VIEW_TAB3                                                           |                                                                   | 3rd Tab                                                                                   |
44089 | IDM_VIEW_TAB4                                                           |                                                                   | 4th Tab                                                                                   |
44090 | IDM_VIEW_TAB5                                                           |                                                                   | 5th Tab                                                                                   |
44091 | IDM_VIEW_TAB6                                                           |                                                                   | 6th Tab                                                                                   |
44092 | IDM_VIEW_TAB7                                                           |                                                                   | 7th Tab                                                                                   |
44093 | IDM_VIEW_TAB8                                                           |                                                                   | 8th Tab                                                                                   |
44094 | IDM_VIEW_TAB9                                                           |                                                                   | 9th Tab                                                                                   |
44095 | IDM_VIEW_TAB_NEXT                                                       |                                                                   | Next Tab                                                                                  |
44096 | IDM_VIEW_TAB_PREV                                                       |                                                                   | Previous Tab                                                                              |
44098 | IDM_VIEW_TAB_MOVEFORWARD                                                |                                                                   | Move Tab Forward                                                                          |
44099 | IDM_VIEW_TAB_MOVEBACKWARD                                               |                                                                   | Move Tab Backward                                                                         |
44100 | IDM_VIEW_IN_FIREFOX                                                     |                                                                   | View in Firefox                                                                           |
44101 | IDM_VIEW_IN_CHROME                                                      |                                                                   | View in Chrome                                                                            |
44102 | IDM_VIEW_IN_EDGE                                                        |                                                                   | View in Edge                                                                              |
44103 | IDM_VIEW_IN_IE                                                          |                                                                   | View in IE                                                                                |
45001 | IDM_FORMAT_TODOS                                                        |                                                                   | Windows (CR LF)                                                                           |
45002 | IDM_FORMAT_TOUNIX                                                       |                                                                   | Unix (LF)                                                                                 |
45003 | IDM_FORMAT_TOMAC                                                        |                                                                   | Macintosh (CR)                                                                            |
50003 | IDC_PREV_DOC                                                            |                                                                   | Switch to previous document                                                               |
50004 | IDC_NEXT_DOC                                                            |                                                                   | Switch to next document                                                                   |

```

{{< /details >}}

{{< details "show editing actions that should be macro-recordable" >}}
`TODO: remove cmdID and internal constant columns`
`TODO: make a similar table to the one above`
{{< /details >}}



## Play a recorded macro

To play the macro in the buffer, select **Macro > Playback** or press the button.
This will perform the macro once at the current position.


## Save a recorded macro

To save the macro in the buffer, select **Macro > Save current recorded macro...** or
press the toolbar button. A dialog will pop up asking for a name of the macro and the
default key combination. These can later be changed (or deleted) using
**Macro > Modify Shortcut/Delete Macro...**, which brings up the
[**Settings > Shortcut Mapper**](../preferences/#shortcut-mapper) on the **Macros** tab.
When saved, the macro will be available in the bottom section of the **Macro** menu, or
from the pulldown in the dialog accessed from the **Macro > Run a Macro Multiple Times...**
menu entry.

As noted in the [Configuration Files](../config-files) documentation, Notepad++
writes the configuration files (including the macros) when it exits, which means that
after you save your macro, your new macro will _not_ be written to the `shortcuts.xml`
configuration file until Notepad++ exits.  Thus, if you open `shortcuts.xml` after saving
the macro but before exiting Notepad++, you will _not_ be able to see your new macro yet.

## Play a recorded macro multiple times

To play the current macro in the buffer or any saved macro once or multiple
times, select **Macro > Run a Macro Multiple Times...** or press the button.
A dialog will pop up allowing you to select what macro to perform (buffer
macro or any saved macro) and how many times. You can also opt to perform the
macro until the [caret](../editing/#caret-and-cursor "typing/insertion cursor") reaches the end of the current file (starting from
its current position).

Note that if no macros are available, this menu option is greyed out, and
the dialog is inaccessible.


## Edit or delete an existing macro shortcut

To edit or delete an existing macro shortcut, you can use the Shortcut mapper,
which displays all shortcuts of all kinds, and allows changing or removing a key
binding. The interface is also available through the **Macro > Modify
shortcut/Delete macro...** menu entry.

The contents of a macro definition can be edited only in the `shortcuts.xml`
file: there is no built-in interface in Notepad++.  For more information on
the details of how the macros are stored, and the syntax involved, see the
[**Configuration Files Details**: **<Macros>** section](../config-files/#macros).

Some information on the limitations of Macros and possible workarounds can be found in the community page [FAQ: Automating Notepad++](https://community.notepad-plus-plus.org/topic/25400/faq-automating-notepad).

## Macro Security

Starting in v8.9.6.2, the Run menu added extra security-warning that will notify you if the `shortcuts.xml` was modified manually or outside of Notepad++ (if your file was customized when you upgraded from a version before this to this version or later, the notification will also be used the first time you run a saved entry from the Run menu).  In v8.9.7, this protection was extended to also apply to the Macro menu.  You can read more in the [Config Files > shortucts.xml Security](../config-files/#shortcutsxml-security) section; but in brief, open `shortcuts.xml`, verify that your `<UserDefinedCommands>` and `<Macros>` entries look correct, then use **Run > Validate shortcuts.xml** to inform Notepad++ that everything looks reasonable.  (This security step prevents a malicious outside actor from overwriting your `shortcuts.xml` to include a malicious macro or run-menu command, by warning you when there's an unexpected change to the file.)
