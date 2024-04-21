> [!abstract]
> 
> PySimpleGUI is a Python library for creating quick and easy graphical user interfaces. It offers a simple API that encapsulates the complexities of underlying libraries like Tkinter, Qt, WxPython, and Remi, enabling developers to create fully functional GUIs with minimal code.

# Layouts
## Brackets
| # Bracket Set | Explanation |
| ---- | ---- |
| First | Collection to encapsulate the layout |
| **Second** | Elements will be grouped in the same row |
| *Third* | Elements will be grouped in the same column (and row) |
# Elements
## All
|Element Name|Aliases|tkinter Widget|Description|
|:--|:--|:--|:--|
|[[#Text]] |T, Txt|tk.Label|One or more lines of Text|
|Input|I, In, InputText|tk.Entry|Single line text input|
|Combo|DD, Drop, DropDown, InputCombo|ttk.Combobox|A "Dropdown" list that can be edited too|
|OptionMenu|InputOptionMenu|tk.OptionMenu|Like a Combo|
|Multiline|ML, MLine|tk.Text or tk.scrolledtext.ScrolledText|Multiple lines of text for input or output|
|Output||tk.Text (sorta)|Not suggested. Multiline is better choice. Re-routes stdout|
|Radio|R, Rad|tk.Radiobutton|Radio Buttons - choose 1 from several|
|Checkbox|CB, CBox, Check|tk.Checkbutton|Checkbox - binary choice Yes/No|
|Spin|Sp|tk.Spinbox|Choose 1 by using arrows. Can manually enter also|
|Button|B, Btn|tk.Button or ttk.Button|Button - plain or with image|
|Image|Im|tk.Label|A PNG or GIF image|
|Canvas||tk.Canvas|A drawing area. Graph may be batter to use|
|Column|Col|Combination Canvas & Frame|Embeds layouts inside layouts|
|Frame|Fr|tk.LabelFrame|A frame with a title and a border|
|Tab||tk.Frame|Container used with TabGroup|
|TabGroup||ttk.Notebook|Holds Tabs in layouts|
|Pane||tk.PanedWindow|Sliding columns (it's kinda weird but useful)|
|Graph|G|tk.Canvas|A drawing area with primitives|
|Slider|Sl|tk.Scale|Slider to choose from range of choices|
|Listbox|LB, LBox|tk.Listbox|Listbox - a list of choices|
|Menu|MenuBar, Menubar|tk.Menu|A standard Menubar|
|MenubarCustom||Combined Elements|Custom colors and font for menubar|
|ButtonMenu|BM, BMenu|tk.Menubutton|Button that shows a menu|
|Titlebar||Combined Elements|Custom colors for a titlebar|
|ProgressBar|PBar, Prog, Progress|ttk.Progressbar||
|Table||ttk.Treeview|A table with clickible cells and headers|
|Tree||ttk.Treeview|A tree with collapsible sections|
|VerticalSeparator|VSep, VSeparator|ttk.Separator|Vertical line|
|HorizontalSeparator|HSep, HSeparator|ttk.Separator|Horizontal line|
|StatusBar|SBar|tk.Label|Statusbar for bottom of window|
|Sizegrip|SGrip|ttk.Sizegrip|A grip for the bottom right corner of a window|
|Push|P, Stretch|PySimpleGUI Elements|Pushes elements horizontally|
|VPush|VP, VStretch|PySimpleGUI Elements|Pushes rows vertically|
|Sizer||Column Element|Creates a Width x Height number of pixels for padding/sizing|
## Text
### sg.Text
Used to display basic text

> [!parameters]
>**text** - Text to be shown in the screen
>

### sg.InputText
Can inherit values from other elements to display

> [!parameters] 
> **default_text** - Text if element isn't transferred text
> **key** - Unique identifier

