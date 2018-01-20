These are some JavaScript snippets I use to generate the lists. 

### To use on https://wally3k.github.io/
```javascript
lists = document.getElementsByClassName('bdUrlList')
c = '!'
o = '';
 
for(i=0;i<lists.length;i++){
  list = lists[i]
  sites = list.getElementsByClassName('bdTick')
  if(sites.length){
    o += c+document.getElementsByTagName('h2')[i].innerHTML+' - '+sites.length+" links \n"
    console.log(sites)
    for(j=0;j<sites.length;j++){
      o += sites[j].getElementsByTagName('a')[1].innerHTML+"\n"
    }
  }
}
 
console.log(o)
```

### To use on uBlock 3rd party backend
```javascript
items = jQuery('.groupEntry[data-groupkey="custom"] ul.listEntries li')

output = []

for(i=0;i<items.length;i++){
  item = items[i]
  if( !$(item).hasClass('obsolete') ){
    output.push( [ parseInt($(item).find('.counts')[0].innerHTML.split(' out of ')[1].replace(',','')) ,$(item).attr('data-listkey') ] )
  }
}
output.sort(function(a,b) {
    return a[0] - b[0];
});


out = "\n\n\n"

for(i=output.length-1;i>-1;i--){
it = output[i]
out+="* "+it[1]+" - "+it[0]+"\n"
}

console.log(out+"\n\n")
```
