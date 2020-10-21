https://www.hackthebox.eu/invite

Commençez par ouvrir la console avec `F12`.<br/>
On tombe là-dessus :<br/><br/>
![Image de la tête de mort](https://github.com/Filtox/Cybersecurity/blob/main/HackTheBox/console.PNG)

Il est indiqué qu'un fichier javascript est intéressant, on va donc se rendre dans l'onglet `sources > js > inviteapi.min.js`

```javascript
//This javascript code looks strange...is it obfuscated???

eval(function(p,a,c,k,e,r){e=function(c){return c.toString(a)};if(!''.replace(/^/,String)){while(c--)r[e(c)]=k[c]||e(c);k=[function(e){return r[e]}];e=function(){return'\\w+'};c=1};while(c--)if(k[c])p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c]);return p}('0 3(){$.4({5:"6",7:"8",9:\'/b/c/d/e/f\',g:0(a){1.2(a)},h:0(a){1.2(a)}})}',18,18,'function|console|log|makeInviteCode|ajax|type|POST|dataType|json|url||api|invite|how|to|generate|success|error'.split('|'),0,{}))
```
Un mot nous interpelle : `makeInviteCode`

Il faut taper `makeInviteCode()` dans la console. Une réponse très intéressante apparait :<br/><br/>
![Image de la réponse dans la console](https://github.com/Filtox/Cybersecurity/blob/main/HackTheBox/console1.png)

Les données sont cryptées. Elles sont cryptés en ROT13. Il suffit de se rendre sur un site et de décoder ces données `Va beqre gb trarengr gur vaivgr pbqr, znxr n CBFG erdhrfg gb /ncv/vaivgr/trarengr`, ce qui donne `In order to generate the invite code, make a POST request to /api/invite/generate`. Après ça, ouvrez un terminal et éxécuter `curl -XPOST https://www.hackthebox.eu/api/invite/generate`, ce qui donne : `{"success":1,"data":{"code":"unCodeSeraIci","format":"encoded"},"0":200}`. On peut voir que le code est encore encodé. Allez à nouveau sur un décodeur en base 64 et rentrez le code, ce qui vous donnera votre code d'invitation.