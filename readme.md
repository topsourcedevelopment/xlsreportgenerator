
About

This is the phpexcel compatibility with PHP7.4. date of changes - 10 Oct. 2020

fixed the below warnings which were appearing in the phpexcel class file for php 7.4 version

Warning1: PHP Warning:  count(): Parameter must be an array or an object that implements Countable in PHPExcel\Writer\Excel2007\Worksheet.php on line 769

Original line of code was:  if (count($columns > 0)) changed it to - if (is_array($columns) && count($columns) > 0)


Warning2: PHP Warning:  A non-numeric value encountered in PHPExcel\Cell.php on line 803

Error was appearing for the line: $_indexCache[$pColumnIndex] = chr(65 + $pColumnIndex); 
This line of code is define in the public static function stringFromColumnIndex($pColumnIndex = 0) block. added the below code at the start of the function to solve this warning.

if(!is_numeric($pColumnIndex))
                                {
                                                $pColumnIndex = 0;
                                }

