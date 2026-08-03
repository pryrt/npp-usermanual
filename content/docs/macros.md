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

| ? | Main Menu Location | Identifier |
|---|--------------------|------------|
| + | File > New | IDM_FILE_NEW |
| - | File > Open... | IDM_FILE_OPEN |
| - | File > Open Containing Folder > Explorer | IDM_FILE_OPEN_FOLDER |
| - | File > Open Containing Folder > cmd | IDM_FILE_OPEN_CMD |
| - | File > Open Containing Folder > PowerShell | IDM_FILE_OPEN_POWERSHELL |
| - | File > Open Containing Folder > Folder as Workspace | IDM_FILE_CONTAININGFOLDERASWORKSPACE |
| - | File > Open in Default Viewer | IDM_FILE_OPEN_DEFAULT_VIEWER |
| - | File > Open Folder as Workspace... | IDM_FILE_OPENFOLDERASWORKSPACE |
| + | File > Reload from Disk | IDM_FILE_RELOAD |
| + | File > Save | IDM_FILE_SAVE |
| - | File > Save As... | IDM_FILE_SAVEAS |
| - | File > Save a Copy As... | IDM_FILE_SAVECOPYAS |
| + | File > Save All | IDM_FILE_SAVEALL |
| - | File > Rename... | IDM_FILE_RENAME |
| + | File > Close | IDM_FILE_CLOSE |
| + | File > Close All | IDM_FILE_CLOSEALL |
| + | File > Close Multiple Documents > Close All but Active Document | IDM_FILE_CLOSEALL_BUT_CURRENT |
| + | File > Close Multiple Documents > Close All but Pinned Documents | IDM_FILE_CLOSEALL_BUT_PINNED |
| + | File > Close Multiple Documents > Close All to the Left | IDM_FILE_CLOSEALL_TOLEFT |
| + | File > Close Multiple Documents > Close All to the Right | IDM_FILE_CLOSEALL_TORIGHT |
| + | File > Close Multiple Documents > Close All Unchanged | IDM_FILE_CLOSEALL_UNCHANGED |
| - | File > Move to Recycle Bin | IDM_FILE_DELETE |
| - | File > Load Session... | IDM_FILE_LOADSESSION |
| - | File > Save Session... | IDM_FILE_SAVESESSION |
| - | File > Print... | IDM_FILE_PRINT |
| - | File > Print Now | IDM_FILE_PRINTNOW |
| - | File > Exit | IDM_FILE_EXIT |
| + | Edit > Undo | IDM_EDIT_UNDO |
| + | Edit > Redo | IDM_EDIT_REDO |
| + | Edit > Cut | IDM_EDIT_CUT |
| + | Edit > Copy | IDM_EDIT_COPY |
| + | Edit > Paste | IDM_EDIT_PASTE |
| + | Edit > Delete | IDM_EDIT_DELETE |
| + | Edit > Select All | IDM_EDIT_SELECTALL |
| + | Edit > Begin/End Select | IDM_EDIT_BEGINENDSELECT |
| + | Edit > Begin/End Select in Column Mode | IDM_EDIT_BEGINENDSELECT_COLUMNMODE |
| + | Edit > Insert > Date Time (short) | IDM_EDIT_INSERT_DATETIME_SHORT |
| + | Edit > Insert > Date Time (long) | IDM_EDIT_INSERT_DATETIME_LONG |
| + | Edit > Insert > Date Time (customized) | IDM_EDIT_INSERT_DATETIME_CUSTOMIZED |
| + | Edit > Copy to Clipboard > Copy Current Full File path | IDM_EDIT_FULLPATHTOCLIP |
| + | Edit > Copy to Clipboard > Copy Current Filename | IDM_EDIT_FILENAMETOCLIP |
| + | Edit > Copy to Clipboard > Copy Current Dir. Path | IDM_EDIT_CURRENTDIRTOCLIP |
| + | Edit > Copy to Clipboard > Copy All Filenames | IDM_EDIT_COPY_ALL_NAMES |
| + | Edit > Copy to Clipboard > Copy All File Paths | IDM_EDIT_COPY_ALL_PATHS |
| + | Edit > Indent > Increase Line Indent | IDM_EDIT_INS_TAB |
| + | Edit > Indent > Decrease Line Indent | IDM_EDIT_RMV_TAB |
| + | Edit > Convert Case to > UPPERCASE | IDM_EDIT_UPPERCASE |
| + | Edit > Convert Case to > lowercase | IDM_EDIT_LOWERCASE |
| + | Edit > Convert Case to > Proper Case | IDM_EDIT_PROPERCASE_FORCE |
| + | Edit > Convert Case to > Proper Case (blend) | IDM_EDIT_PROPERCASE_BLEND |
| + | Edit > Convert Case to > Sentence case | IDM_EDIT_SENTENCECASE_FORCE |
| + | Edit > Convert Case to > Sentence case (blend) | IDM_EDIT_SENTENCECASE_BLEND |
| + | Edit > Convert Case to > iNVERT cASE | IDM_EDIT_INVERTCASE |
| + | Edit > Convert Case to > ranDOm CasE | IDM_EDIT_RANDOMCASE |
| + | Edit > Line Operations > Duplicate Current Line | IDM_EDIT_DUP_LINE |
| + | Edit > Line Operations > Remove Duplicate Lines | IDM_EDIT_REMOVE_ANY_DUP_LINES |
| + | Edit > Line Operations > Remove Consecutive Duplicate Lines | IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES |
| + | Edit > Line Operations > Split Lines | IDM_EDIT_SPLIT_LINES |
| + | Edit > Line Operations > Join Lines | IDM_EDIT_JOIN_LINES |
| + | Edit > Line Operations > Move Up Current Line | IDM_EDIT_LINE_UP |
| + | Edit > Line Operations > Move Down Current Line | IDM_EDIT_LINE_DOWN |
| + | Edit > Line Operations > Remove Empty Lines | IDM_EDIT_REMOVEEMPTYLINES |
| + | Edit > Line Operations > Remove Empty Lines (Containing Blank characters) | IDM_EDIT_REMOVEEMPTYLINESWITHBLANK |
| + | Edit > Line Operations > Insert Blank Line Above Current | IDM_EDIT_BLANKLINEABOVECURRENT |
| + | Edit > Line Operations > Insert Blank Line Below Current | IDM_EDIT_BLANKLINEBELOWCURRENT |
| + | Edit > Line Operations > Reverse Line Order | IDM_EDIT_SORTLINES_REVERSE_ORDER |
| + | Edit > Line Operations > Randomize Line Order | IDM_EDIT_SORTLINES_RANDOMLY |
| + | Edit > Line Operations > Sort Lines Lexicographically Ascending | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING |
| + | Edit > Line Operations > Sort Lines Lex. Ascending Ignoring Case | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING |
| + | Edit > Line Operations > Sort Lines In Locale Order Ascending | IDM_EDIT_SORTLINES_LOCALE_ASCENDING |
| + | Edit > Line Operations > Sort Lines As Integers Ascending | IDM_EDIT_SORTLINES_INTEGER_ASCENDING |
| + | Edit > Line Operations > Sort Lines As Decimals (Comma) Ascending | IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING |
| + | Edit > Line Operations > Sort Lines As Decimals (Dot) Ascending | IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING |
| + | Edit > Line Operations > Sort Lines By Length Ascending | IDM_EDIT_SORTLINES_LENGTH_ASCENDING |
| + | Edit > Line Operations > Sort Lines Lexicographically Descending | IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING |
| + | Edit > Line Operations > Sort Lines Lex. Descending Ignoring Case | IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING |
| + | Edit > Line Operations > Sort Lines In Locale Order Descending | IDM_EDIT_SORTLINES_LOCALE_DESCENDING |
| + | Edit > Line Operations > Sort Lines As Integers Descending | IDM_EDIT_SORTLINES_INTEGER_DESCENDING |
| + | Edit > Line Operations > Sort Lines As Decimals (Comma) Descending | IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING |
| + | Edit > Line Operations > Sort Lines As Decimals (Dot) Descending | IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING |
| + | Edit > Line Operations > Sort Lines By Length Descending | IDM_EDIT_SORTLINES_LENGTH_DESCENDING |
| + | Edit > Comment/Uncomment > Toggle Single Line Comment | IDM_EDIT_BLOCK_COMMENT |
| + | Edit > Comment/Uncomment > Single Line Comment | IDM_EDIT_BLOCK_COMMENT_SET |
| + | Edit > Comment/Uncomment > Single Line Uncomment | IDM_EDIT_BLOCK_UNCOMMENT |
| + | Edit > Comment/Uncomment > Block Comment | IDM_EDIT_STREAM_COMMENT |
| - | Edit > Comment/Uncomment > Block Uncomment | IDM_EDIT_STREAM_UNCOMMENT |
| - | Edit > Auto-Completion > Function Completion | IDM_EDIT_AUTOCOMPLETE |
| - | Edit > Auto-Completion > Word Completion | IDM_EDIT_AUTOCOMPLETE_CURRENTFILE |
| - | Edit > Auto-Completion > Function Parameters Hint | IDM_EDIT_FUNCCALLTIP |
| - | Edit > Auto-Completion > Function Parameters Previous Hint | IDM_EDIT_FUNCCALLTIP_PREVIOUS |
| - | Edit > Auto-Completion > Function Parameters Next Hint | IDM_EDIT_FUNCCALLTIP_NEXT |
| - | Edit > Auto-Completion > Path Completion | IDM_EDIT_AUTOCOMPLETE_PATH |
| + | Edit > EOL Conversion > Windows (CR LF) | IDM_FORMAT_TODOS |
| + | Edit > EOL Conversion > Unix (LF) | IDM_FORMAT_TOUNIX |
| + | Edit > EOL Conversion > Macintosh (CR) | IDM_FORMAT_TOMAC |
| + | Edit > Blank Operations > Trim Trailing Space | IDM_EDIT_TRIMTRAILING |
| + | Edit > Blank Operations > Trim Leading Space | IDM_EDIT_TRIMLINEHEAD |
| + | Edit > Blank Operations > Trim Leading and Trailing Space | IDM_EDIT_TRIM_BOTH |
| + | Edit > Blank Operations > EOL to Space | IDM_EDIT_EOL2WS |
| + | Edit > Blank Operations > Trim both and EOL to Space | IDM_EDIT_TRIMALL |
| + | Edit > Blank Operations > TAB to Space | IDM_EDIT_TAB2SW |
| + | Edit > Blank Operations > Space to TAB (All) | IDM_EDIT_SW2TAB_ALL |
| + | Edit > Blank Operations > Space to TAB (Leading) | IDM_EDIT_SW2TAB_LEADING |
| - | Edit > Paste Special > Paste HTML Content | IDM_EDIT_PASTE_AS_HTML |
| - | Edit > Paste Special > Paste RTF Content | IDM_EDIT_PASTE_AS_RTF |
| - | Edit > Paste Special > Copy Binary Content | IDM_EDIT_COPY_BINARY |
| - | Edit > Paste Special > Cut Binary Content | IDM_EDIT_CUT_BINARY |
| - | Edit > Paste Special > Paste Binary Content | IDM_EDIT_PASTE_BINARY |
| - | Edit > On Selection > Open File | IDM_EDIT_OPENSELECTEDFILETOEDIT |
| - | Edit > On Selection > Open Containing Folder in Explorer | IDM_EDIT_OPENSELECTEDFILEFOLDERINEXPLORER |
| + | Edit > On Selection > Redact Selection █ (Shift: ●) | IDM_EDIT_REDACT_SELECTION |
| - | Edit > On Selection > Search on Internet | IDM_EDIT_SEARCHONINTERNET |
| - | Edit > On Selection > Change Search Engine... | IDM_EDIT_CHANGESEARCHENGINE |
| - | Edit > Multi-select All > Ignore Case  Whole Word | IDM_EDIT_MULTISELECTALL |
| - | Edit > Multi-select All > Match Case Only | IDM_EDIT_MULTISELECTALLMATCHCASE |
| + | Edit > Multi-select All > Match Whole Word Only | IDM_EDIT_MULTISELECTALLWHOLEWORD |
| + | Edit > Multi-select All > Match Case  Whole Word | IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD |
| + | Edit > Multi-select Next > Ignore Case  Whole Word | IDM_EDIT_MULTISELECTNEXT |
| + | Edit > Multi-select Next > Match Case Only | IDM_EDIT_MULTISELECTNEXTMATCHCASE |
| + | Edit > Multi-select Next > Match Whole Word Only | IDM_EDIT_MULTISELECTNEXTWHOLEWORD |
| + | Edit > Multi-select Next > Match Case  Whole Word | IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD |
| + | Edit > Undo the Latest Added Multi-Select | IDM_EDIT_MULTISELECTUNDO |
| + | Edit > Skip Current  Go to Next Multi-select | IDM_EDIT_MULTISELECTSSKIP |
| - | Edit > Column Mode... | IDM_EDIT_COLUMNMODETIP |
| - | Edit > Column Editor... | IDM_EDIT_COLUMNMODE |
| - | Edit > Character Panel | IDM_EDIT_CHAR_PANEL |
| - | Edit > Clipboard History | IDM_EDIT_CLIPBOARDHISTORY_PANEL |
| + | Edit > Read-Only in Notepad++ > Read-Only on Current Document | IDM_EDIT_TOGGLEREADONLY |
| + | Edit > Read-Only in Notepad++ > Read-Only for All Documents | IDM_EDIT_SETREADONLYFORALLDOCS |
| + | Edit > Read-Only in Notepad++ > Clear Read-Only for All Documents | IDM_EDIT_CLEARREADONLYFORALLDOCS |
| + | Edit > Read-Only Attribute in Windows | IDM_EDIT_TOGGLESYSTEMREADONLY |
| - | Search > Find... | IDM_SEARCH_FIND |
| - | Search > Find in Files... | IDM_SEARCH_FINDINFILES |
| + | Search > Find Next | IDM_SEARCH_FINDNEXT |
| + | Search > Find Previous | IDM_SEARCH_FINDPREV |
| + | Search > Select and Find Next | IDM_SEARCH_SETANDFINDNEXT |
| + | Search > Select and Find Previous | IDM_SEARCH_SETANDFINDPREV |
| + | Search > Find (Volatile) Next | IDM_SEARCH_VOLATILE_FINDNEXT |
| + | Search > Find (Volatile) Previous | IDM_SEARCH_VOLATILE_FINDPREV |
| - | Search > Replace... | IDM_SEARCH_REPLACE |
| - | Search > Incremental Search | IDM_SEARCH_FINDINCREMENT |
| - | Search > Search Results Window | IDM_FOCUS_ON_FOUND_RESULTS |
| - | Search > Next Search Result | IDM_SEARCH_GOTONEXTFOUND |
| - | Search > Previous Search Result | IDM_SEARCH_GOTOPREVFOUND |
| - | Search > Go to... | IDM_SEARCH_GOTOLINE |
| + | Search > Go to Matching Brace | IDM_SEARCH_GOTOMATCHINGBRACE |
| + | Search > Select All In-between {} [] or () | IDM_SEARCH_SELECTMATCHINGBRACES |
| - | Search > Mark... | IDM_SEARCH_MARK |
| - | Search > Change History > Go to Next Change | IDM_SEARCH_CHANGED_NEXT |
| - | Search > Change History > Go to Previous Change | IDM_SEARCH_CHANGED_PREV |
| - | Search > Change History > Clear Change History | IDM_SEARCH_CLEAR_CHANGE_HISTORY |
| + | Search > Style All Occurrences of Token > Using 1st Style | IDM_SEARCH_MARKALLEXT1 |
| + | Search > Style All Occurrences of Token > Using 2nd Style | IDM_SEARCH_MARKALLEXT2 |
| + | Search > Style All Occurrences of Token > Using 3rd Style | IDM_SEARCH_MARKALLEXT3 |
| + | Search > Style All Occurrences of Token > Using 4th Style | IDM_SEARCH_MARKALLEXT4 |
| + | Search > Style All Occurrences of Token > Using 5th Style | IDM_SEARCH_MARKALLEXT5 |
| + | Search > Style One Token > Using 1st Style | IDM_SEARCH_MARKONEEXT1 |
| + | Search > Style One Token > Using 2nd Style | IDM_SEARCH_MARKONEEXT2 |
| + | Search > Style One Token > Using 3rd Style | IDM_SEARCH_MARKONEEXT3 |
| + | Search > Style One Token > Using 4th Style | IDM_SEARCH_MARKONEEXT4 |
| + | Search > Style One Token > Using 5th Style | IDM_SEARCH_MARKONEEXT5 |
| + | Search > Clear Style > Clear 1st Style | IDM_SEARCH_UNMARKALLEXT1 |
| + | Search > Clear Style > Clear 2nd Style | IDM_SEARCH_UNMARKALLEXT2 |
| + | Search > Clear Style > Clear 3rd Style | IDM_SEARCH_UNMARKALLEXT3 |
| + | Search > Clear Style > Clear 4th Style | IDM_SEARCH_UNMARKALLEXT4 |
| + | Search > Clear Style > Clear 5th Style | IDM_SEARCH_UNMARKALLEXT5 |
| + | Search > Clear Style > Clear all Styles | IDM_SEARCH_CLEARALLMARKS |
| + | Search > Jump Up > 1st Style | IDM_SEARCH_GOPREVMARKER1 |
| + | Search > Jump Up > 2nd Style | IDM_SEARCH_GOPREVMARKER2 |
| + | Search > Jump Up > 3rd Style | IDM_SEARCH_GOPREVMARKER3 |
| + | Search > Jump Up > 4th Style | IDM_SEARCH_GOPREVMARKER4 |
| + | Search > Jump Up > 5th Style | IDM_SEARCH_GOPREVMARKER5 |
| + | Search > Jump Up > Find Mark Style | IDM_SEARCH_GOPREVMARKER_DEF |
| + | Search > Jump Down > 1st Style | IDM_SEARCH_GONEXTMARKER1 |
| + | Search > Jump Down > 2nd Style | IDM_SEARCH_GONEXTMARKER2 |
| + | Search > Jump Down > 3rd Style | IDM_SEARCH_GONEXTMARKER3 |
| + | Search > Jump Down > 4th Style | IDM_SEARCH_GONEXTMARKER4 |
| + | Search > Jump Down > 5th Style | IDM_SEARCH_GONEXTMARKER5 |
| + | Search > Jump Down > Find Mark Style | IDM_SEARCH_GONEXTMARKER_DEF |
| + | Search > Copy Styled Text > 1st Style | IDM_SEARCH_STYLE1TOCLIP |
| + | Search > Copy Styled Text > 2nd Style | IDM_SEARCH_STYLE2TOCLIP |
| + | Search > Copy Styled Text > 3rd Style | IDM_SEARCH_STYLE3TOCLIP |
| + | Search > Copy Styled Text > 4th Style | IDM_SEARCH_STYLE4TOCLIP |
| + | Search > Copy Styled Text > 5th Style | IDM_SEARCH_STYLE5TOCLIP |
| + | Search > Copy Styled Text > All Styles | IDM_SEARCH_ALLSTYLESTOCLIP |
| + | Search > Copy Styled Text > Find Mark Style | IDM_SEARCH_MARKEDTOCLIP |
| + | Search > Bookmark > Toggle Bookmark | IDM_SEARCH_TOGGLE_BOOKMARK |
| + | Search > Bookmark > Next Bookmark | IDM_SEARCH_NEXT_BOOKMARK |
| + | Search > Bookmark > Previous Bookmark | IDM_SEARCH_PREV_BOOKMARK |
| + | Search > Bookmark > Clear All Bookmarks | IDM_SEARCH_CLEAR_BOOKMARKS |
| + | Search > Bookmark > Cut Bookmarked Lines | IDM_SEARCH_CUTMARKEDLINES |
| + | Search > Bookmark > Copy Bookmarked Lines | IDM_SEARCH_COPYMARKEDLINES |
| + | Search > Bookmark > Paste to (Replace) Bookmarked Lines | IDM_SEARCH_PASTEMARKEDLINES |
| + | Search > Bookmark > Remove Bookmarked Lines | IDM_SEARCH_DELETEMARKEDLINES |
| + | Search > Bookmark > Remove Non-Bookmarked Lines | IDM_SEARCH_DELETEUNMARKEDLINES |
| + | Search > Bookmark > Inverse Bookmarks | IDM_SEARCH_INVERSEMARKS |
| - | Search > Find characters in range... | IDM_SEARCH_FINDCHARINRANGE |
| + | View > Always on Top | IDM_VIEW_ALWAYSONTOP |
| + | View > Toggle Full Screen Mode | IDM_VIEW_FULLSCREENTOGGLE |
| - | View > Post-It | IDM_VIEW_POSTIT |
| - | View > Distraction Free Mode | IDM_VIEW_DISTRACTIONFREE |
| + | View > View Current File in > Firefox | IDM_VIEW_IN_FIREFOX |
| + | View > View Current File in > Chrome | IDM_VIEW_IN_CHROME |
| + | View > View Current File in > Edge | IDM_VIEW_IN_EDGE |
| + | View > View Current File in > IE | IDM_VIEW_IN_IE |
| - | View > Show Symbol > Show Space and Tab | IDM_VIEW_TAB_SPACE |
| - | View > Show Symbol > Show End of Line | IDM_VIEW_EOL |
| - | View > Show Symbol > Show Non-Printing Characters | IDM_VIEW_NPC |
| - | View > Show Symbol > Show Control Characters  Unicode EOL | IDM_VIEW_NPC_CCUNIEOL |
| - | View > Show Symbol > Show All Characters | IDM_VIEW_ALL_CHARACTERS |
| - | View > Show Symbol > Show Indent Guide | IDM_VIEW_INDENT_GUIDE |
| - | View > Show Symbol > Show Wrap Symbol | IDM_VIEW_WRAP_SYMBOL |
| - | View > Zoom > Zoom In (Ctrl+Mouse Wheel Up) | IDM_VIEW_ZOOMIN |
| - | View > Zoom > Zoom Out (Ctrl+Mouse Wheel Down) | IDM_VIEW_ZOOMOUT |
| - | View > Zoom > Restore Default Zoom | IDM_VIEW_ZOOMRESTORE |
| - | View > Zoom > Synchronize Across Views | IDM_VIEW_ZOOM_SYNC |
| + | View > Move/Clone Current Document > Move to Other View | IDM_VIEW_GOTO_ANOTHER_VIEW |
| + | View > Move/Clone Current Document > Clone to Other View | IDM_VIEW_CLONE_TO_ANOTHER_VIEW |
| + | View > Move/Clone Current Document > Move to New Instance | IDM_VIEW_GOTO_NEW_INSTANCE |
| + | View > Move/Clone Current Document > Open in New Instance | IDM_VIEW_LOAD_IN_NEW_INSTANCE |
| + | View > Tab > 1st Tab | IDM_VIEW_TAB1 |
| + | View > Tab > 2nd Tab | IDM_VIEW_TAB2 |
| + | View > Tab > 3rd Tab | IDM_VIEW_TAB3 |
| + | View > Tab > 4th Tab | IDM_VIEW_TAB4 |
| + | View > Tab > 5th Tab | IDM_VIEW_TAB5 |
| + | View > Tab > 6th Tab | IDM_VIEW_TAB6 |
| + | View > Tab > 7th Tab | IDM_VIEW_TAB7 |
| + | View > Tab > 8th Tab | IDM_VIEW_TAB8 |
| + | View > Tab > 9th Tab | IDM_VIEW_TAB9 |
| - | View > Tab > First Tab | IDM_VIEW_TAB_START |
| - | View > Tab > Last Tab | IDM_VIEW_TAB_END |
| + | View > Tab > Next Tab | IDM_VIEW_TAB_NEXT |
| + | View > Tab > Previous Tab | IDM_VIEW_TAB_PREV |
| + | View > Tab > Move to Start | IDM_VIEW_GOTO_START |
| + | View > Tab > Move to End | IDM_VIEW_GOTO_END |
| + | View > Tab > Move Tab Forward | IDM_VIEW_TAB_MOVEFORWARD |
| + | View > Tab > Move Tab Backward | IDM_VIEW_TAB_MOVEBACKWARD |
| - | View > Tab > Apply Color 1 | IDM_VIEW_TAB_COLOUR_1 |
| - | View > Tab > Apply Color 2 | IDM_VIEW_TAB_COLOUR_2 |
| - | View > Tab > Apply Color 3 | IDM_VIEW_TAB_COLOUR_3 |
| - | View > Tab > Apply Color 4 | IDM_VIEW_TAB_COLOUR_4 |
| - | View > Tab > Apply Color 5 | IDM_VIEW_TAB_COLOUR_5 |
| - | View > Tab > Remove Color | IDM_VIEW_TAB_COLOUR_NONE |
| + | View > Word wrap | IDM_VIEW_WRAP |
| - | View > Focus on Another View | IDM_VIEW_SWITCHTO_OTHER_VIEW |
| - | View > Hide Lines | IDM_VIEW_HIDELINES |
| + | View > Fold All | IDM_VIEW_FOLDALL |
| + | View > Unfold All | IDM_VIEW_UNFOLDALL |
| + | View > Fold Current Level | IDM_VIEW_FOLD_CURRENT |
| + | View > Unfold Current Level | IDM_VIEW_UNFOLD_CURRENT |
| + | View > Fold Level > 1 | IDM_VIEW_FOLD_1 |
| + | View > Fold Level > 2 | IDM_VIEW_FOLD_2 |
| + | View > Fold Level > 3 | IDM_VIEW_FOLD_3 |
| + | View > Fold Level > 4 | IDM_VIEW_FOLD_4 |
| + | View > Fold Level > 5 | IDM_VIEW_FOLD_5 |
| + | View > Fold Level > 6 | IDM_VIEW_FOLD_6 |
| + | View > Fold Level > 7 | IDM_VIEW_FOLD_7 |
| + | View > Fold Level > 8 | IDM_VIEW_FOLD_8 |
| + | View > Unfold Level > 1 | IDM_VIEW_UNFOLD_1 |
| + | View > Unfold Level > 2 | IDM_VIEW_UNFOLD_2 |
| + | View > Unfold Level > 3 | IDM_VIEW_UNFOLD_3 |
| + | View > Unfold Level > 4 | IDM_VIEW_UNFOLD_4 |
| + | View > Unfold Level > 5 | IDM_VIEW_UNFOLD_5 |
| + | View > Unfold Level > 6 | IDM_VIEW_UNFOLD_6 |
| + | View > Unfold Level > 7 | IDM_VIEW_UNFOLD_7 |
| + | View > Unfold Level > 8 | IDM_VIEW_UNFOLD_8 |
| - | View > Summary... | IDM_VIEW_SUMMARY |
| - | View > Project Panels > Project Panel 1 | IDM_VIEW_PROJECT_PANEL_1 |
| - | View > Project Panels > Project Panel 2 | IDM_VIEW_PROJECT_PANEL_2 |
| - | View > Project Panels > Project Panel 3 | IDM_VIEW_PROJECT_PANEL_3 |
| - | View > Folder as Workspace | IDM_VIEW_FILEBROWSER |
| - | View > Document Map | IDM_VIEW_DOC_MAP |
| - | View > Document List | IDM_VIEW_DOCLIST |
| - | View > Function List | IDM_VIEW_FUNC_LIST |
| + | View > Synchronize Vertical Scrolling | IDM_VIEW_SYNSCROLLV |
| + | View > Synchronize Horizontal Scrolling | IDM_VIEW_SYNSCROLLH |
| + | View > Text Direction RTL | IDM_EDIT_RTL |
| + | View > Text Direction LTR | IDM_EDIT_LTR |
| - | View > Monitoring (tail -f) | IDM_VIEW_MONITORING |
| - | Encoding > ANSI | IDM_FORMAT_ANSI |
| - | Encoding > UTF-8 | IDM_FORMAT_AS_UTF_8 |
| - | Encoding > UTF-8-BOM | IDM_FORMAT_UTF_8 |
| - | Encoding > UTF-16 BE BOM | IDM_FORMAT_UTF_16BE |
| - | Encoding > UTF-16 LE BOM | IDM_FORMAT_UTF_16LE |
| - | Encoding > Character sets > Arabic > ISO 8859-6 | IDM_FORMAT_ISO_8859_6 |
| - | Encoding > Character sets > Arabic > OEM 720 | IDM_FORMAT_DOS_720 |
| - | Encoding > Character sets > Arabic > Windows-1256 | IDM_FORMAT_WIN_1256 |
| - | Encoding > Character sets > Baltic > ISO 8859-4 | IDM_FORMAT_ISO_8859_4 |
| - | Encoding > Character sets > Baltic > ISO 8859-13 | IDM_FORMAT_ISO_8859_13 |
| - | Encoding > Character sets > Baltic > OEM 775 | IDM_FORMAT_DOS_775 |
| - | Encoding > Character sets > Baltic > Windows-1257 | IDM_FORMAT_WIN_1257 |
| - | Encoding > Character sets > Celtic > ISO 8859-14 | IDM_FORMAT_ISO_8859_14 |
| - | Encoding > Character sets > Cyrillic > ISO 8859-5 | IDM_FORMAT_ISO_8859_5 |
| - | Encoding > Character sets > Cyrillic > KOI8-R | IDM_FORMAT_KOI8R_CYRILLIC |
| - | Encoding > Character sets > Cyrillic > KOI8-U | IDM_FORMAT_KOI8U_CYRILLIC |
| - | Encoding > Character sets > Cyrillic > Macintosh | IDM_FORMAT_MAC_CYRILLIC |
| - | Encoding > Character sets > Cyrillic > OEM 855 | IDM_FORMAT_DOS_855 |
| - | Encoding > Character sets > Cyrillic > OEM 866 | IDM_FORMAT_DOS_866 |
| - | Encoding > Character sets > Cyrillic > Windows-1251 | IDM_FORMAT_WIN_1251 |
| - | Encoding > Character sets > Central European > OEM 852 | IDM_FORMAT_DOS_852 |
| - | Encoding > Character sets > Central European > Windows-1250 | IDM_FORMAT_WIN_1250 |
| - | Encoding > Character sets > Chinese > Big5 (Traditional) | IDM_FORMAT_BIG5 |
| - | Encoding > Character sets > Chinese > GB2312 (Simplified) | IDM_FORMAT_GB2312 |
| - | Encoding > Character sets > Eastern European > ISO 8859-2 | IDM_FORMAT_ISO_8859_2 |
| - | Encoding > Character sets > Greek > ISO 8859-7 | IDM_FORMAT_ISO_8859_7 |
| - | Encoding > Character sets > Greek > OEM 737 | IDM_FORMAT_DOS_737 |
| - | Encoding > Character sets > Greek > OEM 869 | IDM_FORMAT_DOS_869 |
| - | Encoding > Character sets > Greek > Windows-1253 | IDM_FORMAT_WIN_1253 |
| - | Encoding > Character sets > Hebrew > ISO 8859-8 | IDM_FORMAT_ISO_8859_8 |
| - | Encoding > Character sets > Hebrew > OEM 862 | IDM_FORMAT_DOS_862 |
| - | Encoding > Character sets > Hebrew > Windows-1255 | IDM_FORMAT_WIN_1255 |
| - | Encoding > Character sets > Japanese > Shift-JIS | IDM_FORMAT_SHIFT_JIS |
| - | Encoding > Character sets > Korean > Windows 949 | IDM_FORMAT_KOREAN_WIN |
| - | Encoding > Character sets > Korean > EUC-KR | IDM_FORMAT_EUC_KR |
| - | Encoding > Character sets > North European > OEM 861 : Icelandic | IDM_FORMAT_DOS_861 |
| - | Encoding > Character sets > North European > OEM 865 : Nordic | IDM_FORMAT_DOS_865 |
| - | Encoding > Character sets > Thai > TIS-620 | IDM_FORMAT_TIS_620 |
| - | Encoding > Character sets > Turkish > ISO 8859-3 | IDM_FORMAT_ISO_8859_3 |
| - | Encoding > Character sets > Turkish > ISO 8859-9 | IDM_FORMAT_ISO_8859_9 |
| - | Encoding > Character sets > Turkish > OEM 857 | IDM_FORMAT_DOS_857 |
| - | Encoding > Character sets > Turkish > Windows-1254 | IDM_FORMAT_WIN_1254 |
| - | Encoding > Character sets > Western European > ISO 8859-1 | IDM_FORMAT_ISO_8859_1 |
| - | Encoding > Character sets > Western European > ISO 8859-10 | IDM_FORMAT_ISO_8859_10 |
| - | Encoding > Character sets > Western European > ISO 8859-15 | IDM_FORMAT_ISO_8859_15 |
| - | Encoding > Character sets > Western European > OEM 850 | IDM_FORMAT_DOS_850 |
| - | Encoding > Character sets > Western European > OEM 858 | IDM_FORMAT_DOS_858 |
| - | Encoding > Character sets > Western European > OEM 860 : Portuguese | IDM_FORMAT_DOS_860 |
| - | Encoding > Character sets > Western European > OEM 863 : French | IDM_FORMAT_DOS_863 |
| - | Encoding > Character sets > Western European > OEM-US | IDM_FORMAT_DOS_437 |
| - | Encoding > Character sets > Western European > Windows-1252 | IDM_FORMAT_WIN_1252 |
| - | Encoding > Character sets > Vietnamese > Windows-1258 | IDM_FORMAT_WIN_1258 |
| - | Encoding > Convert to ANSI | IDM_FORMAT_CONV2_ANSI |
| - | Encoding > Convert to UTF-8 | IDM_FORMAT_CONV2_AS_UTF_8 |
| - | Encoding > Convert to UTF-8-BOM | IDM_FORMAT_CONV2_UTF_8 |
| - | Encoding > Convert to UTF-16 BE BOM | IDM_FORMAT_CONV2_UTF_16BE |
| - | Encoding > Convert to UTF-16 LE BOM | IDM_FORMAT_CONV2_UTF_16LE |
| - | Language > None (Normal Text) | IDM_LANG_TEXT |
| - | Language > ActionScript | IDM_LANG_FLASH |
| - | Language > Ada | IDM_LANG_ADA |
| - | Language > ASN.1 | IDM_LANG_ASN1 |
| - | Language > ASP | IDM_LANG_ASP |
| - | Language > Assembly | IDM_LANG_ASM |
| - | Language > AutoIt | IDM_LANG_AU3 |
| - | Language > AviSynth | IDM_LANG_AVS |
| - | Language > BaanC | IDM_LANG_BAANC |
| - | Language > Batch | IDM_LANG_BATCH |
| - | Language > Blitzbasic | IDM_LANG_BLITZBASIC |
| - | Language > C | IDM_LANG_C |
| - | Language > C# | IDM_LANG_CS |
| - | Language > C++ | IDM_LANG_CPP |
| - | Language > Caml | IDM_LANG_CAML |
| - | Language > CMake | IDM_LANG_CMAKE |
| - | Language > COBOL | IDM_LANG_COBOL |
| - | Language > CSound | IDM_LANG_CSOUND |
| - | Language > CoffeeScript | IDM_LANG_COFFEESCRIPT |
| - | Language > CSS | IDM_LANG_CSS |
| - | Language > D | IDM_LANG_D |
| - | Language > Diff | IDM_LANG_DIFF |
| - | Language > Erlang | IDM_LANG_ERLANG |
| - | Language > ErrorList | IDM_LANG_ERRORLIST |
| - | Language > Escape Sequence (ANSI) | IDM_LANG_ESCSEQ |
| - | Language > ESCRIPT | IDM_LANG_ESCRIPT |
| - | Language > Forth | IDM_LANG_FORTH |
| - | Language > Fortran (free form) | IDM_LANG_FORTRAN |
| - | Language > Fortran (fixed form) | IDM_LANG_FORTRAN_77 |
| - | Language > Freebasic | IDM_LANG_FREEBASIC |
| - | Language > GDScript | IDM_LANG_GDSCRIPT |
| - | Language > Go | IDM_LANG_GOLANG |
| - | Language > Gui4Cli | IDM_LANG_GUI4CLI |
| - | Language > Haskell | IDM_LANG_HASKELL |
| - | Language > Hollywood | IDM_LANG_HOLLYWOOD |
| - | Language > HTML | IDM_LANG_HTML |
| - | Language > INI file | IDM_LANG_INI |
| - | Language > Inno Setup | IDM_LANG_INNO |
| - | Language > Intel HEX | IDM_LANG_IHEX |
| - | Language > Java | IDM_LANG_JAVA |
| - | Language > JavaScript | IDM_LANG_JS |
| - | Language > JSON | IDM_LANG_JSON |
| - | Language > JSON5 | IDM_LANG_JSON5 |
| - | Language > JSP | IDM_LANG_JSP |
| - | Language > KIXtart | IDM_LANG_KIX |
| - | Language > LISP | IDM_LANG_LISP |
| - | Language > LaTeX | IDM_LANG_LATEX |
| - | Language > Lua | IDM_LANG_LUA |
| - | Language > Makefile | IDM_LANG_MAKEFILE |
| - | Language > Matlab | IDM_LANG_MATLAB |
| - | Language > Microsoft Transact-SQL | IDM_LANG_MSSQL |
| - | Language > MMIXAL | IDM_LANG_MMIXAL |
| - | Language > MS-DOS Style | IDM_LANG_ASCII |
| - | Language > Nim | IDM_LANG_NIM |
| - | Language > Nncrontab | IDM_LANG_NNCRONTAB |
| - | Language > NSIS | IDM_LANG_NSIS |
| - | Language > Objective-C | IDM_LANG_OBJC |
| - | Language > OScript | IDM_LANG_OSCRIPT |
| - | Language > Pascal | IDM_LANG_PASCAL |
| - | Language > Perl | IDM_LANG_PERL |
| - | Language > PHP | IDM_LANG_PHP |
| - | Language > PostScript | IDM_LANG_PS |
| - | Language > PowerShell | IDM_LANG_POWERSHELL |
| - | Language > Properties | IDM_LANG_PROPS |
| - | Language > Purebasic | IDM_LANG_PUREBASIC |
| - | Language > Python | IDM_LANG_PYTHON |
| - | Language > R | IDM_LANG_R |
| - | Language > Raku | IDM_LANG_RAKU |
| - | Language > REBOL | IDM_LANG_REBOL |
| - | Language > Registry | IDM_LANG_REGISTRY |
| - | Language > Resource file | IDM_LANG_RC |
| - | Language > Ruby | IDM_LANG_RUBY |
| - | Language > Rust | IDM_LANG_RUST |
| - | Language > SAS | IDM_LANG_SAS |
| - | Language > Shell | IDM_LANG_BASH |
| - | Language > Scheme | IDM_LANG_SCHEME |
| - | Language > Smalltalk | IDM_LANG_SMALLTALK |
| - | Language > Spice | IDM_LANG_SPICE |
| - | Language > SQL | IDM_LANG_SQL |
| - | Language > Swift | IDM_LANG_SWIFT |
| - | Language > S-Record | IDM_LANG_SREC |
| - | Language > TCL | IDM_LANG_TCL |
| - | Language > Tektronix extended HEX | IDM_LANG_TEHEX |
| - | Language > TeX | IDM_LANG_TEX |
| - | Language > TOML | IDM_LANG_TOML |
| - | Language > txt2tags | IDM_LANG_TXT2TAGS |
| - | Language > TypeScript | IDM_LANG_TYPESCRIPT |
| - | Language > Verilog | IDM_LANG_VERILOG |
| - | Language > VHDL | IDM_LANG_VHDL |
| - | Language > Visual Basic | IDM_LANG_VB |
| - | Language > Visual Prolog | IDM_LANG_VISUALPROLOG |
| - | Language > XML | IDM_LANG_XML |
| - | Language > YAML | IDM_LANG_YAML |
| - | Language > Define your language... | IDM_LANG_USER_DLG |
| - | Language > Open User Defined Language folder... | IDM_LANG_OPENUDLDIR |
| - | Language > Notepad++ User Defined Languages Collection | IDM_LANG_UDLCOLLECTION_PROJECT_SITE |
| - | Language > User-Defined | IDM_LANG_USER |
| - | Language > None (Normal Text) | IDM_LANG_TEXT |
| - | Language > A > ActionScript | IDM_LANG_FLASH |
| - | Language > A > Ada | IDM_LANG_ADA |
| - | Language > A > ASN.1 | IDM_LANG_ASN1 |
| - | Language > A > ASP | IDM_LANG_ASP |
| - | Language > A > Assembly | IDM_LANG_ASM |
| - | Language > A > AutoIt | IDM_LANG_AU3 |
| - | Language > A > AviSynth | IDM_LANG_AVS |
| - | Language > B > BaanC | IDM_LANG_BAANC |
| - | Language > B > Batch | IDM_LANG_BATCH |
| - | Language > B > Blitzbasic | IDM_LANG_BLITZBASIC |
| - | Language > C > C | IDM_LANG_C |
| - | Language > C > C# | IDM_LANG_CS |
| - | Language > C > C++ | IDM_LANG_CPP |
| - | Language > C > Caml | IDM_LANG_CAML |
| - | Language > C > CMake | IDM_LANG_CMAKE |
| - | Language > C > COBOL | IDM_LANG_COBOL |
| - | Language > C > CSound | IDM_LANG_CSOUND |
| - | Language > C > CoffeeScript | IDM_LANG_COFFEESCRIPT |
| - | Language > C > CSS | IDM_LANG_CSS |
| - | Language > D > D | IDM_LANG_D |
| - | Language > D > Diff | IDM_LANG_DIFF |
| - | Language > E > Erlang | IDM_LANG_ERLANG |
| - | Language > E > ErrorList | IDM_LANG_ERRORLIST |
| - | Language > E > Escape Sequence (ANSI) | IDM_LANG_ESCSEQ |
| - | Language > E > ESCRIPT | IDM_LANG_ESCRIPT |
| - | Language > F > Forth | IDM_LANG_FORTH |
| - | Language > F > Fortran (free form) | IDM_LANG_FORTRAN |
| - | Language > F > Fortran (fixed form) | IDM_LANG_FORTRAN_77 |
| - | Language > F > Freebasic | IDM_LANG_FREEBASIC |
| - | Language > G > GDScript | IDM_LANG_GDSCRIPT |
| - | Language > G > Go | IDM_LANG_GOLANG |
| - | Language > G > Gui4Cli | IDM_LANG_GUI4CLI |
| - | Language > H > Haskell | IDM_LANG_HASKELL |
| - | Language > H > Hollywood | IDM_LANG_HOLLYWOOD |
| - | Language > H > HTML | IDM_LANG_HTML |
| - | Language > I > INI file | IDM_LANG_INI |
| - | Language > I > Inno Setup | IDM_LANG_INNO |
| - | Language > I > Intel HEX | IDM_LANG_IHEX |
| - | Language > J > Java | IDM_LANG_JAVA |
| - | Language > J > JavaScript | IDM_LANG_JS |
| - | Language > J > JSON | IDM_LANG_JSON |
| - | Language > J > JSON5 | IDM_LANG_JSON5 |
| - | Language > J > JSP | IDM_LANG_JSP |
| - | Language > KIXtart | IDM_LANG_KIX |
| - | Language > L > LaTeX | IDM_LANG_LATEX |
| - | Language > L > LISP | IDM_LANG_LISP |
| - | Language > L > Lua | IDM_LANG_LUA |
| - | Language > M > Makefile | IDM_LANG_MAKEFILE |
| - | Language > M > Matlab | IDM_LANG_MATLAB |
| - | Language > M > Microsoft Transact-SQL | IDM_LANG_MSSQL |
| - | Language > M > MMIXAL | IDM_LANG_MMIXAL |
| - | Language > M > MS-DOS Style | IDM_LANG_ASCII |
| - | Language > N > Nim | IDM_LANG_NIM |
| - | Language > N > Nncrontab | IDM_LANG_NNCRONTAB |
| - | Language > N > NSIS | IDM_LANG_NSIS |
| - | Language > O > Objective-C | IDM_LANG_OBJC |
| - | Language > O > OScript | IDM_LANG_OSCRIPT |
| - | Language > P > Pascal | IDM_LANG_PASCAL |
| - | Language > P > Perl | IDM_LANG_PERL |
| - | Language > P > PHP | IDM_LANG_PHP |
| - | Language > P > PostScript | IDM_LANG_PS |
| - | Language > P > PowerShell | IDM_LANG_POWERSHELL |
| - | Language > P > Properties | IDM_LANG_PROPS |
| - | Language > P > Purebasic | IDM_LANG_PUREBASIC |
| - | Language > P > Python | IDM_LANG_PYTHON |
| - | Language > R > R | IDM_LANG_R |
| - | Language > R > Raku | IDM_LANG_RAKU |
| - | Language > R > REBOL | IDM_LANG_REBOL |
| - | Language > R > Registry | IDM_LANG_REGISTRY |
| - | Language > R > Resource file | IDM_LANG_RC |
| - | Language > R > Ruby | IDM_LANG_RUBY |
| - | Language > R > Rust | IDM_LANG_RUST |
| - | Language > S > SAS | IDM_LANG_SAS |
| - | Language > S > Shell | IDM_LANG_BASH |
| - | Language > S > Scheme | IDM_LANG_SCHEME |
| - | Language > S > Smalltalk | IDM_LANG_SMALLTALK |
| - | Language > S > Spice | IDM_LANG_SPICE |
| - | Language > S > SQL | IDM_LANG_SQL |
| - | Language > S > Swift | IDM_LANG_SWIFT |
| - | Language > S > S-Record | IDM_LANG_SREC |
| - | Language > T > TCL | IDM_LANG_TCL |
| - | Language > T > Tektronix extended HEX | IDM_LANG_TEHEX |
| - | Language > T > TeX | IDM_LANG_TEX |
| - | Language > T > TOML | IDM_LANG_TOML |
| - | Language > T > txt2tags | IDM_LANG_TXT2TAGS |
| - | Language > T > TypeScript | IDM_LANG_TYPESCRIPT |
| - | Language > V > Visual Basic | IDM_LANG_VB |
| - | Language > V > Visual Prolog | IDM_LANG_VISUALPROLOG |
| - | Language > V > VHDL | IDM_LANG_VHDL |
| - | Language > V > Verilog | IDM_LANG_VERILOG |
| - | Language > XML | IDM_LANG_XML |
| - | Language > YAML | IDM_LANG_YAML |
| - | Language > User Defined Language > Define your language... | IDM_LANG_USER_DLG |
| - | Language > User Defined Language > Open User Defined Language folder... | IDM_LANG_OPENUDLDIR |
| - | Language > User Defined Language > Notepad++ User Defined Languages Collection | IDM_LANG_UDLCOLLECTION_PROJECT_SITE |
| - | Language > User-Defined | IDM_LANG_USER |
| - | Settings > Preferences... | IDM_SETTING_PREFERENCE |
| - | Settings > Style Configurator... | IDM_LANGSTYLE_CONFIG_DLG |
| - | Settings > Shortcut Mapper... | IDM_SETTING_SHORTCUT_MAPPER |
| - | Settings > Import > Import plugin(s)... | IDM_SETTING_IMPORTPLUGIN |
| - | Settings > Import > Import style theme(s)... | IDM_SETTING_IMPORTSTYLETHEMES |
| - | Settings > Edit Popup ContextMenu | IDM_SETTING_EDITCONTEXTMENU |
| - | Tools > MD5 > Generate... | IDM_TOOL_MD5_GENERATE |
| - | Tools > MD5 > Generate from files... | IDM_TOOL_MD5_GENERATEFROMFILE |
| - | Tools > MD5 > Generate from selection into clipboard | IDM_TOOL_MD5_GENERATEINTOCLIPBOARD |
| - | Tools > SHA-1 > Generate... | IDM_TOOL_SHA1_GENERATE |
| - | Tools > SHA-1 > Generate from files... | IDM_TOOL_SHA1_GENERATEFROMFILE |
| - | Tools > SHA-1 > Generate from selection into clipboard | IDM_TOOL_SHA1_GENERATEINTOCLIPBOARD |
| - | Tools > SHA-256 > Generate... | IDM_TOOL_SHA256_GENERATE |
| - | Tools > SHA-256 > Generate from files... | IDM_TOOL_SHA256_GENERATEFROMFILE |
| - | Tools > SHA-256 > Generate from selection into clipboard | IDM_TOOL_SHA256_GENERATEINTOCLIPBOARD |
| - | Tools > SHA-512 > Generate... | IDM_TOOL_SHA512_GENERATE |
| - | Tools > SHA-512 > Generate from files... | IDM_TOOL_SHA512_GENERATEFROMFILE |
| - | Tools > SHA-512 > Generate from selection into clipboard | IDM_TOOL_SHA512_GENERATEINTOCLIPBOARD |
| - | Macro > Start Recording | IDM_MACRO_STARTRECORDINGMACRO |
| - | Macro > Stop Recording | IDM_MACRO_STOPRECORDINGMACRO |
| - | Macro > Playback | IDM_MACRO_PLAYBACKRECORDEDMACRO |
| - | Macro > Save Current Recorded Macro... | IDM_MACRO_SAVECURRENTMACRO |
| - | Macro > Run a Macro Multiple Times... | IDM_MACRO_RUNMULTIMACRODLG |
| - | Run > Run... | IDM_EXECUTE |
| - | Run > Validate shortcuts.xml | IDM_EXECUTE_VALIDATE_SHORTCUTSXML |
| - | Plugins > Open Plugins Folder... | IDM_SETTING_OPENPLUGINSDIR |
| - | Window > Sort By > Name A to Z | IDM_WINDOW_SORT_FN_ASC |
| - | Window > Sort By > Name Z to A | IDM_WINDOW_SORT_FN_DSC |
| - | Window > Sort By > Path A to Z | IDM_WINDOW_SORT_FP_ASC |
| - | Window > Sort By > Path Z to A | IDM_WINDOW_SORT_FP_DSC |
| - | Window > Sort By > Type A to Z | IDM_WINDOW_SORT_FT_ASC |
| - | Window > Sort By > Type Z to A | IDM_WINDOW_SORT_FT_DSC |
| - | Window > Sort By > Content Length Ascending | IDM_WINDOW_SORT_FS_ASC |
| - | Window > Sort By > Content Length Descending | IDM_WINDOW_SORT_FS_DSC |
| - | Window > Sort By > Modified Time Ascending | IDM_WINDOW_SORT_FD_ASC |
| - | Window > Sort By > Modified Time Descending | IDM_WINDOW_SORT_FD_DSC |
| - | Window > Windows... | IDM_WINDOW_WINDOWS |
| - | Window > Recent Window | IDM_WINDOW_MRU_FIRST |
| - | ? > Command Line Arguments... | IDM_CMDLINEARGUMENTS |
| - | ? > Notepad++ Home | IDM_HOMESWEETHOME |
| - | ? > Notepad++ Project Page | IDM_PROJECTPAGE |
| - | ? > Notepad++ Online User Manual | IDM_ONLINEDOCUMENT |
| - | ? > Notepad++ Community (Forum) | IDM_FORUM |
| - | ? > Update Notepad++ | IDM_UPDATE_NPP |
| - | ? > Set Updater Proxy... | IDM_CONFUPDATERPROXY |
| - | ? > Debug Info... | IDM_DEBUGINFO |
| - | ? > About Notepad++ | IDM_ABOUT |
| + | ＋ | IDM_FILE_NEW |
| - | ▼ > Recent Window | IDM_DROPLIST_LIST |
| + | ✕ | IDM_FILE_CLOSE |


```
TODO NEXT:
UNFORTUNATELY, A LOT OF THE ONES FROM THE MENUCMDID.H DIDN'T END UP IN MY ORIGINAL TABLE
(I DON'T KNOW WHETHER THERE WAS A REGEX PROBLEM OR A COPY/PASTE ISSUE OR WHAT, BECAUSE THEY SHOULD HAVE ALL BEEN THERE....)
SAVE THIS FOR NOW, AND COME BACK... WILL HAVE TO REGRAB THE NAMES FROM ENGLISH.XML AS WELL :-(

FIND = ^(?=(IDM_\w+)\b :: MENUITEM(?s).*(?-s)(^\d{5} . \b\1\b.*$))
REPL = $2

START WITH RC, then

    //

    &

    ^\h*(BEGIN|END)\h*\R

    , (GRAYED|HELP)$

    MENUITEM "(.*)"
    MENUITEM $1

    ,\h*IDM_
    \x20                                                                 ; IDM_


    ^(\x20{12}POPUP.*\R)(^\x20{16,}MENUITEM.*\R)(?=(?2))
    $1$2$1

    ^(\x20{12})POPUP "(.*)"\R^\x20{16,}MENUITEM
    ${1}MENUITEM ${2} >

    ^(\x20{8}POPUP.*\R)(^\x20{12,}MENUITEM.*\R)(?=(?2))
    $1$2$1

    ^(\x20{8})POPUP "(.*)"\R^\x20{12,}MENUITEM
    ${1}MENUITEM ${2} >

    ^(\x20{4}POPUP.*\R)(^\x20{8,}MENUITEM.*\R)(?=(?2))
    $1$2$1

    ^(\x20{4})POPUP "(.*)"\R^\x20{8,}MENUITEM
    ${1}MENUITEM ${2} >

GETS ME:

MENUITEM File > New                                          ; IDM_FILE_NEW
MENUITEM File > Open...                                          ; IDM_FILE_OPEN
MENUITEM File > Open Containing Folder > Explorer                                          ; IDM_FILE_OPEN_FOLDER
MENUITEM File > Open Containing Folder > cmd                                          ; IDM_FILE_OPEN_CMD
MENUITEM File > Open Containing Folder > PowerShell                                          ; IDM_FILE_OPEN_POWERSHELL
MENUITEM File > Open Containing Folder > Folder as Workspace                                          ; IDM_FILE_CONTAININGFOLDERASWORKSPACE
MENUITEM File > Open in Default Viewer                                          ; IDM_FILE_OPEN_DEFAULT_VIEWER
MENUITEM File > Open Folder as Workspace...                                          ; IDM_FILE_OPENFOLDERASWORKSPACE
MENUITEM File > Reload from Disk                                          ; IDM_FILE_RELOAD
MENUITEM File > Save                                          ; IDM_FILE_SAVE
MENUITEM File > Save As...                                          ; IDM_FILE_SAVEAS
MENUITEM File > Save a Copy As...                                          ; IDM_FILE_SAVECOPYAS
MENUITEM File > Save All                                          ; IDM_FILE_SAVEALL
MENUITEM File > Rename...                                          ; IDM_FILE_RENAME
MENUITEM File > Close                                          ; IDM_FILE_CLOSE
MENUITEM File > Close All                                          ; IDM_FILE_CLOSEALL
MENUITEM File > Close Multiple Documents > Close All but Active Document                                          ; IDM_FILE_CLOSEALL_BUT_CURRENT
MENUITEM File > Close Multiple Documents > Close All but Pinned Documents                                          ; IDM_FILE_CLOSEALL_BUT_PINNED
MENUITEM File > Close Multiple Documents > Close All to the Left                                          ; IDM_FILE_CLOSEALL_TOLEFT
MENUITEM File > Close Multiple Documents > Close All to the Right                                          ; IDM_FILE_CLOSEALL_TORIGHT
MENUITEM File > Close Multiple Documents > Close All Unchanged                                          ; IDM_FILE_CLOSEALL_UNCHANGED
MENUITEM File > Move to Recycle Bin                                          ; IDM_FILE_DELETE
MENUITEM File > Load Session...                                          ; IDM_FILE_LOADSESSION
MENUITEM File > Save Session...                                          ; IDM_FILE_SAVESESSION
MENUITEM File > Print...                                          ; IDM_FILE_PRINT
MENUITEM File > Print Now                                          ; IDM_FILE_PRINTNOW
MENUITEM File > Exit                                          ; IDM_FILE_EXIT
MENUITEM Edit > Undo                                          ; IDM_EDIT_UNDO
MENUITEM Edit > Redo                                          ; IDM_EDIT_REDO
MENUITEM Edit > Cut                                          ; IDM_EDIT_CUT
MENUITEM Edit > Copy                                          ; IDM_EDIT_COPY
MENUITEM Edit > Paste                                          ; IDM_EDIT_PASTE
MENUITEM Edit > Delete                                          ; IDM_EDIT_DELETE
MENUITEM Edit > Select All                                          ; IDM_EDIT_SELECTALL
MENUITEM Edit > Begin/End Select                                          ; IDM_EDIT_BEGINENDSELECT
MENUITEM Edit > Begin/End Select in Column Mode                                          ; IDM_EDIT_BEGINENDSELECT_COLUMNMODE
MENUITEM Edit > Insert > Date Time (short)                                          ; IDM_EDIT_INSERT_DATETIME_SHORT
MENUITEM Edit > Insert > Date Time (long)                                          ; IDM_EDIT_INSERT_DATETIME_LONG
MENUITEM Edit > Insert > Date Time (customized)                                          ; IDM_EDIT_INSERT_DATETIME_CUSTOMIZED
MENUITEM Edit > Copy to Clipboard > Copy Current Full File path                                          ; IDM_EDIT_FULLPATHTOCLIP
MENUITEM Edit > Copy to Clipboard > Copy Current Filename                                          ; IDM_EDIT_FILENAMETOCLIP
MENUITEM Edit > Copy to Clipboard > Copy Current Dir. Path                                          ; IDM_EDIT_CURRENTDIRTOCLIP
MENUITEM Edit > Copy to Clipboard > Copy All Filenames                                          ; IDM_EDIT_COPY_ALL_NAMES
MENUITEM Edit > Copy to Clipboard > Copy All File Paths                                          ; IDM_EDIT_COPY_ALL_PATHS
MENUITEM Edit > Indent > Increase Line Indent                                          ; IDM_EDIT_INS_TAB
MENUITEM Edit > Indent > Decrease Line Indent                                          ; IDM_EDIT_RMV_TAB
MENUITEM Edit > Convert Case to > UPPERCASE                                          ; IDM_EDIT_UPPERCASE
MENUITEM Edit > Convert Case to > lowercase                                          ; IDM_EDIT_LOWERCASE
MENUITEM Edit > Convert Case to > Proper Case                                          ; IDM_EDIT_PROPERCASE_FORCE
MENUITEM Edit > Convert Case to > Proper Case (blend)                                          ; IDM_EDIT_PROPERCASE_BLEND
MENUITEM Edit > Convert Case to > Sentence case                                          ; IDM_EDIT_SENTENCECASE_FORCE
MENUITEM Edit > Convert Case to > Sentence case (blend)                                          ; IDM_EDIT_SENTENCECASE_BLEND
MENUITEM Edit > Convert Case to > iNVERT cASE                                          ; IDM_EDIT_INVERTCASE
MENUITEM Edit > Convert Case to > ranDOm CasE                                          ; IDM_EDIT_RANDOMCASE
MENUITEM Edit > Line Operations > Duplicate Current Line                                          ; IDM_EDIT_DUP_LINE
MENUITEM Edit > Line Operations > Remove Duplicate Lines                                          ; IDM_EDIT_REMOVE_ANY_DUP_LINES
MENUITEM Edit > Line Operations > Remove Consecutive Duplicate Lines                                          ; IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES
MENUITEM Edit > Line Operations > Split Lines                                          ; IDM_EDIT_SPLIT_LINES
MENUITEM Edit > Line Operations > Join Lines                                          ; IDM_EDIT_JOIN_LINES
MENUITEM Edit > Line Operations > Move Up Current Line                                          ; IDM_EDIT_LINE_UP
MENUITEM Edit > Line Operations > Move Down Current Line                                          ; IDM_EDIT_LINE_DOWN
MENUITEM Edit > Line Operations > Remove Empty Lines                                          ; IDM_EDIT_REMOVEEMPTYLINES
MENUITEM Edit > Line Operations > Remove Empty Lines (Containing Blank characters)                                          ; IDM_EDIT_REMOVEEMPTYLINESWITHBLANK
MENUITEM Edit > Line Operations > Insert Blank Line Above Current                                          ; IDM_EDIT_BLANKLINEABOVECURRENT
MENUITEM Edit > Line Operations > Insert Blank Line Below Current                                          ; IDM_EDIT_BLANKLINEBELOWCURRENT
MENUITEM Edit > Line Operations > Reverse Line Order                                          ; IDM_EDIT_SORTLINES_REVERSE_ORDER
MENUITEM Edit > Line Operations > Randomize Line Order                                          ; IDM_EDIT_SORTLINES_RANDOMLY
MENUITEM Edit > Line Operations > Sort Lines Lexicographically Ascending                                          ; IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines Lex. Ascending Ignoring Case                                          ; IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines In Locale Order Ascending                                          ; IDM_EDIT_SORTLINES_LOCALE_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines As Integers Ascending                                          ; IDM_EDIT_SORTLINES_INTEGER_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines As Decimals (Comma) Ascending                                          ; IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines As Decimals (Dot) Ascending                                          ; IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines By Length Ascending                                          ; IDM_EDIT_SORTLINES_LENGTH_ASCENDING
MENUITEM Edit > Line Operations > Sort Lines Lexicographically Descending                                          ; IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING
MENUITEM Edit > Line Operations > Sort Lines Lex. Descending Ignoring Case                                          ; IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING
MENUITEM Edit > Line Operations > Sort Lines In Locale Order Descending                                          ; IDM_EDIT_SORTLINES_LOCALE_DESCENDING
MENUITEM Edit > Line Operations > Sort Lines As Integers Descending                                          ; IDM_EDIT_SORTLINES_INTEGER_DESCENDING
MENUITEM Edit > Line Operations > Sort Lines As Decimals (Comma) Descending                                          ; IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING
MENUITEM Edit > Line Operations > Sort Lines As Decimals (Dot) Descending                                          ; IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING
MENUITEM Edit > Line Operations > Sort Lines By Length Descending                                          ; IDM_EDIT_SORTLINES_LENGTH_DESCENDING
MENUITEM Edit > Comment/Uncomment > Toggle Single Line Comment                                          ; IDM_EDIT_BLOCK_COMMENT
MENUITEM Edit > Comment/Uncomment > Single Line Comment                                          ; IDM_EDIT_BLOCK_COMMENT_SET
MENUITEM Edit > Comment/Uncomment > Single Line Uncomment                                          ; IDM_EDIT_BLOCK_UNCOMMENT
MENUITEM Edit > Comment/Uncomment > Block Comment                                          ; IDM_EDIT_STREAM_COMMENT
MENUITEM Edit > Comment/Uncomment > Block Uncomment                                          ; IDM_EDIT_STREAM_UNCOMMENT
MENUITEM Edit > Auto-Completion > Function Completion                                          ; IDM_EDIT_AUTOCOMPLETE
MENUITEM Edit > Auto-Completion > Word Completion                                          ; IDM_EDIT_AUTOCOMPLETE_CURRENTFILE
MENUITEM Edit > Auto-Completion > Function Parameters Hint                                          ; IDM_EDIT_FUNCCALLTIP
MENUITEM Edit > Auto-Completion > Function Parameters Previous Hint                                          ; IDM_EDIT_FUNCCALLTIP_PREVIOUS
MENUITEM Edit > Auto-Completion > Function Parameters Next Hint                                          ; IDM_EDIT_FUNCCALLTIP_NEXT
MENUITEM Edit > Auto-Completion > Path Completion                                          ; IDM_EDIT_AUTOCOMPLETE_PATH
MENUITEM Edit > EOL Conversion > Windows (CR LF)                                          ; IDM_FORMAT_TODOS
MENUITEM Edit > EOL Conversion > Unix (LF)                                          ; IDM_FORMAT_TOUNIX
MENUITEM Edit > EOL Conversion > Macintosh (CR)                                          ; IDM_FORMAT_TOMAC
MENUITEM Edit > Blank Operations > Trim Trailing Space                                          ; IDM_EDIT_TRIMTRAILING
MENUITEM Edit > Blank Operations > Trim Leading Space                                          ; IDM_EDIT_TRIMLINEHEAD
MENUITEM Edit > Blank Operations > Trim Leading and Trailing Space                                          ; IDM_EDIT_TRIM_BOTH
MENUITEM Edit > Blank Operations > EOL to Space                                          ; IDM_EDIT_EOL2WS
MENUITEM Edit > Blank Operations > Trim both and EOL to Space                                          ; IDM_EDIT_TRIMALL
MENUITEM Edit > Blank Operations > TAB to Space                                          ; IDM_EDIT_TAB2SW
MENUITEM Edit > Blank Operations > Space to TAB (All)                                          ; IDM_EDIT_SW2TAB_ALL
MENUITEM Edit > Blank Operations > Space to TAB (Leading)                                          ; IDM_EDIT_SW2TAB_LEADING
MENUITEM Edit > Paste Special > Paste HTML Content                                          ; IDM_EDIT_PASTE_AS_HTML
MENUITEM Edit > Paste Special > Paste RTF Content                                          ; IDM_EDIT_PASTE_AS_RTF
MENUITEM Edit > Paste Special > Copy Binary Content                                          ; IDM_EDIT_COPY_BINARY
MENUITEM Edit > Paste Special > Cut Binary Content                                          ; IDM_EDIT_CUT_BINARY
MENUITEM Edit > Paste Special > Paste Binary Content                                          ; IDM_EDIT_PASTE_BINARY
MENUITEM Edit > On Selection > Open File                                          ; IDM_EDIT_OPENSELECTEDFILETOEDIT
MENUITEM Edit > On Selection > Open Containing Folder in Explorer                                          ; IDM_EDIT_OPENSELECTEDFILEFOLDERINEXPLORER
MENUITEM Edit > On Selection > Redact Selection █ (Shift: ●)                                          ; IDM_EDIT_REDACT_SELECTION
MENUITEM Edit > On Selection > Search on Internet                                          ; IDM_EDIT_SEARCHONINTERNET
MENUITEM Edit > On Selection > Change Search Engine...                                          ; IDM_EDIT_CHANGESEARCHENGINE
MENUITEM Edit > Multi-select All > Ignore Case  Whole Word                                          ; IDM_EDIT_MULTISELECTALL
MENUITEM Edit > Multi-select All > Match Case Only                                          ; IDM_EDIT_MULTISELECTALLMATCHCASE
MENUITEM Edit > Multi-select All > Match Whole Word Only                                          ; IDM_EDIT_MULTISELECTALLWHOLEWORD
MENUITEM Edit > Multi-select All > Match Case  Whole Word                                          ; IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD
MENUITEM Edit > Multi-select Next > Ignore Case  Whole Word                                          ; IDM_EDIT_MULTISELECTNEXT
MENUITEM Edit > Multi-select Next > Match Case Only                                          ; IDM_EDIT_MULTISELECTNEXTMATCHCASE
MENUITEM Edit > Multi-select Next > Match Whole Word Only                                          ; IDM_EDIT_MULTISELECTNEXTWHOLEWORD
MENUITEM Edit > Multi-select Next > Match Case  Whole Word                                          ; IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD
MENUITEM Edit > Undo the Latest Added Multi-Select                                          ; IDM_EDIT_MULTISELECTUNDO
MENUITEM Edit > Skip Current  Go to Next Multi-select                              ; IDM_EDIT_MULTISELECTSSKIP
MENUITEM Edit > Column Mode...                                          ; IDM_EDIT_COLUMNMODETIP
MENUITEM Edit > Column Editor...                                          ; IDM_EDIT_COLUMNMODE
MENUITEM Edit > Character Panel                                          ; IDM_EDIT_CHAR_PANEL
MENUITEM Edit > Clipboard History                                          ; IDM_EDIT_CLIPBOARDHISTORY_PANEL
MENUITEM Edit > Read-Only in Notepad++ > Read-Only on Current Document                                          ; IDM_EDIT_TOGGLEREADONLY
MENUITEM Edit > Read-Only in Notepad++ > Read-Only for All Documents                                          ; IDM_EDIT_SETREADONLYFORALLDOCS
MENUITEM Edit > Read-Only in Notepad++ > Clear Read-Only for All Documents                                          ; IDM_EDIT_CLEARREADONLYFORALLDOCS
MENUITEM Edit > Read-Only Attribute in Windows                                          ; IDM_EDIT_TOGGLESYSTEMREADONLY
MENUITEM Search > Find...                                          ; IDM_SEARCH_FIND
MENUITEM Search > Find in Files...                                          ; IDM_SEARCH_FINDINFILES
MENUITEM Search > Find Next                                          ; IDM_SEARCH_FINDNEXT
MENUITEM Search > Find Previous                                          ; IDM_SEARCH_FINDPREV
MENUITEM Search > Select and Find Next                                          ; IDM_SEARCH_SETANDFINDNEXT
MENUITEM Search > Select and Find Previous                                          ; IDM_SEARCH_SETANDFINDPREV
MENUITEM Search > Find (Volatile) Next                                          ; IDM_SEARCH_VOLATILE_FINDNEXT
MENUITEM Search > Find (Volatile) Previous                                          ; IDM_SEARCH_VOLATILE_FINDPREV
MENUITEM Search > Replace...                                          ; IDM_SEARCH_REPLACE
MENUITEM Search > Incremental Search                                          ; IDM_SEARCH_FINDINCREMENT
MENUITEM Search > Search Results Window                                          ; IDM_FOCUS_ON_FOUND_RESULTS
MENUITEM Search > Next Search Result                                          ; IDM_SEARCH_GOTONEXTFOUND
MENUITEM Search > Previous Search Result                                          ; IDM_SEARCH_GOTOPREVFOUND
MENUITEM Search > Go to...                                          ; IDM_SEARCH_GOTOLINE
MENUITEM Search > Go to Matching Brace                                          ; IDM_SEARCH_GOTOMATCHINGBRACE
MENUITEM Search > Select All In-between {} [] or ()                                          ; IDM_SEARCH_SELECTMATCHINGBRACES
MENUITEM Search > Mark...                                          ; IDM_SEARCH_MARK
MENUITEM Search > Change History > Go to Next Change                                          ; IDM_SEARCH_CHANGED_NEXT
MENUITEM Search > Change History > Go to Previous Change                                          ; IDM_SEARCH_CHANGED_PREV
MENUITEM Search > Change History > Clear Change History                                          ; IDM_SEARCH_CLEAR_CHANGE_HISTORY
MENUITEM Search > Style All Occurrences of Token > Using 1st Style                                          ; IDM_SEARCH_MARKALLEXT1
MENUITEM Search > Style All Occurrences of Token > Using 2nd Style                                          ; IDM_SEARCH_MARKALLEXT2
MENUITEM Search > Style All Occurrences of Token > Using 3rd Style                                          ; IDM_SEARCH_MARKALLEXT3
MENUITEM Search > Style All Occurrences of Token > Using 4th Style                                          ; IDM_SEARCH_MARKALLEXT4
MENUITEM Search > Style All Occurrences of Token > Using 5th Style                                          ; IDM_SEARCH_MARKALLEXT5
MENUITEM Search > Style One Token > Using 1st Style                                          ; IDM_SEARCH_MARKONEEXT1
MENUITEM Search > Style One Token > Using 2nd Style                                          ; IDM_SEARCH_MARKONEEXT2
MENUITEM Search > Style One Token > Using 3rd Style                                          ; IDM_SEARCH_MARKONEEXT3
MENUITEM Search > Style One Token > Using 4th Style                                          ; IDM_SEARCH_MARKONEEXT4
MENUITEM Search > Style One Token > Using 5th Style                                          ; IDM_SEARCH_MARKONEEXT5
MENUITEM Search > Clear Style > Clear 1st Style                                          ; IDM_SEARCH_UNMARKALLEXT1
MENUITEM Search > Clear Style > Clear 2nd Style                                          ; IDM_SEARCH_UNMARKALLEXT2
MENUITEM Search > Clear Style > Clear 3rd Style                                          ; IDM_SEARCH_UNMARKALLEXT3
MENUITEM Search > Clear Style > Clear 4th Style                                          ; IDM_SEARCH_UNMARKALLEXT4
MENUITEM Search > Clear Style > Clear 5th Style                                          ; IDM_SEARCH_UNMARKALLEXT5
MENUITEM Search > Clear Style > Clear all Styles                                          ; IDM_SEARCH_CLEARALLMARKS
MENUITEM Search > Jump Up > 1st Style                                          ; IDM_SEARCH_GOPREVMARKER1
MENUITEM Search > Jump Up > 2nd Style                                          ; IDM_SEARCH_GOPREVMARKER2
MENUITEM Search > Jump Up > 3rd Style                                          ; IDM_SEARCH_GOPREVMARKER3
MENUITEM Search > Jump Up > 4th Style                                          ; IDM_SEARCH_GOPREVMARKER4
MENUITEM Search > Jump Up > 5th Style                                          ; IDM_SEARCH_GOPREVMARKER5
MENUITEM Search > Jump Up > Find Mark Style                                          ; IDM_SEARCH_GOPREVMARKER_DEF
MENUITEM Search > Jump Down > 1st Style                                          ; IDM_SEARCH_GONEXTMARKER1
MENUITEM Search > Jump Down > 2nd Style                                          ; IDM_SEARCH_GONEXTMARKER2
MENUITEM Search > Jump Down > 3rd Style                                          ; IDM_SEARCH_GONEXTMARKER3
MENUITEM Search > Jump Down > 4th Style                                          ; IDM_SEARCH_GONEXTMARKER4
MENUITEM Search > Jump Down > 5th Style                                          ; IDM_SEARCH_GONEXTMARKER5
MENUITEM Search > Jump Down > Find Mark Style                                          ; IDM_SEARCH_GONEXTMARKER_DEF
MENUITEM Search > Copy Styled Text > 1st Style                                          ; IDM_SEARCH_STYLE1TOCLIP
MENUITEM Search > Copy Styled Text > 2nd Style                                          ; IDM_SEARCH_STYLE2TOCLIP
MENUITEM Search > Copy Styled Text > 3rd Style                                          ; IDM_SEARCH_STYLE3TOCLIP
MENUITEM Search > Copy Styled Text > 4th Style                                          ; IDM_SEARCH_STYLE4TOCLIP
MENUITEM Search > Copy Styled Text > 5th Style                                          ; IDM_SEARCH_STYLE5TOCLIP
MENUITEM Search > Copy Styled Text > All Styles                                          ; IDM_SEARCH_ALLSTYLESTOCLIP
MENUITEM Search > Copy Styled Text > Find Mark Style                                          ; IDM_SEARCH_MARKEDTOCLIP
MENUITEM Search > Bookmark > Toggle Bookmark                                           ; IDM_SEARCH_TOGGLE_BOOKMARK
MENUITEM Search > Bookmark > Next Bookmark                                          ; IDM_SEARCH_NEXT_BOOKMARK
MENUITEM Search > Bookmark > Previous Bookmark                                          ; IDM_SEARCH_PREV_BOOKMARK
MENUITEM Search > Bookmark > Clear All Bookmarks                                          ; IDM_SEARCH_CLEAR_BOOKMARKS
MENUITEM Search > Bookmark > Cut Bookmarked Lines                                          ; IDM_SEARCH_CUTMARKEDLINES
MENUITEM Search > Bookmark > Copy Bookmarked Lines                                          ; IDM_SEARCH_COPYMARKEDLINES
MENUITEM Search > Bookmark > Paste to (Replace) Bookmarked Lines                                          ; IDM_SEARCH_PASTEMARKEDLINES
MENUITEM Search > Bookmark > Remove Bookmarked Lines                                          ; IDM_SEARCH_DELETEMARKEDLINES
MENUITEM Search > Bookmark > Remove Non-Bookmarked Lines                                          ; IDM_SEARCH_DELETEUNMARKEDLINES
MENUITEM Search > Bookmark > Inverse Bookmarks                                          ; IDM_SEARCH_INVERSEMARKS
MENUITEM Search > Find characters in range...                                          ; IDM_SEARCH_FINDCHARINRANGE
MENUITEM View > Always on Top                                          ; IDM_VIEW_ALWAYSONTOP
MENUITEM View > Toggle Full Screen Mode                                          ; IDM_VIEW_FULLSCREENTOGGLE
MENUITEM View > Post-It                                          ; IDM_VIEW_POSTIT
MENUITEM View > Distraction Free Mode                                          ; IDM_VIEW_DISTRACTIONFREE
MENUITEM View > View Current File in > Firefox                                          ; IDM_VIEW_IN_FIREFOX
MENUITEM View > View Current File in > Chrome                                          ; IDM_VIEW_IN_CHROME
MENUITEM View > View Current File in > Edge                                          ; IDM_VIEW_IN_EDGE
MENUITEM View > View Current File in > IE                                          ; IDM_VIEW_IN_IE
MENUITEM View > Show Symbol > Show Space and Tab                                          ; IDM_VIEW_TAB_SPACE
MENUITEM View > Show Symbol > Show End of Line                                          ; IDM_VIEW_EOL
MENUITEM View > Show Symbol > Show Non-Printing Characters                                          ; IDM_VIEW_NPC
MENUITEM View > Show Symbol > Show Control Characters  Unicode EOL                                          ; IDM_VIEW_NPC_CCUNIEOL
MENUITEM View > Show Symbol > Show All Characters                                          ; IDM_VIEW_ALL_CHARACTERS
MENUITEM View > Show Symbol > Show Indent Guide                                          ; IDM_VIEW_INDENT_GUIDE
MENUITEM View > Show Symbol > Show Wrap Symbol                                          ; IDM_VIEW_WRAP_SYMBOL
MENUITEM View > Zoom > Zoom In (Ctrl+Mouse Wheel Up)                                          ; IDM_VIEW_ZOOMIN
MENUITEM View > Zoom > Zoom Out (Ctrl+Mouse Wheel Down)                                          ; IDM_VIEW_ZOOMOUT
MENUITEM View > Zoom > Restore Default Zoom                                          ; IDM_VIEW_ZOOMRESTORE
MENUITEM View > Zoom > Synchronize Across Views                                          ; IDM_VIEW_ZOOM_SYNC
MENUITEM View > Move/Clone Current Document > Move to Other View                                          ; IDM_VIEW_GOTO_ANOTHER_VIEW
MENUITEM View > Move/Clone Current Document > Clone to Other View                                          ; IDM_VIEW_CLONE_TO_ANOTHER_VIEW
MENUITEM View > Move/Clone Current Document > Move to New Instance                                          ; IDM_VIEW_GOTO_NEW_INSTANCE
MENUITEM View > Move/Clone Current Document > Open in New Instance                                          ; IDM_VIEW_LOAD_IN_NEW_INSTANCE
MENUITEM View > Tab > 1st Tab                                          ; IDM_VIEW_TAB1
MENUITEM View > Tab > 2nd Tab                                          ; IDM_VIEW_TAB2
MENUITEM View > Tab > 3rd Tab                                          ; IDM_VIEW_TAB3
MENUITEM View > Tab > 4th Tab                                          ; IDM_VIEW_TAB4
MENUITEM View > Tab > 5th Tab                                          ; IDM_VIEW_TAB5
MENUITEM View > Tab > 6th Tab                                          ; IDM_VIEW_TAB6
MENUITEM View > Tab > 7th Tab                                          ; IDM_VIEW_TAB7
MENUITEM View > Tab > 8th Tab                                          ; IDM_VIEW_TAB8
MENUITEM View > Tab > 9th Tab                                          ; IDM_VIEW_TAB9
MENUITEM View > Tab > First Tab                                          ; IDM_VIEW_TAB_START
MENUITEM View > Tab > Last Tab                                          ; IDM_VIEW_TAB_END
MENUITEM View > Tab > Next Tab                                          ; IDM_VIEW_TAB_NEXT
MENUITEM View > Tab > Previous Tab                                          ; IDM_VIEW_TAB_PREV
MENUITEM View > Tab > Move to Start                                          ; IDM_VIEW_GOTO_START
MENUITEM View > Tab > Move to End                                          ; IDM_VIEW_GOTO_END
MENUITEM View > Tab > Move Tab Forward                                          ; IDM_VIEW_TAB_MOVEFORWARD
MENUITEM View > Tab > Move Tab Backward                                          ; IDM_VIEW_TAB_MOVEBACKWARD
MENUITEM View > Tab > Apply Color 1                                          ; IDM_VIEW_TAB_COLOUR_1
MENUITEM View > Tab > Apply Color 2                                          ; IDM_VIEW_TAB_COLOUR_2
MENUITEM View > Tab > Apply Color 3                                          ; IDM_VIEW_TAB_COLOUR_3
MENUITEM View > Tab > Apply Color 4                                          ; IDM_VIEW_TAB_COLOUR_4
MENUITEM View > Tab > Apply Color 5                                          ; IDM_VIEW_TAB_COLOUR_5
MENUITEM View > Tab > Remove Color                                          ; IDM_VIEW_TAB_COLOUR_NONE
MENUITEM View > Word wrap                                          ; IDM_VIEW_WRAP
MENUITEM View > Focus on Another View                                          ; IDM_VIEW_SWITCHTO_OTHER_VIEW
MENUITEM View > Hide Lines                                          ; IDM_VIEW_HIDELINES
MENUITEM View > Fold All                                          ; IDM_VIEW_FOLDALL
MENUITEM View > Unfold All                                          ; IDM_VIEW_UNFOLDALL
MENUITEM View > Fold Current Level                                          ; IDM_VIEW_FOLD_CURRENT
MENUITEM View > Unfold Current Level                                          ; IDM_VIEW_UNFOLD_CURRENT
MENUITEM View > Fold Level > 1                                          ; IDM_VIEW_FOLD_1
MENUITEM View > Fold Level > 2                                          ; IDM_VIEW_FOLD_2
MENUITEM View > Fold Level > 3                                          ; IDM_VIEW_FOLD_3
MENUITEM View > Fold Level > 4                                          ; IDM_VIEW_FOLD_4
MENUITEM View > Fold Level > 5                                          ; IDM_VIEW_FOLD_5
MENUITEM View > Fold Level > 6                                          ; IDM_VIEW_FOLD_6
MENUITEM View > Fold Level > 7                                          ; IDM_VIEW_FOLD_7
MENUITEM View > Fold Level > 8                                          ; IDM_VIEW_FOLD_8
MENUITEM View > Unfold Level > 1                                          ; IDM_VIEW_UNFOLD_1
MENUITEM View > Unfold Level > 2                                          ; IDM_VIEW_UNFOLD_2
MENUITEM View > Unfold Level > 3                                          ; IDM_VIEW_UNFOLD_3
MENUITEM View > Unfold Level > 4                                          ; IDM_VIEW_UNFOLD_4
MENUITEM View > Unfold Level > 5                                          ; IDM_VIEW_UNFOLD_5
MENUITEM View > Unfold Level > 6                                          ; IDM_VIEW_UNFOLD_6
MENUITEM View > Unfold Level > 7                                          ; IDM_VIEW_UNFOLD_7
MENUITEM View > Unfold Level > 8                                          ; IDM_VIEW_UNFOLD_8
MENUITEM View > Summary...                                          ; IDM_VIEW_SUMMARY
MENUITEM View > Project Panels > Project Panel 1                                          ; IDM_VIEW_PROJECT_PANEL_1
MENUITEM View > Project Panels > Project Panel 2                                          ; IDM_VIEW_PROJECT_PANEL_2
MENUITEM View > Project Panels > Project Panel 3                                          ; IDM_VIEW_PROJECT_PANEL_3
MENUITEM View > Folder as Workspace                                          ; IDM_VIEW_FILEBROWSER
MENUITEM View > Document Map                                          ; IDM_VIEW_DOC_MAP
MENUITEM View > Document List                                          ; IDM_VIEW_DOCLIST
MENUITEM View > Function List                                          ; IDM_VIEW_FUNC_LIST
MENUITEM View > Synchronize Vertical Scrolling                                          ; IDM_VIEW_SYNSCROLLV
MENUITEM View > Synchronize Horizontal Scrolling                                          ; IDM_VIEW_SYNSCROLLH
MENUITEM View > Text Direction RTL                                          ; IDM_EDIT_RTL
MENUITEM View > Text Direction LTR                                          ; IDM_EDIT_LTR
MENUITEM View > Monitoring (tail -f)                                          ; IDM_VIEW_MONITORING
MENUITEM Encoding > ANSI                                          ; IDM_FORMAT_ANSI
MENUITEM Encoding > UTF-8                                          ; IDM_FORMAT_AS_UTF_8
MENUITEM Encoding > UTF-8-BOM                                          ; IDM_FORMAT_UTF_8
MENUITEM Encoding > UTF-16 BE BOM                                          ; IDM_FORMAT_UTF_16BE
MENUITEM Encoding > UTF-16 LE BOM                                          ; IDM_FORMAT_UTF_16LE
MENUITEM Encoding > Character sets > Arabic > ISO 8859-6                                          ; IDM_FORMAT_ISO_8859_6
MENUITEM Encoding > Character sets > Arabic > OEM 720                                          ; IDM_FORMAT_DOS_720
MENUITEM Encoding > Character sets > Arabic > Windows-1256                                          ; IDM_FORMAT_WIN_1256
MENUITEM Encoding > Character sets > Baltic > ISO 8859-4                                          ; IDM_FORMAT_ISO_8859_4
MENUITEM Encoding > Character sets > Baltic > ISO 8859-13                                          ; IDM_FORMAT_ISO_8859_13
MENUITEM Encoding > Character sets > Baltic > OEM 775                                          ; IDM_FORMAT_DOS_775
MENUITEM Encoding > Character sets > Baltic > Windows-1257                                          ; IDM_FORMAT_WIN_1257
MENUITEM Encoding > Character sets > Celtic > ISO 8859-14                                          ; IDM_FORMAT_ISO_8859_14
MENUITEM Encoding > Character sets > Cyrillic > ISO 8859-5                                          ; IDM_FORMAT_ISO_8859_5
MENUITEM Encoding > Character sets > Cyrillic > KOI8-R                                          ; IDM_FORMAT_KOI8R_CYRILLIC
MENUITEM Encoding > Character sets > Cyrillic > KOI8-U                                          ; IDM_FORMAT_KOI8U_CYRILLIC
MENUITEM Encoding > Character sets > Cyrillic > Macintosh                                          ; IDM_FORMAT_MAC_CYRILLIC
MENUITEM Encoding > Character sets > Cyrillic > OEM 855                                          ; IDM_FORMAT_DOS_855
MENUITEM Encoding > Character sets > Cyrillic > OEM 866                                          ; IDM_FORMAT_DOS_866
MENUITEM Encoding > Character sets > Cyrillic > Windows-1251                                          ; IDM_FORMAT_WIN_1251
MENUITEM Encoding > Character sets > Central European > OEM 852                                          ; IDM_FORMAT_DOS_852
MENUITEM Encoding > Character sets > Central European > Windows-1250                                          ; IDM_FORMAT_WIN_1250
MENUITEM Encoding > Character sets > Chinese > Big5 (Traditional)                                          ; IDM_FORMAT_BIG5
MENUITEM Encoding > Character sets > Chinese > GB2312 (Simplified)                                          ; IDM_FORMAT_GB2312
MENUITEM Encoding > Character sets > Eastern European > ISO 8859-2                                          ; IDM_FORMAT_ISO_8859_2
MENUITEM Encoding > Character sets > Greek > ISO 8859-7                                          ; IDM_FORMAT_ISO_8859_7
MENUITEM Encoding > Character sets > Greek > OEM 737                                          ; IDM_FORMAT_DOS_737
MENUITEM Encoding > Character sets > Greek > OEM 869                                          ; IDM_FORMAT_DOS_869
MENUITEM Encoding > Character sets > Greek > Windows-1253                                          ; IDM_FORMAT_WIN_1253
MENUITEM Encoding > Character sets > Hebrew > ISO 8859-8                                          ; IDM_FORMAT_ISO_8859_8
MENUITEM Encoding > Character sets > Hebrew > OEM 862                                          ; IDM_FORMAT_DOS_862
MENUITEM Encoding > Character sets > Hebrew > Windows-1255                                          ; IDM_FORMAT_WIN_1255
MENUITEM Encoding > Character sets > Japanese > Shift-JIS                                          ; IDM_FORMAT_SHIFT_JIS
MENUITEM Encoding > Character sets > Korean > Windows 949                                          ; IDM_FORMAT_KOREAN_WIN
MENUITEM Encoding > Character sets > Korean > EUC-KR                                          ; IDM_FORMAT_EUC_KR
MENUITEM Encoding > Character sets > North European > OEM 861 : Icelandic                                          ; IDM_FORMAT_DOS_861
MENUITEM Encoding > Character sets > North European > OEM 865 : Nordic                                          ; IDM_FORMAT_DOS_865
MENUITEM Encoding > Character sets > Thai > TIS-620                                          ; IDM_FORMAT_TIS_620
MENUITEM Encoding > Character sets > Turkish > ISO 8859-3                                          ; IDM_FORMAT_ISO_8859_3
MENUITEM Encoding > Character sets > Turkish > ISO 8859-9                                          ; IDM_FORMAT_ISO_8859_9
MENUITEM Encoding > Character sets > Turkish > OEM 857                                          ; IDM_FORMAT_DOS_857
MENUITEM Encoding > Character sets > Turkish > Windows-1254                                          ; IDM_FORMAT_WIN_1254
MENUITEM Encoding > Character sets > Western European > ISO 8859-1                                          ; IDM_FORMAT_ISO_8859_1
MENUITEM Encoding > Character sets > Western European > ISO 8859-10                                          ; IDM_FORMAT_ISO_8859_10
MENUITEM Encoding > Character sets > Western European > ISO 8859-15                                          ; IDM_FORMAT_ISO_8859_15
MENUITEM Encoding > Character sets > Western European > OEM 850                                          ; IDM_FORMAT_DOS_850
MENUITEM Encoding > Character sets > Western European > OEM 858                                          ; IDM_FORMAT_DOS_858
MENUITEM Encoding > Character sets > Western European > OEM 860 : Portuguese                                          ; IDM_FORMAT_DOS_860
MENUITEM Encoding > Character sets > Western European > OEM 863 : French                                          ; IDM_FORMAT_DOS_863
MENUITEM Encoding > Character sets > Western European > OEM-US                                          ; IDM_FORMAT_DOS_437
MENUITEM Encoding > Character sets > Western European > Windows-1252                                          ; IDM_FORMAT_WIN_1252
MENUITEM Encoding > Character sets > Vietnamese > Windows-1258                                          ; IDM_FORMAT_WIN_1258
MENUITEM Encoding > Convert to ANSI                                          ; IDM_FORMAT_CONV2_ANSI
MENUITEM Encoding > Convert to UTF-8                                          ; IDM_FORMAT_CONV2_AS_UTF_8
MENUITEM Encoding > Convert to UTF-8-BOM                                          ; IDM_FORMAT_CONV2_UTF_8
MENUITEM Encoding > Convert to UTF-16 BE BOM                                          ; IDM_FORMAT_CONV2_UTF_16BE
MENUITEM Encoding > Convert to UTF-16 LE BOM                                          ; IDM_FORMAT_CONV2_UTF_16LE
MENUITEM Language > None (Normal Text)                                          ; IDM_LANG_TEXT
MENUITEM Language > ActionScript                                          ; IDM_LANG_FLASH
MENUITEM Language > Ada                                          ; IDM_LANG_ADA
MENUITEM Language > ASN.1                                          ; IDM_LANG_ASN1
MENUITEM Language > ASP                                          ; IDM_LANG_ASP
MENUITEM Language > Assembly                                          ; IDM_LANG_ASM
MENUITEM Language > AutoIt                                          ; IDM_LANG_AU3
MENUITEM Language > AviSynth                                          ; IDM_LANG_AVS
MENUITEM Language > BaanC                                          ; IDM_LANG_BAANC
MENUITEM Language > Batch                                          ; IDM_LANG_BATCH
MENUITEM Language > Blitzbasic                                          ; IDM_LANG_BLITZBASIC
MENUITEM Language > C                                          ; IDM_LANG_C
MENUITEM Language > C#                                          ; IDM_LANG_CS
MENUITEM Language > C++                                          ; IDM_LANG_CPP
MENUITEM Language > Caml                                          ; IDM_LANG_CAML
MENUITEM Language > CMake                                          ; IDM_LANG_CMAKE
MENUITEM Language > COBOL                                          ; IDM_LANG_COBOL
MENUITEM Language > CSound                                          ; IDM_LANG_CSOUND
MENUITEM Language > CoffeeScript                                          ; IDM_LANG_COFFEESCRIPT
MENUITEM Language > CSS                                          ; IDM_LANG_CSS
MENUITEM Language > D                                          ; IDM_LANG_D
MENUITEM Language > Diff                                          ; IDM_LANG_DIFF
MENUITEM Language > Erlang                                          ; IDM_LANG_ERLANG
MENUITEM Language > ErrorList                                          ; IDM_LANG_ERRORLIST
MENUITEM Language > Escape Sequence (ANSI)                                          ; IDM_LANG_ESCSEQ
MENUITEM Language > ESCRIPT                                          ; IDM_LANG_ESCRIPT
MENUITEM Language > Forth                                          ; IDM_LANG_FORTH
MENUITEM Language > Fortran (free form)                                          ; IDM_LANG_FORTRAN
MENUITEM Language > Fortran (fixed form)                                          ; IDM_LANG_FORTRAN_77
MENUITEM Language > Freebasic                                          ; IDM_LANG_FREEBASIC
MENUITEM Language > GDScript                                          ; IDM_LANG_GDSCRIPT
MENUITEM Language > Go                                          ; IDM_LANG_GOLANG
MENUITEM Language > Gui4Cli                                          ; IDM_LANG_GUI4CLI
MENUITEM Language > Haskell                                          ; IDM_LANG_HASKELL
MENUITEM Language > Hollywood                                          ; IDM_LANG_HOLLYWOOD
MENUITEM Language > HTML                                          ; IDM_LANG_HTML
MENUITEM Language > INI file                                          ; IDM_LANG_INI
MENUITEM Language > Inno Setup                                          ; IDM_LANG_INNO
MENUITEM Language > Intel HEX                                          ; IDM_LANG_IHEX
MENUITEM Language > Java                                          ; IDM_LANG_JAVA
MENUITEM Language > JavaScript                                          ; IDM_LANG_JS
MENUITEM Language > JSON                                          ; IDM_LANG_JSON
MENUITEM Language > JSON5                                          ; IDM_LANG_JSON5
MENUITEM Language > JSP                                          ; IDM_LANG_JSP
MENUITEM Language > KIXtart                                          ; IDM_LANG_KIX
MENUITEM Language > LISP                                          ; IDM_LANG_LISP
MENUITEM Language > LaTeX                                          ; IDM_LANG_LATEX
MENUITEM Language > Lua                                          ; IDM_LANG_LUA
MENUITEM Language > Makefile                                          ; IDM_LANG_MAKEFILE
MENUITEM Language > Matlab                                          ; IDM_LANG_MATLAB
MENUITEM Language > Microsoft Transact-SQL                                          ; IDM_LANG_MSSQL
MENUITEM Language > MMIXAL                                          ; IDM_LANG_MMIXAL
MENUITEM Language > MS-DOS Style                                          ; IDM_LANG_ASCII
MENUITEM Language > Nim                                          ; IDM_LANG_NIM
MENUITEM Language > Nncrontab                                          ; IDM_LANG_NNCRONTAB
MENUITEM Language > NSIS                                          ; IDM_LANG_NSIS
MENUITEM Language > Objective-C                                          ; IDM_LANG_OBJC
MENUITEM Language > OScript                                          ; IDM_LANG_OSCRIPT
MENUITEM Language > Pascal                                          ; IDM_LANG_PASCAL
MENUITEM Language > Perl                                          ; IDM_LANG_PERL
MENUITEM Language > PHP                                          ; IDM_LANG_PHP
MENUITEM Language > PostScript                                          ; IDM_LANG_PS
MENUITEM Language > PowerShell                                          ; IDM_LANG_POWERSHELL
MENUITEM Language > Properties                                          ; IDM_LANG_PROPS
MENUITEM Language > Purebasic                                          ; IDM_LANG_PUREBASIC
MENUITEM Language > Python                                          ; IDM_LANG_PYTHON
MENUITEM Language > R                                          ; IDM_LANG_R
MENUITEM Language > Raku                                          ; IDM_LANG_RAKU
MENUITEM Language > REBOL                                          ; IDM_LANG_REBOL
MENUITEM Language > Registry                                          ; IDM_LANG_REGISTRY
MENUITEM Language > Resource file                                          ; IDM_LANG_RC
MENUITEM Language > Ruby                                          ; IDM_LANG_RUBY
MENUITEM Language > Rust                                          ; IDM_LANG_RUST
MENUITEM Language > SAS                                          ; IDM_LANG_SAS
MENUITEM Language > Shell                                          ; IDM_LANG_BASH
MENUITEM Language > Scheme                                          ; IDM_LANG_SCHEME
MENUITEM Language > Smalltalk                                          ; IDM_LANG_SMALLTALK
MENUITEM Language > Spice                                          ; IDM_LANG_SPICE
MENUITEM Language > SQL                                          ; IDM_LANG_SQL
MENUITEM Language > Swift                                          ; IDM_LANG_SWIFT
MENUITEM Language > S-Record                                          ; IDM_LANG_SREC
MENUITEM Language > TCL                                          ; IDM_LANG_TCL
MENUITEM Language > Tektronix extended HEX                                          ; IDM_LANG_TEHEX
MENUITEM Language > TeX                                          ; IDM_LANG_TEX
MENUITEM Language > TOML                                          ; IDM_LANG_TOML
MENUITEM Language > txt2tags                                          ; IDM_LANG_TXT2TAGS
MENUITEM Language > TypeScript                                          ; IDM_LANG_TYPESCRIPT
MENUITEM Language > Verilog                                          ; IDM_LANG_VERILOG
MENUITEM Language > VHDL                                          ; IDM_LANG_VHDL
MENUITEM Language > Visual Basic                                          ; IDM_LANG_VB
MENUITEM Language > Visual Prolog                                          ; IDM_LANG_VISUALPROLOG
MENUITEM Language > XML                                          ; IDM_LANG_XML
MENUITEM Language > YAML                                          ; IDM_LANG_YAML
MENUITEM Language > Define your language...                                          ; IDM_LANG_USER_DLG
MENUITEM Language > Open User Defined Language folder...                                          ; IDM_LANG_OPENUDLDIR
MENUITEM Language > Notepad++ User Defined Languages Collection                                          ; IDM_LANG_UDLCOLLECTION_PROJECT_SITE
MENUITEM Language > User-Defined                                          ; IDM_LANG_USER
MENUITEM Language > None (Normal Text)                                          ; IDM_LANG_TEXT
MENUITEM Language > A > ActionScript                                          ; IDM_LANG_FLASH
MENUITEM Language > A > Ada                                          ; IDM_LANG_ADA
MENUITEM Language > A > ASN.1                                          ; IDM_LANG_ASN1
MENUITEM Language > A > ASP                                          ; IDM_LANG_ASP
MENUITEM Language > A > Assembly                                          ; IDM_LANG_ASM
MENUITEM Language > A > AutoIt                                          ; IDM_LANG_AU3
MENUITEM Language > A > AviSynth                                          ; IDM_LANG_AVS
MENUITEM Language > B > BaanC                                          ; IDM_LANG_BAANC
MENUITEM Language > B > Batch                                          ; IDM_LANG_BATCH
MENUITEM Language > B > Blitzbasic                                          ; IDM_LANG_BLITZBASIC
MENUITEM Language > C > C                                          ; IDM_LANG_C
MENUITEM Language > C > C#                                          ; IDM_LANG_CS
MENUITEM Language > C > C++                                          ; IDM_LANG_CPP
MENUITEM Language > C > Caml                                          ; IDM_LANG_CAML
MENUITEM Language > C > CMake                                          ; IDM_LANG_CMAKE
MENUITEM Language > C > COBOL                                          ; IDM_LANG_COBOL
MENUITEM Language > C > CSound                                          ; IDM_LANG_CSOUND
MENUITEM Language > C > CoffeeScript                                          ; IDM_LANG_COFFEESCRIPT
MENUITEM Language > C > CSS                                          ; IDM_LANG_CSS
MENUITEM Language > D > D                                          ; IDM_LANG_D
MENUITEM Language > D > Diff                                          ; IDM_LANG_DIFF
MENUITEM Language > E > Erlang                                          ; IDM_LANG_ERLANG
MENUITEM Language > E > ErrorList                                          ; IDM_LANG_ERRORLIST
MENUITEM Language > E > Escape Sequence (ANSI)                                          ; IDM_LANG_ESCSEQ
MENUITEM Language > E > ESCRIPT                                          ; IDM_LANG_ESCRIPT
MENUITEM Language > F > Forth                                          ; IDM_LANG_FORTH
MENUITEM Language > F > Fortran (free form)                                          ; IDM_LANG_FORTRAN
MENUITEM Language > F > Fortran (fixed form)                                          ; IDM_LANG_FORTRAN_77
MENUITEM Language > F > Freebasic                                          ; IDM_LANG_FREEBASIC
MENUITEM Language > G > GDScript                                          ; IDM_LANG_GDSCRIPT
MENUITEM Language > G > Go                                          ; IDM_LANG_GOLANG
MENUITEM Language > G > Gui4Cli                                          ; IDM_LANG_GUI4CLI
MENUITEM Language > H > Haskell                                          ; IDM_LANG_HASKELL
MENUITEM Language > H > Hollywood                                          ; IDM_LANG_HOLLYWOOD
MENUITEM Language > H > HTML                                          ; IDM_LANG_HTML
MENUITEM Language > I > INI file                                          ; IDM_LANG_INI
MENUITEM Language > I > Inno Setup                                          ; IDM_LANG_INNO
MENUITEM Language > I > Intel HEX                                          ; IDM_LANG_IHEX
MENUITEM Language > J > Java                                          ; IDM_LANG_JAVA
MENUITEM Language > J > JavaScript                                          ; IDM_LANG_JS
MENUITEM Language > J > JSON                                          ; IDM_LANG_JSON
MENUITEM Language > J > JSON5                                          ; IDM_LANG_JSON5
MENUITEM Language > J > JSP                                          ; IDM_LANG_JSP
MENUITEM Language > KIXtart                                          ; IDM_LANG_KIX
MENUITEM Language > L > LaTeX                                          ; IDM_LANG_LATEX
MENUITEM Language > L > LISP                                          ; IDM_LANG_LISP
MENUITEM Language > L > Lua                                          ; IDM_LANG_LUA
MENUITEM Language > M > Makefile                                          ; IDM_LANG_MAKEFILE
MENUITEM Language > M > Matlab                                          ; IDM_LANG_MATLAB
MENUITEM Language > M > Microsoft Transact-SQL                         ; IDM_LANG_MSSQL
MENUITEM Language > M > MMIXAL                                          ; IDM_LANG_MMIXAL
MENUITEM Language > M > MS-DOS Style                                          ; IDM_LANG_ASCII
MENUITEM Language > N > Nim                                          ; IDM_LANG_NIM
MENUITEM Language > N > Nncrontab                                          ; IDM_LANG_NNCRONTAB
MENUITEM Language > N > NSIS                                          ; IDM_LANG_NSIS
MENUITEM Language > O > Objective-C                                          ; IDM_LANG_OBJC
MENUITEM Language > O > OScript                                          ; IDM_LANG_OSCRIPT
MENUITEM Language > P > Pascal                                          ; IDM_LANG_PASCAL
MENUITEM Language > P > Perl                                          ; IDM_LANG_PERL
MENUITEM Language > P > PHP                                          ; IDM_LANG_PHP
MENUITEM Language > P > PostScript                                          ; IDM_LANG_PS
MENUITEM Language > P > PowerShell                                          ; IDM_LANG_POWERSHELL
MENUITEM Language > P > Properties                                          ; IDM_LANG_PROPS
MENUITEM Language > P > Purebasic                                          ; IDM_LANG_PUREBASIC
MENUITEM Language > P > Python                                          ; IDM_LANG_PYTHON
MENUITEM Language > R > R                                          ; IDM_LANG_R
MENUITEM Language > R > Raku                                          ; IDM_LANG_RAKU
MENUITEM Language > R > REBOL                                          ; IDM_LANG_REBOL
MENUITEM Language > R > Registry                                          ; IDM_LANG_REGISTRY
MENUITEM Language > R > Resource file                                          ; IDM_LANG_RC
MENUITEM Language > R > Ruby                                          ; IDM_LANG_RUBY
MENUITEM Language > R > Rust                                          ; IDM_LANG_RUST
MENUITEM Language > S > SAS                                          ; IDM_LANG_SAS
MENUITEM Language > S > Shell                                          ; IDM_LANG_BASH
MENUITEM Language > S > Scheme                                          ; IDM_LANG_SCHEME
MENUITEM Language > S > Smalltalk                                          ; IDM_LANG_SMALLTALK
MENUITEM Language > S > Spice                                          ; IDM_LANG_SPICE
MENUITEM Language > S > SQL                                          ; IDM_LANG_SQL
MENUITEM Language > S > Swift                                          ; IDM_LANG_SWIFT
MENUITEM Language > S > S-Record                                          ; IDM_LANG_SREC
MENUITEM Language > T > TCL                                          ; IDM_LANG_TCL
MENUITEM Language > T > Tektronix extended HEX                         ; IDM_LANG_TEHEX
MENUITEM Language > T > TeX                                          ; IDM_LANG_TEX
MENUITEM Language > T > TOML                                          ; IDM_LANG_TOML
MENUITEM Language > T > txt2tags                                          ; IDM_LANG_TXT2TAGS
MENUITEM Language > T > TypeScript                                          ; IDM_LANG_TYPESCRIPT
MENUITEM Language > V > Visual Basic                                          ; IDM_LANG_VB
MENUITEM Language > V > Visual Prolog                                          ; IDM_LANG_VISUALPROLOG
MENUITEM Language > V > VHDL                                          ; IDM_LANG_VHDL
MENUITEM Language > V > Verilog                                          ; IDM_LANG_VERILOG
MENUITEM Language > XML                                          ; IDM_LANG_XML
MENUITEM Language > YAML                                          ; IDM_LANG_YAML
MENUITEM Language > User Defined Language > Define your language...                                          ; IDM_LANG_USER_DLG
MENUITEM Language > User Defined Language > Open User Defined Language folder...                                          ; IDM_LANG_OPENUDLDIR
MENUITEM Language > User Defined Language > Notepad++ User Defined Languages Collection                                          ; IDM_LANG_UDLCOLLECTION_PROJECT_SITE
MENUITEM Language > User-Defined                                          ; IDM_LANG_USER
MENUITEM Settings > Preferences...                                          ; IDM_SETTING_PREFERENCE
MENUITEM Settings > Style Configurator...                                          ; IDM_LANGSTYLE_CONFIG_DLG
MENUITEM Settings > Shortcut Mapper...                                          ; IDM_SETTING_SHORTCUT_MAPPER
MENUITEM Settings > Import > Import plugin(s)...                                          ; IDM_SETTING_IMPORTPLUGIN
MENUITEM Settings > Import > Import style theme(s)...                                          ; IDM_SETTING_IMPORTSTYLETHEMES
MENUITEM Settings > Edit Popup ContextMenu                                          ; IDM_SETTING_EDITCONTEXTMENU
MENUITEM Tools > MD5 > Generate...                                          ; IDM_TOOL_MD5_GENERATE
MENUITEM Tools > MD5 > Generate from files...                                          ; IDM_TOOL_MD5_GENERATEFROMFILE
MENUITEM Tools > MD5 > Generate from selection into clipboard                                          ; IDM_TOOL_MD5_GENERATEINTOCLIPBOARD
MENUITEM Tools > SHA-1 > Generate...                                          ; IDM_TOOL_SHA1_GENERATE
MENUITEM Tools > SHA-1 > Generate from files...                                          ; IDM_TOOL_SHA1_GENERATEFROMFILE
MENUITEM Tools > SHA-1 > Generate from selection into clipboard                                          ; IDM_TOOL_SHA1_GENERATEINTOCLIPBOARD
MENUITEM Tools > SHA-256 > Generate...                                          ; IDM_TOOL_SHA256_GENERATE
MENUITEM Tools > SHA-256 > Generate from files...                                          ; IDM_TOOL_SHA256_GENERATEFROMFILE
MENUITEM Tools > SHA-256 > Generate from selection into clipboard                                          ; IDM_TOOL_SHA256_GENERATEINTOCLIPBOARD
MENUITEM Tools > SHA-512 > Generate...                                          ; IDM_TOOL_SHA512_GENERATE
MENUITEM Tools > SHA-512 > Generate from files...                                          ; IDM_TOOL_SHA512_GENERATEFROMFILE
MENUITEM Tools > SHA-512 > Generate from selection into clipboard                                          ; IDM_TOOL_SHA512_GENERATEINTOCLIPBOARD
MENUITEM Macro > Start Recording                                          ; IDM_MACRO_STARTRECORDINGMACRO
MENUITEM Macro > Stop Recording                                          ; IDM_MACRO_STOPRECORDINGMACRO
MENUITEM Macro > Playback                                          ; IDM_MACRO_PLAYBACKRECORDEDMACRO
MENUITEM Macro > Save Current Recorded Macro...                                          ; IDM_MACRO_SAVECURRENTMACRO
MENUITEM Macro > Run a Macro Multiple Times...                                          ; IDM_MACRO_RUNMULTIMACRODLG
MENUITEM Run > Run...                                          ; IDM_EXECUTE
MENUITEM Run > Validate shortcuts.xml                                          ; IDM_EXECUTE_VALIDATE_SHORTCUTSXML
MENUITEM Plugins > Open Plugins Folder...                                          ; IDM_SETTING_OPENPLUGINSDIR
MENUITEM Window > Sort By > Name A to Z                                          ; IDM_WINDOW_SORT_FN_ASC
MENUITEM Window > Sort By > Name Z to A                                          ; IDM_WINDOW_SORT_FN_DSC
MENUITEM Window > Sort By > Path A to Z                                          ; IDM_WINDOW_SORT_FP_ASC
MENUITEM Window > Sort By > Path Z to A                                          ; IDM_WINDOW_SORT_FP_DSC
MENUITEM Window > Sort By > Type A to Z                                          ; IDM_WINDOW_SORT_FT_ASC
MENUITEM Window > Sort By > Type Z to A                                          ; IDM_WINDOW_SORT_FT_DSC
MENUITEM Window > Sort By > Content Length Ascending                                          ; IDM_WINDOW_SORT_FS_ASC
MENUITEM Window > Sort By > Content Length Descending                                          ; IDM_WINDOW_SORT_FS_DSC
MENUITEM Window > Sort By > Modified Time Ascending                                          ; IDM_WINDOW_SORT_FD_ASC
MENUITEM Window > Sort By > Modified Time Descending                                          ; IDM_WINDOW_SORT_FD_DSC
MENUITEM Window > Windows...                                          ; IDM_WINDOW_WINDOWS
MENUITEM Window > Recent Window                                          ; IDM_WINDOW_MRU_FIRST
MENUITEM ? > Command Line Arguments...                                          ; IDM_CMDLINEARGUMENTS
MENUITEM ? > Notepad++ Home                                          ; IDM_HOMESWEETHOME
MENUITEM ? > Notepad++ Project Page                                          ; IDM_PROJECTPAGE
MENUITEM ? > Notepad++ Online User Manual                                          ; IDM_ONLINEDOCUMENT
MENUITEM ? > Notepad++ Community (Forum)                                          ; IDM_FORUM
MENUITEM ? > Update Notepad++                                          ; IDM_UPDATE_NPP
MENUITEM ? > Set Updater Proxy...                                          ; IDM_CONFUPDATERPROXY
MENUITEM ? > Debug Info...                                          ; IDM_DEBUGINFO
MENUITEM ? > About Notepad++                                          ; IDM_ABOUT
MENUITEM ＋                                          ; IDM_FILE_NEW
MENUITEM ▼ > Recent Window                                          ; IDM_DROPLIST_LIST
MENUITEM ✕                                          ; IDM_FILE_CLOSE

===============================

+ IDM_FILE_NEW | File > New |
IDM_FILE_OPEN | File > Open... |
IDM_FILE_OPEN_FOLDER | File > Open Containing Folder > Explorer |
IDM_FILE_OPEN_CMD | File > Open Containing Folder > cmd |
IDM_FILE_OPEN_POWERSHELL | File > Open Containing Folder > PowerShell |
IDM_FILE_CONTAININGFOLDERASWORKSPACE | File > Open Containing Folder > Folder as Workspace |
IDM_FILE_OPEN_DEFAULT_VIEWER | File > Open in Default Viewer |
IDM_FILE_OPENFOLDERASWORKSPACE | File > Open Folder as Workspace... |
+ IDM_FILE_RELOAD | File > Reload from Disk |
+ IDM_FILE_SAVE | File > Save |
IDM_FILE_SAVEAS | File > Save As... |
IDM_FILE_SAVECOPYAS | File > Save a Copy As... |
+ IDM_FILE_SAVEALL | File > Save All |
IDM_FILE_RENAME | File > Rename... |
+ IDM_FILE_CLOSE | File > Close |
+ IDM_FILE_CLOSEALL | File > Close All |
+ IDM_FILE_CLOSEALL_BUT_CURRENT | File > Close Multiple Documents > Close All but Active Document |
+ IDM_FILE_CLOSEALL_BUT_PINNED | File > Close Multiple Documents > Close All but Pinned Documents |
+ IDM_FILE_CLOSEALL_TOLEFT | File > Close Multiple Documents > Close All to the Left |
+ IDM_FILE_CLOSEALL_TORIGHT | File > Close Multiple Documents > Close All to the Right |
+ IDM_FILE_CLOSEALL_UNCHANGED | File > Close Multiple Documents > Close All Unchanged |
IDM_FILE_DELETE | File > Move to Recycle Bin |
IDM_FILE_LOADSESSION | File > Load Session... |
IDM_FILE_SAVESESSION | File > Save Session... |
IDM_FILE_PRINT | File > Print... |
IDM_FILE_PRINTNOW | File > Print Now |
IDM_FILE_EXIT | File > Exit |
+ IDM_EDIT_UNDO | Edit > Undo |
+ IDM_EDIT_REDO | Edit > Redo |
+ IDM_EDIT_CUT | Edit > Cut |
+ IDM_EDIT_COPY | Edit > Copy |
+ IDM_EDIT_PASTE | Edit > Paste |
+ IDM_EDIT_DELETE | Edit > Delete |
+ IDM_EDIT_SELECTALL | Edit > Select All |
+ IDM_EDIT_BEGINENDSELECT | Edit > Begin/End Select |
+ IDM_EDIT_BEGINENDSELECT_COLUMNMODE | Edit > Begin/End Select in Column Mode |
+ IDM_EDIT_INSERT_DATETIME_SHORT | Edit > Insert > Date Time (short) |
+ IDM_EDIT_INSERT_DATETIME_LONG | Edit > Insert > Date Time (long) |
+ IDM_EDIT_INSERT_DATETIME_CUSTOMIZED | Edit > Insert > Date Time (customized) |
+ IDM_EDIT_FULLPATHTOCLIP | Edit > Copy to Clipboard > Copy Current Full File path |
+ IDM_EDIT_FILENAMETOCLIP | Edit > Copy to Clipboard > Copy Current Filename |
+ IDM_EDIT_CURRENTDIRTOCLIP | Edit > Copy to Clipboard > Copy Current Dir. Path |
+ IDM_EDIT_COPY_ALL_NAMES | Edit > Copy to Clipboard > Copy All Filenames |
+ IDM_EDIT_COPY_ALL_PATHS | Edit > Copy to Clipboard > Copy All File Paths |
+ IDM_EDIT_INS_TAB | Edit > Indent > Increase Line Indent |
+ IDM_EDIT_RMV_TAB | Edit > Indent > Decrease Line Indent |
+ IDM_EDIT_UPPERCASE | Edit > Convert Case to > UPPERCASE |
+ IDM_EDIT_LOWERCASE | Edit > Convert Case to > lowercase |
+ IDM_EDIT_PROPERCASE_FORCE | Edit > Convert Case to > Proper Case |
+ IDM_EDIT_PROPERCASE_BLEND | Edit > Convert Case to > Proper Case (blend) |
+ IDM_EDIT_SENTENCECASE_FORCE | Edit > Convert Case to > Sentence case |
+ IDM_EDIT_SENTENCECASE_BLEND | Edit > Convert Case to > Sentence case (blend) |
+ IDM_EDIT_INVERTCASE | Edit > Convert Case to > iNVERT cASE |
+ IDM_EDIT_RANDOMCASE | Edit > Convert Case to > ranDOm CasE |
+ IDM_EDIT_DUP_LINE | Edit > Line Operations > Duplicate Current Line |
+ IDM_EDIT_REMOVE_ANY_DUP_LINES | Edit > Line Operations > Remove Duplicate Lines |
+ IDM_EDIT_REMOVE_CONSECUTIVE_DUP_LINES | Edit > Line Operations > Remove Consecutive Duplicate Lines |
+ IDM_EDIT_SPLIT_LINES | Edit > Line Operations > Split Lines |
+ IDM_EDIT_JOIN_LINES | Edit > Line Operations > Join Lines |
+ IDM_EDIT_LINE_UP | Edit > Line Operations > Move Up Current Line |
+ IDM_EDIT_LINE_DOWN | Edit > Line Operations > Move Down Current Line |
+ IDM_EDIT_REMOVEEMPTYLINES | Edit > Line Operations > Remove Empty Lines |
+ IDM_EDIT_REMOVEEMPTYLINESWITHBLANK | Edit > Line Operations > Remove Empty Lines (Containing Blank characters) |
+ IDM_EDIT_BLANKLINEABOVECURRENT | Edit > Line Operations > Insert Blank Line Above Current |
+ IDM_EDIT_BLANKLINEBELOWCURRENT | Edit > Line Operations > Insert Blank Line Below Current |
+ IDM_EDIT_SORTLINES_REVERSE_ORDER | Edit > Line Operations > Reverse Line Order |
+ IDM_EDIT_SORTLINES_RANDOMLY | Edit > Line Operations > Randomize Line Order |
+ IDM_EDIT_SORTLINES_LEXICOGRAPHIC_ASCENDING | Edit > Line Operations > Sort Lines Lexicographically Ascending |
+ IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_ASCENDING | Edit > Line Operations > Sort Lines Lex. Ascending Ignoring Case |
+ IDM_EDIT_SORTLINES_LOCALE_ASCENDING | Edit > Line Operations > Sort Lines In Locale Order Ascending |
+ IDM_EDIT_SORTLINES_INTEGER_ASCENDING | Edit > Line Operations > Sort Lines As Integers Ascending |
+ IDM_EDIT_SORTLINES_DECIMALCOMMA_ASCENDING | Edit > Line Operations > Sort Lines As Decimals (Comma) Ascending |
+ IDM_EDIT_SORTLINES_DECIMALDOT_ASCENDING | Edit > Line Operations > Sort Lines As Decimals (Dot) Ascending |
+ IDM_EDIT_SORTLINES_LENGTH_ASCENDING | Edit > Line Operations > Sort Lines By Length Ascending |
+ IDM_EDIT_SORTLINES_LEXICOGRAPHIC_DESCENDING | Edit > Line Operations > Sort Lines Lexicographically Descending |
+ IDM_EDIT_SORTLINES_LEXICO_CASE_INSENS_DESCENDING | Edit > Line Operations > Sort Lines Lex. Descending Ignoring Case |
+ IDM_EDIT_SORTLINES_LOCALE_DESCENDING | Edit > Line Operations > Sort Lines In Locale Order Descending |
+ IDM_EDIT_SORTLINES_INTEGER_DESCENDING | Edit > Line Operations > Sort Lines As Integers Descending |
+ IDM_EDIT_SORTLINES_DECIMALCOMMA_DESCENDING | Edit > Line Operations > Sort Lines As Decimals (Comma) Descending |
+ IDM_EDIT_SORTLINES_DECIMALDOT_DESCENDING | Edit > Line Operations > Sort Lines As Decimals (Dot) Descending |
+ IDM_EDIT_SORTLINES_LENGTH_DESCENDING | Edit > Line Operations > Sort Lines By Length Descending |
+ IDM_EDIT_BLOCK_COMMENT | Edit > Comment/Uncomment > Toggle Single Line Comment |
+ IDM_EDIT_BLOCK_COMMENT_SET | Edit > Comment/Uncomment > Single Line Comment |
+ IDM_EDIT_BLOCK_UNCOMMENT | Edit > Comment/Uncomment > Single Line Uncomment |
+ IDM_EDIT_STREAM_COMMENT | Edit > Comment/Uncomment > Block Comment |
IDM_EDIT_STREAM_UNCOMMENT | Edit > Comment/Uncomment > Block Uncomment |
IDM_EDIT_AUTOCOMPLETE | Edit > Auto-Completion > Function Completion |
IDM_EDIT_AUTOCOMPLETE_CURRENTFILE | Edit > Auto-Completion > Word Completion |
IDM_EDIT_FUNCCALLTIP | Edit > Auto-Completion > Function Parameters Hint |
IDM_EDIT_FUNCCALLTIP_PREVIOUS | Edit > Auto-Completion > Function Parameters Previous Hint |
IDM_EDIT_FUNCCALLTIP_NEXT | Edit > Auto-Completion > Function Parameters Next Hint |
IDM_EDIT_AUTOCOMPLETE_PATH | Edit > Auto-Completion > Path Completion |
+ IDM_FORMAT_TODOS | Edit > EOL Conversion > Windows (CR LF) |
+ IDM_FORMAT_TOUNIX | Edit > EOL Conversion > Unix (LF) |
+ IDM_FORMAT_TOMAC | Edit > EOL Conversion > Macintosh (CR) |
+ IDM_EDIT_TRIMTRAILING | Edit > Blank Operations > Trim Trailing Space |
+ IDM_EDIT_TRIMLINEHEAD | Edit > Blank Operations > Trim Leading Space |
+ IDM_EDIT_TRIM_BOTH | Edit > Blank Operations > Trim Leading and Trailing Space |
+ IDM_EDIT_EOL2WS | Edit > Blank Operations > EOL to Space |
+ IDM_EDIT_TRIMALL | Edit > Blank Operations > Trim both and EOL to Space |
+ IDM_EDIT_TAB2SW | Edit > Blank Operations > TAB to Space |
+ IDM_EDIT_SW2TAB_ALL | Edit > Blank Operations > Space to TAB (All) |
+ IDM_EDIT_SW2TAB_LEADING | Edit > Blank Operations > Space to TAB (Leading) |
IDM_EDIT_PASTE_AS_HTML | Edit > Paste Special > Paste HTML Content |
IDM_EDIT_PASTE_AS_RTF | Edit > Paste Special > Paste RTF Content |
IDM_EDIT_COPY_BINARY | Edit > Paste Special > Copy Binary Content |
IDM_EDIT_CUT_BINARY | Edit > Paste Special > Cut Binary Content |
IDM_EDIT_PASTE_BINARY | Edit > Paste Special > Paste Binary Content |
IDM_EDIT_OPENSELECTEDFILETOEDIT | Edit > On Selection > Open File |
IDM_EDIT_OPENSELECTEDFILEFOLDERINEXPLORER | Edit > On Selection > Open Containing Folder in Explorer |
+ IDM_EDIT_REDACT_SELECTION | Edit > On Selection > Redact Selection █ (Shift: ●) |
IDM_EDIT_SEARCHONINTERNET | Edit > On Selection > Search on Internet |
IDM_EDIT_CHANGESEARCHENGINE | Edit > On Selection > Change Search Engine... |
IDM_EDIT_MULTISELECTALL | Edit > Multi-select All > Ignore Case  Whole Word |
IDM_EDIT_MULTISELECTALLMATCHCASE | Edit > Multi-select All > Match Case Only |
+ IDM_EDIT_MULTISELECTALLWHOLEWORD | Edit > Multi-select All > Match Whole Word Only |
+ IDM_EDIT_MULTISELECTALLMATCHCASEWHOLEWORD | Edit > Multi-select All > Match Case  Whole Word |
+ IDM_EDIT_MULTISELECTNEXT | Edit > Multi-select Next > Ignore Case  Whole Word |
+ IDM_EDIT_MULTISELECTNEXTMATCHCASE | Edit > Multi-select Next > Match Case Only |
+ IDM_EDIT_MULTISELECTNEXTWHOLEWORD | Edit > Multi-select Next > Match Whole Word Only |
+ IDM_EDIT_MULTISELECTNEXTMATCHCASEWHOLEWORD | Edit > Multi-select Next > Match Case  Whole Word |
+ IDM_EDIT_MULTISELECTUNDO | Edit > Undo the Latest Added Multi-Select |
+ IDM_EDIT_MULTISELECTSSKIP | Edit > Skip Current  Go to Next Multi-select |
IDM_EDIT_COLUMNMODETIP | Edit > Column Mode... |
IDM_EDIT_COLUMNMODE | Edit > Column Editor... |
IDM_EDIT_CHAR_PANEL | Edit > Character Panel |
IDM_EDIT_CLIPBOARDHISTORY_PANEL | Edit > Clipboard History |
+ IDM_EDIT_TOGGLEREADONLY | Edit > Read-Only in Notepad++ > Read-Only on Current Document |
+ IDM_EDIT_SETREADONLYFORALLDOCS | Edit > Read-Only in Notepad++ > Read-Only for All Documents |
+ IDM_EDIT_CLEARREADONLYFORALLDOCS | Edit > Read-Only in Notepad++ > Clear Read-Only for All Documents |
+ IDM_EDIT_TOGGLESYSTEMREADONLY | Edit > Read-Only Attribute in Windows |
IDM_SEARCH_FIND | Search > Find... |
IDM_SEARCH_FINDINFILES | Search > Find in Files... |
+ IDM_SEARCH_FINDNEXT | Search > Find Next |
+ IDM_SEARCH_FINDPREV | Search > Find Previous |
+ IDM_SEARCH_SETANDFINDNEXT | Search > Select and Find Next |
+ IDM_SEARCH_SETANDFINDPREV | Search > Select and Find Previous |
+ IDM_SEARCH_VOLATILE_FINDNEXT | Search > Find (Volatile) Next |
+ IDM_SEARCH_VOLATILE_FINDPREV | Search > Find (Volatile) Previous |
IDM_SEARCH_REPLACE | Search > Replace... |
IDM_SEARCH_FINDINCREMENT | Search > Incremental Search |
IDM_FOCUS_ON_FOUND_RESULTS | Search > Search Results Window |
IDM_SEARCH_GOTONEXTFOUND | Search > Next Search Result |
IDM_SEARCH_GOTOPREVFOUND | Search > Previous Search Result |
IDM_SEARCH_GOTOLINE | Search > Go to... |
+ IDM_SEARCH_GOTOMATCHINGBRACE | Search > Go to Matching Brace |
+ IDM_SEARCH_SELECTMATCHINGBRACES | Search > Select All In-between {} [] or () |
IDM_SEARCH_MARK | Search > Mark... |
IDM_SEARCH_CHANGED_NEXT | Search > Change History > Go to Next Change |
IDM_SEARCH_CHANGED_PREV | Search > Change History > Go to Previous Change |
IDM_SEARCH_CLEAR_CHANGE_HISTORY | Search > Change History > Clear Change History |
+ IDM_SEARCH_MARKALLEXT1 | Search > Style All Occurrences of Token > Using 1st Style |
+ IDM_SEARCH_MARKALLEXT2 | Search > Style All Occurrences of Token > Using 2nd Style |
+ IDM_SEARCH_MARKALLEXT3 | Search > Style All Occurrences of Token > Using 3rd Style |
+ IDM_SEARCH_MARKALLEXT4 | Search > Style All Occurrences of Token > Using 4th Style |
+ IDM_SEARCH_MARKALLEXT5 | Search > Style All Occurrences of Token > Using 5th Style |
+ IDM_SEARCH_MARKONEEXT1 | Search > Style One Token > Using 1st Style |
+ IDM_SEARCH_MARKONEEXT2 | Search > Style One Token > Using 2nd Style |
+ IDM_SEARCH_MARKONEEXT3 | Search > Style One Token > Using 3rd Style |
+ IDM_SEARCH_MARKONEEXT4 | Search > Style One Token > Using 4th Style |
+ IDM_SEARCH_MARKONEEXT5 | Search > Style One Token > Using 5th Style |
+ IDM_SEARCH_UNMARKALLEXT1 | Search > Clear Style > Clear 1st Style |
+ IDM_SEARCH_UNMARKALLEXT2 | Search > Clear Style > Clear 2nd Style |
+ IDM_SEARCH_UNMARKALLEXT3 | Search > Clear Style > Clear 3rd Style |
+ IDM_SEARCH_UNMARKALLEXT4 | Search > Clear Style > Clear 4th Style |
+ IDM_SEARCH_UNMARKALLEXT5 | Search > Clear Style > Clear 5th Style |
+ IDM_SEARCH_CLEARALLMARKS | Search > Clear Style > Clear all Styles |
+ IDM_SEARCH_GOPREVMARKER1 | Search > Jump Up > 1st Style |
+ IDM_SEARCH_GOPREVMARKER2 | Search > Jump Up > 2nd Style |
+ IDM_SEARCH_GOPREVMARKER3 | Search > Jump Up > 3rd Style |
+ IDM_SEARCH_GOPREVMARKER4 | Search > Jump Up > 4th Style |
+ IDM_SEARCH_GOPREVMARKER5 | Search > Jump Up > 5th Style |
+ IDM_SEARCH_GOPREVMARKER_DEF | Search > Jump Up > Find Mark Style |
+ IDM_SEARCH_GONEXTMARKER1 | Search > Jump Down > 1st Style |
+ IDM_SEARCH_GONEXTMARKER2 | Search > Jump Down > 2nd Style |
+ IDM_SEARCH_GONEXTMARKER3 | Search > Jump Down > 3rd Style |
+ IDM_SEARCH_GONEXTMARKER4 | Search > Jump Down > 4th Style |
+ IDM_SEARCH_GONEXTMARKER5 | Search > Jump Down > 5th Style |
+ IDM_SEARCH_GONEXTMARKER_DEF | Search > Jump Down > Find Mark Style |
+ IDM_SEARCH_STYLE1TOCLIP | Search > Copy Styled Text > 1st Style |
+ IDM_SEARCH_STYLE2TOCLIP | Search > Copy Styled Text > 2nd Style |
+ IDM_SEARCH_STYLE3TOCLIP | Search > Copy Styled Text > 3rd Style |
+ IDM_SEARCH_STYLE4TOCLIP | Search > Copy Styled Text > 4th Style |
+ IDM_SEARCH_STYLE5TOCLIP | Search > Copy Styled Text > 5th Style |
+ IDM_SEARCH_ALLSTYLESTOCLIP | Search > Copy Styled Text > All Styles |
+ IDM_SEARCH_MARKEDTOCLIP | Search > Copy Styled Text > Find Mark Style |
+ IDM_SEARCH_TOGGLE_BOOKMARK | Search > Bookmark > Toggle Bookmark |
+ IDM_SEARCH_NEXT_BOOKMARK | Search > Bookmark > Next Bookmark |
+ IDM_SEARCH_PREV_BOOKMARK | Search > Bookmark > Previous Bookmark |
+ IDM_SEARCH_CLEAR_BOOKMARKS | Search > Bookmark > Clear All Bookmarks |
+ IDM_SEARCH_CUTMARKEDLINES | Search > Bookmark > Cut Bookmarked Lines |
+ IDM_SEARCH_COPYMARKEDLINES | Search > Bookmark > Copy Bookmarked Lines |
+ IDM_SEARCH_PASTEMARKEDLINES | Search > Bookmark > Paste to (Replace) Bookmarked Lines |
+ IDM_SEARCH_DELETEMARKEDLINES | Search > Bookmark > Remove Bookmarked Lines |
+ IDM_SEARCH_DELETEUNMARKEDLINES | Search > Bookmark > Remove Non-Bookmarked Lines |
+ IDM_SEARCH_INVERSEMARKS | Search > Bookmark > Inverse Bookmarks |
IDM_SEARCH_FINDCHARINRANGE | Search > Find characters in range... |
+ IDM_VIEW_ALWAYSONTOP | View > Always on Top |
+ IDM_VIEW_FULLSCREENTOGGLE | View > Toggle Full Screen Mode |
IDM_VIEW_POSTIT | View > Post-It |
IDM_VIEW_DISTRACTIONFREE | View > Distraction Free Mode |
+ IDM_VIEW_IN_FIREFOX | View > View Current File in > Firefox |
+ IDM_VIEW_IN_CHROME | View > View Current File in > Chrome |
+ IDM_VIEW_IN_EDGE | View > View Current File in > Edge |
+ IDM_VIEW_IN_IE | View > View Current File in > IE |
IDM_VIEW_TAB_SPACE | View > Show Symbol > Show Space and Tab |
IDM_VIEW_EOL | View > Show Symbol > Show End of Line |
IDM_VIEW_NPC | View > Show Symbol > Show Non-Printing Characters |
IDM_VIEW_NPC_CCUNIEOL | View > Show Symbol > Show Control Characters  Unicode EOL |
IDM_VIEW_ALL_CHARACTERS | View > Show Symbol > Show All Characters |
IDM_VIEW_INDENT_GUIDE | View > Show Symbol > Show Indent Guide |
IDM_VIEW_WRAP_SYMBOL | View > Show Symbol > Show Wrap Symbol |
IDM_VIEW_ZOOMIN | View > Zoom > Zoom In (Ctrl+Mouse Wheel Up) |
IDM_VIEW_ZOOMOUT | View > Zoom > Zoom Out (Ctrl+Mouse Wheel Down) |
IDM_VIEW_ZOOMRESTORE | View > Zoom > Restore Default Zoom |
IDM_VIEW_ZOOM_SYNC | View > Zoom > Synchronize Across Views |
+ IDM_VIEW_GOTO_ANOTHER_VIEW | View > Move/Clone Current Document > Move to Other View |
+ IDM_VIEW_CLONE_TO_ANOTHER_VIEW | View > Move/Clone Current Document > Clone to Other View |
+ IDM_VIEW_GOTO_NEW_INSTANCE | View > Move/Clone Current Document > Move to New Instance |
+ IDM_VIEW_LOAD_IN_NEW_INSTANCE | View > Move/Clone Current Document > Open in New Instance |
+ IDM_VIEW_TAB1 | View > Tab > 1st Tab |
+ IDM_VIEW_TAB2 | View > Tab > 2nd Tab |
+ IDM_VIEW_TAB3 | View > Tab > 3rd Tab |
+ IDM_VIEW_TAB4 | View > Tab > 4th Tab |
+ IDM_VIEW_TAB5 | View > Tab > 5th Tab |
+ IDM_VIEW_TAB6 | View > Tab > 6th Tab |
+ IDM_VIEW_TAB7 | View > Tab > 7th Tab |
+ IDM_VIEW_TAB8 | View > Tab > 8th Tab |
+ IDM_VIEW_TAB9 | View > Tab > 9th Tab |
IDM_VIEW_TAB_START | View > Tab > First Tab |
IDM_VIEW_TAB_END | View > Tab > Last Tab |
+ IDM_VIEW_TAB_NEXT | View > Tab > Next Tab |
+ IDM_VIEW_TAB_PREV | View > Tab > Previous Tab |
+ IDM_VIEW_GOTO_START | View > Tab > Move to Start |
+ IDM_VIEW_GOTO_END | View > Tab > Move to End |
+ IDM_VIEW_TAB_MOVEFORWARD | View > Tab > Move Tab Forward |
+ IDM_VIEW_TAB_MOVEBACKWARD | View > Tab > Move Tab Backward |
IDM_VIEW_TAB_COLOUR_1 | View > Tab > Apply Color 1 |
IDM_VIEW_TAB_COLOUR_2 | View > Tab > Apply Color 2 |
IDM_VIEW_TAB_COLOUR_3 | View > Tab > Apply Color 3 |
IDM_VIEW_TAB_COLOUR_4 | View > Tab > Apply Color 4 |
IDM_VIEW_TAB_COLOUR_5 | View > Tab > Apply Color 5 |
IDM_VIEW_TAB_COLOUR_NONE | View > Tab > Remove Color |
+ IDM_VIEW_WRAP | View > Word wrap |
IDM_VIEW_SWITCHTO_OTHER_VIEW | View > Focus on Another View |
IDM_VIEW_HIDELINES | View > Hide Lines |
+ IDM_VIEW_FOLDALL | View > Fold All |
+ IDM_VIEW_UNFOLDALL | View > Unfold All |
+ IDM_VIEW_FOLD_CURRENT | View > Fold Current Level |
+ IDM_VIEW_UNFOLD_CURRENT | View > Unfold Current Level |
+ IDM_VIEW_FOLD_1 | View > Fold Level > 1 |
+ IDM_VIEW_FOLD_2 | View > Fold Level > 2 |
+ IDM_VIEW_FOLD_3 | View > Fold Level > 3 |
+ IDM_VIEW_FOLD_4 | View > Fold Level > 4 |
+ IDM_VIEW_FOLD_5 | View > Fold Level > 5 |
+ IDM_VIEW_FOLD_6 | View > Fold Level > 6 |
+ IDM_VIEW_FOLD_7 | View > Fold Level > 7 |
+ IDM_VIEW_FOLD_8 | View > Fold Level > 8 |
+ IDM_VIEW_UNFOLD_1 | View > Unfold Level > 1 |
+ IDM_VIEW_UNFOLD_2 | View > Unfold Level > 2 |
+ IDM_VIEW_UNFOLD_3 | View > Unfold Level > 3 |
+ IDM_VIEW_UNFOLD_4 | View > Unfold Level > 4 |
+ IDM_VIEW_UNFOLD_5 | View > Unfold Level > 5 |
+ IDM_VIEW_UNFOLD_6 | View > Unfold Level > 6 |
+ IDM_VIEW_UNFOLD_7 | View > Unfold Level > 7 |
+ IDM_VIEW_UNFOLD_8 | View > Unfold Level > 8 |
IDM_VIEW_SUMMARY | View > Summary... |
IDM_VIEW_PROJECT_PANEL_1 | View > Project Panels > Project Panel 1 |
IDM_VIEW_PROJECT_PANEL_2 | View > Project Panels > Project Panel 2 |
IDM_VIEW_PROJECT_PANEL_3 | View > Project Panels > Project Panel 3 |
IDM_VIEW_FILEBROWSER | View > Folder as Workspace |
IDM_VIEW_DOC_MAP | View > Document Map |
IDM_VIEW_DOCLIST | View > Document List |
IDM_VIEW_FUNC_LIST | View > Function List |
+ IDM_VIEW_SYNSCROLLV | View > Synchronize Vertical Scrolling |
+ IDM_VIEW_SYNSCROLLH | View > Synchronize Horizontal Scrolling |
+ IDM_EDIT_RTL | View > Text Direction RTL |
+ IDM_EDIT_LTR | View > Text Direction LTR |
IDM_VIEW_MONITORING | View > Monitoring (tail -f) |
IDM_FORMAT_ANSI | Encoding > ANSI |
IDM_FORMAT_AS_UTF_8 | Encoding > UTF-8 |
IDM_FORMAT_UTF_8 | Encoding > UTF-8-BOM |
IDM_FORMAT_UTF_16BE | Encoding > UTF-16 BE BOM |
IDM_FORMAT_UTF_16LE | Encoding > UTF-16 LE BOM |
IDM_FORMAT_ISO_8859_6 | Encoding > Character sets > Arabic > ISO 8859-6 |
IDM_FORMAT_DOS_720 | Encoding > Character sets > Arabic > OEM 720 |
IDM_FORMAT_WIN_1256 | Encoding > Character sets > Arabic > Windows-1256 |
IDM_FORMAT_ISO_8859_4 | Encoding > Character sets > Baltic > ISO 8859-4 |
IDM_FORMAT_ISO_8859_13 | Encoding > Character sets > Baltic > ISO 8859-13 |
IDM_FORMAT_DOS_775 | Encoding > Character sets > Baltic > OEM 775 |
IDM_FORMAT_WIN_1257 | Encoding > Character sets > Baltic > Windows-1257 |
IDM_FORMAT_ISO_8859_14 | Encoding > Character sets > Celtic > ISO 8859-14 |
IDM_FORMAT_ISO_8859_5 | Encoding > Character sets > Cyrillic > ISO 8859-5 |
IDM_FORMAT_KOI8R_CYRILLIC | Encoding > Character sets > Cyrillic > KOI8-R |
IDM_FORMAT_KOI8U_CYRILLIC | Encoding > Character sets > Cyrillic > KOI8-U |
IDM_FORMAT_MAC_CYRILLIC | Encoding > Character sets > Cyrillic > Macintosh |
IDM_FORMAT_DOS_855 | Encoding > Character sets > Cyrillic > OEM 855 |
IDM_FORMAT_DOS_866 | Encoding > Character sets > Cyrillic > OEM 866 |
IDM_FORMAT_WIN_1251 | Encoding > Character sets > Cyrillic > Windows-1251 |
IDM_FORMAT_DOS_852 | Encoding > Character sets > Central European > OEM 852 |
IDM_FORMAT_WIN_1250 | Encoding > Character sets > Central European > Windows-1250 |
IDM_FORMAT_BIG5 | Encoding > Character sets > Chinese > Big5 (Traditional) |
IDM_FORMAT_GB2312 | Encoding > Character sets > Chinese > GB2312 (Simplified) |
IDM_FORMAT_ISO_8859_2 | Encoding > Character sets > Eastern European > ISO 8859-2 |
IDM_FORMAT_ISO_8859_7 | Encoding > Character sets > Greek > ISO 8859-7 |
IDM_FORMAT_DOS_737 | Encoding > Character sets > Greek > OEM 737 |
IDM_FORMAT_DOS_869 | Encoding > Character sets > Greek > OEM 869 |
IDM_FORMAT_WIN_1253 | Encoding > Character sets > Greek > Windows-1253 |
IDM_FORMAT_ISO_8859_8 | Encoding > Character sets > Hebrew > ISO 8859-8 |
IDM_FORMAT_DOS_862 | Encoding > Character sets > Hebrew > OEM 862 |
IDM_FORMAT_WIN_1255 | Encoding > Character sets > Hebrew > Windows-1255 |
IDM_FORMAT_SHIFT_JIS | Encoding > Character sets > Japanese > Shift-JIS |
IDM_FORMAT_KOREAN_WIN | Encoding > Character sets > Korean > Windows 949 |
IDM_FORMAT_EUC_KR | Encoding > Character sets > Korean > EUC-KR |
IDM_FORMAT_DOS_861 | Encoding > Character sets > North European > OEM 861 : Icelandic |
IDM_FORMAT_DOS_865 | Encoding > Character sets > North European > OEM 865 : Nordic |
IDM_FORMAT_TIS_620 | Encoding > Character sets > Thai > TIS-620 |
IDM_FORMAT_ISO_8859_3 | Encoding > Character sets > Turkish > ISO 8859-3 |
IDM_FORMAT_ISO_8859_9 | Encoding > Character sets > Turkish > ISO 8859-9 |
IDM_FORMAT_DOS_857 | Encoding > Character sets > Turkish > OEM 857 |
IDM_FORMAT_WIN_1254 | Encoding > Character sets > Turkish > Windows-1254 |
IDM_FORMAT_ISO_8859_1 | Encoding > Character sets > Western European > ISO 8859-1 |
IDM_FORMAT_ISO_8859_10 | Encoding > Character sets > Western European > ISO 8859-10 |
IDM_FORMAT_ISO_8859_15 | Encoding > Character sets > Western European > ISO 8859-15 |
IDM_FORMAT_DOS_850 | Encoding > Character sets > Western European > OEM 850 |
IDM_FORMAT_DOS_858 | Encoding > Character sets > Western European > OEM 858 |
IDM_FORMAT_DOS_860 | Encoding > Character sets > Western European > OEM 860 : Portuguese |
IDM_FORMAT_DOS_863 | Encoding > Character sets > Western European > OEM 863 : French |
IDM_FORMAT_DOS_437 | Encoding > Character sets > Western European > OEM-US |
IDM_FORMAT_WIN_1252 | Encoding > Character sets > Western European > Windows-1252 |
IDM_FORMAT_WIN_1258 | Encoding > Character sets > Vietnamese > Windows-1258 |
IDM_FORMAT_CONV2_ANSI | Encoding > Convert to ANSI |
IDM_FORMAT_CONV2_AS_UTF_8 | Encoding > Convert to UTF-8 |
IDM_FORMAT_CONV2_UTF_8 | Encoding > Convert to UTF-8-BOM |
IDM_FORMAT_CONV2_UTF_16BE | Encoding > Convert to UTF-16 BE BOM |
IDM_FORMAT_CONV2_UTF_16LE | Encoding > Convert to UTF-16 LE BOM |
IDM_LANG_TEXT | Language > None (Normal Text) |
IDM_LANG_FLASH | Language > ActionScript |
IDM_LANG_ADA | Language > Ada |
IDM_LANG_ASN1 | Language > ASN.1 |
IDM_LANG_ASP | Language > ASP |
IDM_LANG_ASM | Language > Assembly |
IDM_LANG_AU3 | Language > AutoIt |
IDM_LANG_AVS | Language > AviSynth |
IDM_LANG_BAANC | Language > BaanC |
IDM_LANG_BATCH | Language > Batch |
IDM_LANG_BLITZBASIC | Language > Blitzbasic |
IDM_LANG_C | Language > C |
IDM_LANG_CS | Language > C# |
IDM_LANG_CPP | Language > C++ |
IDM_LANG_CAML | Language > Caml |
IDM_LANG_CMAKE | Language > CMake |
IDM_LANG_COBOL | Language > COBOL |
IDM_LANG_CSOUND | Language > CSound |
IDM_LANG_COFFEESCRIPT | Language > CoffeeScript |
IDM_LANG_CSS | Language > CSS |
IDM_LANG_D | Language > D |
IDM_LANG_DIFF | Language > Diff |
IDM_LANG_ERLANG | Language > Erlang |
IDM_LANG_ERRORLIST | Language > ErrorList |
IDM_LANG_ESCSEQ | Language > Escape Sequence (ANSI) |
IDM_LANG_ESCRIPT | Language > ESCRIPT |
IDM_LANG_FORTH | Language > Forth |
IDM_LANG_FORTRAN | Language > Fortran (free form) |
IDM_LANG_FORTRAN_77 | Language > Fortran (fixed form) |
IDM_LANG_FREEBASIC | Language > Freebasic |
IDM_LANG_GDSCRIPT | Language > GDScript |
IDM_LANG_GOLANG | Language > Go |
IDM_LANG_GUI4CLI | Language > Gui4Cli |
IDM_LANG_HASKELL | Language > Haskell |
IDM_LANG_HOLLYWOOD | Language > Hollywood |
IDM_LANG_HTML | Language > HTML |
IDM_LANG_INI | Language > INI file |
IDM_LANG_INNO | Language > Inno Setup |
IDM_LANG_IHEX | Language > Intel HEX |
IDM_LANG_JAVA | Language > Java |
IDM_LANG_JS | Language > JavaScript |
IDM_LANG_JSON | Language > JSON |
IDM_LANG_JSON5 | Language > JSON5 |
IDM_LANG_JSP | Language > JSP |
IDM_LANG_KIX | Language > KIXtart |
IDM_LANG_LISP | Language > LISP |
IDM_LANG_LATEX | Language > LaTeX |
IDM_LANG_LUA | Language > Lua |
IDM_LANG_MAKEFILE | Language > Makefile |
IDM_LANG_MATLAB | Language > Matlab |
IDM_LANG_MSSQL | Language > Microsoft Transact-SQL |
IDM_LANG_MMIXAL | Language > MMIXAL |
IDM_LANG_ASCII | Language > MS-DOS Style |
IDM_LANG_NIM | Language > Nim |
IDM_LANG_NNCRONTAB | Language > Nncrontab |
IDM_LANG_NSIS | Language > NSIS |
IDM_LANG_OBJC | Language > Objective-C |
IDM_LANG_OSCRIPT | Language > OScript |
IDM_LANG_PASCAL | Language > Pascal |
IDM_LANG_PERL | Language > Perl |
IDM_LANG_PHP | Language > PHP |
IDM_LANG_PS | Language > PostScript |
IDM_LANG_POWERSHELL | Language > PowerShell |
IDM_LANG_PROPS | Language > Properties |
IDM_LANG_PUREBASIC | Language > Purebasic |
IDM_LANG_PYTHON | Language > Python |
IDM_LANG_R | Language > R |
IDM_LANG_RAKU | Language > Raku |
IDM_LANG_REBOL | Language > REBOL |
IDM_LANG_REGISTRY | Language > Registry |
IDM_LANG_RC | Language > Resource file |
IDM_LANG_RUBY | Language > Ruby |
IDM_LANG_RUST | Language > Rust |
IDM_LANG_SAS | Language > SAS |
IDM_LANG_BASH | Language > Shell |
IDM_LANG_SCHEME | Language > Scheme |
IDM_LANG_SMALLTALK | Language > Smalltalk |
IDM_LANG_SPICE | Language > Spice |
IDM_LANG_SQL | Language > SQL |
IDM_LANG_SWIFT | Language > Swift |
IDM_LANG_SREC | Language > S-Record |
IDM_LANG_TCL | Language > TCL |
IDM_LANG_TEHEX | Language > Tektronix extended HEX |
IDM_LANG_TEX | Language > TeX |
IDM_LANG_TOML | Language > TOML |
IDM_LANG_TXT2TAGS | Language > txt2tags |
IDM_LANG_TYPESCRIPT | Language > TypeScript |
IDM_LANG_VERILOG | Language > Verilog |
IDM_LANG_VHDL | Language > VHDL |
IDM_LANG_VB | Language > Visual Basic |
IDM_LANG_VISUALPROLOG | Language > Visual Prolog |
IDM_LANG_XML | Language > XML |
IDM_LANG_YAML | Language > YAML |
IDM_LANG_USER_DLG | Language > Define your language... |
IDM_LANG_OPENUDLDIR | Language > Open User Defined Language folder... |
IDM_LANG_UDLCOLLECTION_PROJECT_SITE | Language > Notepad++ User Defined Languages Collection |
IDM_LANG_USER | Language > User-Defined |
IDM_LANG_TEXT | Language > None (Normal Text) |
IDM_LANG_FLASH | Language > A > ActionScript |
IDM_LANG_ADA | Language > A > Ada |
IDM_LANG_ASN1 | Language > A > ASN.1 |
IDM_LANG_ASP | Language > A > ASP |
IDM_LANG_ASM | Language > A > Assembly |
IDM_LANG_AU3 | Language > A > AutoIt |
IDM_LANG_AVS | Language > A > AviSynth |
IDM_LANG_BAANC | Language > B > BaanC |
IDM_LANG_BATCH | Language > B > Batch |
IDM_LANG_BLITZBASIC | Language > B > Blitzbasic |
IDM_LANG_C | Language > C > C |
IDM_LANG_CS | Language > C > C# |
IDM_LANG_CPP | Language > C > C++ |
IDM_LANG_CAML | Language > C > Caml |
IDM_LANG_CMAKE | Language > C > CMake |
IDM_LANG_COBOL | Language > C > COBOL |
IDM_LANG_CSOUND | Language > C > CSound |
IDM_LANG_COFFEESCRIPT | Language > C > CoffeeScript |
IDM_LANG_CSS | Language > C > CSS |
IDM_LANG_D | Language > D > D |
IDM_LANG_DIFF | Language > D > Diff |
IDM_LANG_ERLANG | Language > E > Erlang |
IDM_LANG_ERRORLIST | Language > E > ErrorList |
IDM_LANG_ESCSEQ | Language > E > Escape Sequence (ANSI) |
IDM_LANG_ESCRIPT | Language > E > ESCRIPT |
IDM_LANG_FORTH | Language > F > Forth |
IDM_LANG_FORTRAN | Language > F > Fortran (free form) |
IDM_LANG_FORTRAN_77 | Language > F > Fortran (fixed form) |
IDM_LANG_FREEBASIC | Language > F > Freebasic |
IDM_LANG_GDSCRIPT | Language > G > GDScript |
IDM_LANG_GOLANG | Language > G > Go |
IDM_LANG_GUI4CLI | Language > G > Gui4Cli |
IDM_LANG_HASKELL | Language > H > Haskell |
IDM_LANG_HOLLYWOOD | Language > H > Hollywood |
IDM_LANG_HTML | Language > H > HTML |
IDM_LANG_INI | Language > I > INI file |
IDM_LANG_INNO | Language > I > Inno Setup |
IDM_LANG_IHEX | Language > I > Intel HEX |
IDM_LANG_JAVA | Language > J > Java |
IDM_LANG_JS | Language > J > JavaScript |
IDM_LANG_JSON | Language > J > JSON |
IDM_LANG_JSON5 | Language > J > JSON5 |
IDM_LANG_JSP | Language > J > JSP |
IDM_LANG_KIX | Language > KIXtart |
IDM_LANG_LATEX | Language > L > LaTeX |
IDM_LANG_LISP | Language > L > LISP |
IDM_LANG_LUA | Language > L > Lua |
IDM_LANG_MAKEFILE | Language > M > Makefile |
IDM_LANG_MATLAB | Language > M > Matlab |
IDM_LANG_MSSQL | Language > M > Microsoft Transact-SQL |
IDM_LANG_MMIXAL | Language > M > MMIXAL |
IDM_LANG_ASCII | Language > M > MS-DOS Style |
IDM_LANG_NIM | Language > N > Nim |
IDM_LANG_NNCRONTAB | Language > N > Nncrontab |
IDM_LANG_NSIS | Language > N > NSIS |
IDM_LANG_OBJC | Language > O > Objective-C |
IDM_LANG_OSCRIPT | Language > O > OScript |
IDM_LANG_PASCAL | Language > P > Pascal |
IDM_LANG_PERL | Language > P > Perl |
IDM_LANG_PHP | Language > P > PHP |
IDM_LANG_PS | Language > P > PostScript |
IDM_LANG_POWERSHELL | Language > P > PowerShell |
IDM_LANG_PROPS | Language > P > Properties |
IDM_LANG_PUREBASIC | Language > P > Purebasic |
IDM_LANG_PYTHON | Language > P > Python |
IDM_LANG_R | Language > R > R |
IDM_LANG_RAKU | Language > R > Raku |
IDM_LANG_REBOL | Language > R > REBOL |
IDM_LANG_REGISTRY | Language > R > Registry |
IDM_LANG_RC | Language > R > Resource file |
IDM_LANG_RUBY | Language > R > Ruby |
IDM_LANG_RUST | Language > R > Rust |
IDM_LANG_SAS | Language > S > SAS |
IDM_LANG_BASH | Language > S > Shell |
IDM_LANG_SCHEME | Language > S > Scheme |
IDM_LANG_SMALLTALK | Language > S > Smalltalk |
IDM_LANG_SPICE | Language > S > Spice |
IDM_LANG_SQL | Language > S > SQL |
IDM_LANG_SWIFT | Language > S > Swift |
IDM_LANG_SREC | Language > S > S-Record |
IDM_LANG_TCL | Language > T > TCL |
IDM_LANG_TEHEX | Language > T > Tektronix extended HEX |
IDM_LANG_TEX | Language > T > TeX |
IDM_LANG_TOML | Language > T > TOML |
IDM_LANG_TXT2TAGS | Language > T > txt2tags |
IDM_LANG_TYPESCRIPT | Language > T > TypeScript |
IDM_LANG_VB | Language > V > Visual Basic |
IDM_LANG_VISUALPROLOG | Language > V > Visual Prolog |
IDM_LANG_VHDL | Language > V > VHDL |
IDM_LANG_VERILOG | Language > V > Verilog |
IDM_LANG_XML | Language > XML |
IDM_LANG_YAML | Language > YAML |
IDM_LANG_USER_DLG | Language > User Defined Language > Define your language... |
IDM_LANG_OPENUDLDIR | Language > User Defined Language > Open User Defined Language folder... |
IDM_LANG_UDLCOLLECTION_PROJECT_SITE | Language > User Defined Language > Notepad++ User Defined Languages Collection |
IDM_LANG_USER | Language > User-Defined |
IDM_SETTING_PREFERENCE | Settings > Preferences... |
IDM_LANGSTYLE_CONFIG_DLG | Settings > Style Configurator... |
IDM_SETTING_SHORTCUT_MAPPER | Settings > Shortcut Mapper... |
IDM_SETTING_IMPORTPLUGIN | Settings > Import > Import plugin(s)... |
IDM_SETTING_IMPORTSTYLETHEMES | Settings > Import > Import style theme(s)... |
IDM_SETTING_EDITCONTEXTMENU | Settings > Edit Popup ContextMenu |
IDM_TOOL_MD5_GENERATE | Tools > MD5 > Generate... |
IDM_TOOL_MD5_GENERATEFROMFILE | Tools > MD5 > Generate from files... |
IDM_TOOL_MD5_GENERATEINTOCLIPBOARD | Tools > MD5 > Generate from selection into clipboard |
IDM_TOOL_SHA1_GENERATE | Tools > SHA-1 > Generate... |
IDM_TOOL_SHA1_GENERATEFROMFILE | Tools > SHA-1 > Generate from files... |
IDM_TOOL_SHA1_GENERATEINTOCLIPBOARD | Tools > SHA-1 > Generate from selection into clipboard |
IDM_TOOL_SHA256_GENERATE | Tools > SHA-256 > Generate... |
IDM_TOOL_SHA256_GENERATEFROMFILE | Tools > SHA-256 > Generate from files... |
IDM_TOOL_SHA256_GENERATEINTOCLIPBOARD | Tools > SHA-256 > Generate from selection into clipboard |
IDM_TOOL_SHA512_GENERATE | Tools > SHA-512 > Generate... |
IDM_TOOL_SHA512_GENERATEFROMFILE | Tools > SHA-512 > Generate from files... |
IDM_TOOL_SHA512_GENERATEINTOCLIPBOARD | Tools > SHA-512 > Generate from selection into clipboard |
IDM_MACRO_STARTRECORDINGMACRO | Macro > Start Recording |
IDM_MACRO_STOPRECORDINGMACRO | Macro > Stop Recording |
IDM_MACRO_PLAYBACKRECORDEDMACRO | Macro > Playback |
IDM_MACRO_SAVECURRENTMACRO | Macro > Save Current Recorded Macro... |
IDM_MACRO_RUNMULTIMACRODLG | Macro > Run a Macro Multiple Times... |
IDM_EXECUTE | Run > Run... |
IDM_EXECUTE_VALIDATE_SHORTCUTSXML | Run > Validate shortcuts.xml |
IDM_SETTING_OPENPLUGINSDIR | Plugins > Open Plugins Folder... |
IDM_WINDOW_SORT_FN_ASC | Window > Sort By > Name A to Z |
IDM_WINDOW_SORT_FN_DSC | Window > Sort By > Name Z to A |
IDM_WINDOW_SORT_FP_ASC | Window > Sort By > Path A to Z |
IDM_WINDOW_SORT_FP_DSC | Window > Sort By > Path Z to A |
IDM_WINDOW_SORT_FT_ASC | Window > Sort By > Type A to Z |
IDM_WINDOW_SORT_FT_DSC | Window > Sort By > Type Z to A |
IDM_WINDOW_SORT_FS_ASC | Window > Sort By > Content Length Ascending |
IDM_WINDOW_SORT_FS_DSC | Window > Sort By > Content Length Descending |
IDM_WINDOW_SORT_FD_ASC | Window > Sort By > Modified Time Ascending |
IDM_WINDOW_SORT_FD_DSC | Window > Sort By > Modified Time Descending |
IDM_WINDOW_WINDOWS | Window > Windows... |
IDM_WINDOW_MRU_FIRST | Window > Recent Window |
IDM_CMDLINEARGUMENTS | ? > Command Line Arguments... |
IDM_HOMESWEETHOME | ? > Notepad++ Home |
IDM_PROJECTPAGE | ? > Notepad++ Project Page |
IDM_ONLINEDOCUMENT | ? > Notepad++ Online User Manual |
IDM_FORUM | ? > Notepad++ Community (Forum) |
IDM_UPDATE_NPP | ? > Update Notepad++ |
IDM_CONFUPDATERPROXY | ? > Set Updater Proxy... |
IDM_DEBUGINFO | ? > Debug Info... |
IDM_ABOUT | ? > About Notepad++ |
+ IDM_FILE_NEW | ＋ |
IDM_DROPLIST_LIST | ▼ > Recent Window |
+ IDM_FILE_CLOSE | ✕ |

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
