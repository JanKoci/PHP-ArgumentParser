# PHP-ArgumentParser
Command line arguments parser in PHP, inspired by argparse for Python.

I was doing a school project for PHP and I was not really satisfied with php getopt.
So I wrote this very simple parser based on Python's argparse. 
As I said it is really basic but maybe someone will find it useful :)

### Example:

    $ php your_program --source=filename -f
    
    Array 
    (
        [source] => filename
        [f] => 1
    )
    
To achieve this all you need to do is:

    include 'ArgParser.php';
    
    $message = "USAGE: php your_program [--source filename] [-f]";
    $parser = new ArgParser($usage=$message);
    
    $parser->add_argument('source', $help='a help message', $action='get_val');
    $parser->add_argument('f', $help='a help message', $action='store_true');
    $parser->add_argument("help", $help="print help message", $action='print_help');
    
    $args = $parser->parse();
    
And that's it !

### Possible actions are:

    get_val = this means the argument expects a value (--source filename)
    store_true = store 1 when argument is found
    store_false = store 0 when argument is found
    print_help = should be applied only for the --help argument, prints usage and all help messages
  
### Parser accepts arguments in all these formats: 

    --source filename
    --source=filename
    -source filename
    source filename

### Limitations: 
  Parser does not accept multiple arguments written together: \
    -rtf    would be interpreted as one argument rtf, not 3 arguments -r, -t, -f
    
    


    
    
  
  
