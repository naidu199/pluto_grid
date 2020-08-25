## PlutoGrid for flutter - v0.1.0

PlutoGrid, a data grid, is being developed with the goal of running on all platforms supported by Flutter.

> Currently, under development, there are plans to distribute to pub.dev.

### Features  
* Column fixation : Columns can be fixed to the left or right of the grid.
* Column shift : Change the order of the columns by dragging the column title.
* Column sort : Sort the list by clicking on the column heading.
* Column width : Change the column width by dragging the icon to the right of the column title.
* Column action : Click the icon to the right of the column title, you can control the column with the column action menu.
* Multi selection : By long tapping or clicking and moving.
* Copy & paste : Ctrl(macos : Meta) + C or V.
* Select Row Popup : Same as the grid, a selection popup that can be used when selecting an item from a list.
* Keyboard support : Arrow keys, Enter(Shift + Enter), Tab(Shift +Tab), Esc...

### Demo
[Demo Web](https://bosskmk.github.io/build/web/index.html)

### Preview

![PlutoGrid Image](https://bosskmk.github.io/images/pluto_grid_img1.jpg)

![PlutoGrid Image](https://bosskmk.github.io/images/pluto_grid_img2.jpg)

### Usage
Generate the data to be used in the grid.
```dart

List<PlutoColumn> columns = [
  PlutoColumn(
    title: 'leftFixedColumn',
    field: 'column1',
    type: PlutoColumnType.text(),
    fixed: PlutoColumnFixed.Left,
  ),
  PlutoColumn(
    title: 'readOnlyColumn',
    field: 'column2',
    type: PlutoColumnType.text(readOnly: true),
  ),
  PlutoColumn(
    title: 'textColumn',
    field: 'column3',
    type: PlutoColumnType.text(),
  ),
  PlutoColumn(
    title: 'selectColumn',
    field: 'column4',
    type: PlutoColumnType.select(['One', 'Two', 'Three']),
  ),
  PlutoColumn(
    title: 'rightFixedColumn',
    field: 'column5',
    type: PlutoColumnType.text(),
    fixed: PlutoColumnFixed.Right,
  ),
];

List<PlutoRow> rows = [
  PlutoRow(
    cells: {
      'column1': PlutoCell(value: 'column1 value'),
      'column3': PlutoCell(value: 'column3 value'),
      'column4': PlutoCell(value: 'One'),
      'column5': PlutoCell(value: 'column5 value'),
    }, 
  ),
  PlutoRow(
    cells: {
      'column1': PlutoCell(value: 'column1 value'),
      'column2': PlutoCell(value: 'column2 value'),
      'column3': PlutoCell(value: 'column3 value'),
      'column4': PlutoCell(value: 'Two'),
      'column5': PlutoCell(value: 'column5 value'),
    }, 
  ),
  PlutoRow(
    cells: {
      'column1': PlutoCell(value: 'column1 value'),
      'column2': PlutoCell(value: 'column2 value'),
      'column3': PlutoCell(value: 'column3 value'),
      'column4': PlutoCell(value: 'Three'),
      'column5': PlutoCell(value: 'column5 value'),
    }, 
  ),
];
```

Create a grid with the data created above.
```dart
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('PlutoGrid Demo'),
      ),
      body: Container(
        padding: const EdgeInsets.all(30),
        child: PlutoGrid(
          columns: dummyData.columns,
          rows: dummyData.rows,
          onChanged: (PlutoOnChangedEvent event) {
            print(event);
          },
        ),
      ),
    );
  }
```

### Coming soon

* Column types (Number, Date, DateTime...)
* Column filtering
* Row selection
* Multi column sorting
* Paging
* Control UI for mobile