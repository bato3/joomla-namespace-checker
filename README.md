# Joomla Namespace Checker
For migrating to Joomla 3.8.x

This script scans a directory recursively for PHP files containing calls to the old classes (e.g. JFactory).

## Usage
To run the script, download it and execute it using php
```
$ php joomlaNamespaceChecker.phar path/to/your/project
```

If any calls are found you will get the following output:
```
FILE: path/to/your/project/someFile.php
-------------------------------------------------------------------------------------
Line: 12 | Class found: JTable        | Replace with: Joomla\CMS\Table\Table
Line: 21 | Class found: JPlugin       | Replace with: Joomla\CMS\Plugin\CMSPlugin
Line: 47 | Class found: JPluginHelper | Replace with: Joomla\CMS\Plugin\PluginHelper
Line: 56 | Class found: JFactory      | Replace with: Joomla\CMS\Factory
Line: 75 | Class found: JPluginHelper | Replace with: Joomla\CMS\Plugin\PluginHelper
Line: 84 | Class found: JFactory      | Replace with: Joomla\CMS\Factory
-------------------------------------------------------------------------------------
```

### Excluding paths & files

Pass the `--exclude` option to exclude directories and files.

```
$ php joomlaNamespaceChecker.phar --exclude=/somepath/,somefile.php,some/other/path/ path/to/your/project
```

The exclusion is very basic so you might have to tweak the paths a bit, this also means wildcards like * are *not* supported.

e.g. if you pass `--exclude=google`, it will filter out anything that has `google` in it's path or filename.

To reliably filter out a whole directory wrap it in `/ /` and for single files use `filename.ext`.
