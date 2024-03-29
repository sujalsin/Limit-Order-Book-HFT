# LimitBook

LimitBook is an implementation of a fast limit-order book for level-2 US equities data written in Python. It includes some tools to output sampled data as well as a curses-based application to view the book and move forward or backward in time.

Input files must be for a single day, symbol, and exchange.

## Usage

```
sudo pip install -r requirements.txt
sudo python setup.py install
```

You should then be able to run the applications in the `bin` directory.

## Input Data Format

LimitBook applications expect the following input format (in a CSV file):

* bids:

	`B,<symbol>,<exchange>,<id>,<quantity>,<price>,<timestamp>`

* asks:

	`A,<symbol>,<exchange>,<id>,<quantity>,<price>,<timestamp>`

* trades: (optional)

	`T,<symbol>,<exchange>,,<quantity>,<price>,<timestamp>`

Symbol and exchange values are currently unimportant and can be dummy values.
Lines should be in timestamp-order from earliest to latest (the order it is sent by the exchange).

## Application Descriptions

* `parse.py`  -  Simple illustration of using the limit book
* `tseries.py`  -  Parse an input file and export 1-second snapshots of the book (Uses pandas library to fill in gaps, etc)
* `convert.py`  -  Convert from an input format that uses ', ' as a CSV separator and different column order to the correct input format.
* `bookViewer.py`  -  Graphically view the book state at any point in time

