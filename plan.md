
left.allLines
right.allLines

<side>.allLines // array with all display-lines including object and array terminations, and root object/array start; marked missing:true,evaluated:true default

[
    {dline:line,val,path,type,dtype:'object-start|array-start|object-end|array-end|key-value|array-element',missing:bool,evaluated:bool,id?},
]

missingDiffs filtered
typeDiffs filtered

loop thru allLines -> if path is in missingDiffs; (mark missing=true and if type==object/array skip its children) else mark missing=false
loop thru allLines -> if path is in typeDiffs; (and if type==object/array mark its children evaluated:false)

initialize 2-d matrix - diffRender
[
    [num1,val1,num2,val2], // matching
    [num1,val1,num2,val2], // missing:false -  diff.eq,diff.type,diff.type(either one is array or objeect)
    [----,----,num2,val2], // right.(missing:true || evaluated:false)
    [num1,val1,----,----], // left.(missing:true || evaluated:false)
]

