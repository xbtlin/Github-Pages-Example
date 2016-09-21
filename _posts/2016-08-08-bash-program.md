
## problems I encounted
if not followed by space

    #!/bin/bash
	if[-z $1]
	then
	    echo You have to ...
	    exit 1
	fi

	echo the args is $1
	exit 0
	
提示如下    
	
	./txuan: line 2: if[-z ]: command not found
	./txuan: line 3: syntax error near unexpected token `then'
	./txuan: line 3: `then'

只要把`if`、`[`和`$1`后面分别加个空格，则问题不再出现，为什么？