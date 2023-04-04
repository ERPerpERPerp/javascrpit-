# javascrpit-Live/javascript/

javascript:try{async function getSetId(pin){const res=await fetch(`https://quizlet.com/webapi/3.8/multiplayer/game-instance?gameCode=${pin}`);const json=await res.json();if(json.error)throw new Error(json.error.message);return json.gameInstance.itemId;}async function getSetData(setId){const res=await fetch(`https://quizlet.com/${setId}`);const text=await res.text();const data=text.match(/\\"termIdToTermsMap\\":{.+?{.+?\\"termSort\\":/gi)?.[0];if(!data)throw new Error("Failed to parse set data.");const parsed=JSON.parse(data.slice(21,-14).replaceAll(`\\"`,`"`));return[Object.fromEntries(Object.values(parsed).map(({word, definition})=>[word, definition])),Object.fromEntries(Object.values(parsed).map(({word, definition})=>[definition, word]))];}function getActiveQuestion(){try{const question=document.querySelector(".StudentPrompt-text").textContent;const answers=Array.from(document.querySelectorAll(".StudentAnswerOption-text"));return[question, answers];}catch{}return[null,null];}(async()=>{const pin=prompt("Enter PIN, like: XXX-XXX","").match(/[0-9a-zA-Z]/g).join("");if(pin.length!==6)throw new Error("Pin must be 6 characters in length.");const setId=await getSetId(pin);const[term2Def, def2Term]=await getSetData(setId);setInterval(async function(){const[question,choices]=getActiveQuestion();if(!question||!choices)return;if(question in term2Def){choices.forEach((choice)=>{if(choice.textContent===term2Def[question])choice.style.fontWeight="bolder";});}else if(question in def2Term){choices.forEach((choice)=>{if(choice.textContent===def2Term[question])choice.style.fontWeight="bolder";});}else{choices.forEach((choice)=>{choice.style.fontWeight="normal";});}},0);})()}catch(err){alert(err)};void 0

#javascript-(Micro)match/javascript/

javascript:(function(){const matches={};Quizlet.matchModeData.terms.forEach((term)=>{matches[term.word]=term.definition});let css='FormattedText notranslate TermText MatchModeQuestionGridTile-text';if(document.getElementsByClassName(css).length===0){css='MatchModeQuestionScatterTile'}const tiles=Array.from(document.getElementsByClassName(css));const colors=['#f93640','#f98836','#f9e936','#3df936','#36f9d9','#3650f9','#7e36f9','#dc36f9','#ffffff','#a3a3a3','#424242'];Array.from(document.getElementsByClassName('MatchModeQuestionGridTile-image')).forEach((image)=>{image.style.display='none'});let colorIndex=0;for(const term in matches){const definition=matches[term];tiles.forEach((tile)=>{if(tile.textContent===term){tiles.forEach((box)=>{if(box.textContent===definition){box.style.background=colors[colorIndex];box.style.color='black'}});tile.style.background=colors[colorIndex];tile.style.color='black';colorIndex+=1}})}})();void 0

#javascript-Gravity/javascript/

javascript:(function(){if(!window.gooseGravity){window.gooseGravity=true;const matches={};Quizlet.gravityModeData.terms.forEach((term)=>{matches[term.word]=term.definition});const reversed={};for(const term in matches){reversed[matches[term]]=term}setInterval(function(){const asteroids=Array.from(document.querySelectorAll('.TermText'));if(asteroids.length===0){return}asteroids.forEach((asteroid)=>{const term=asteroid.textContent;if(asteroid.gooseAnswered){return}if(term in matches){asteroid.textContent=matches[term];asteroid.gooseAnswered=true}else if(term in reversed){asteroid.textContent=reversed[term];asteroid.gooseAnswered=true}})},100)}})();void 0

(async ()=>{function _0xf2fc(){const _0x14de8e=['\x20\x66\x6f\x6f\x64\x20\x74\x6f\x20\x39','\x70\x68\x61\x73\x65','\x65\x72\x7b\x63\x6f\x6c\x6f\x72\x3a\x23','\x61\x48\x5a\x4e\x66','\x69\x6e\x2d\x6c\x65\x66\x74\x3a\x20\x35','\x44\x78\x41\x78\x45','\x63\x68\x6f\x69\x63\x65\x45\x53\x50','\x6f\x76\x41\x52\x2b\x67\x79\x72\x75\x32','\x4e\x6c\x57\x4e\x76','\x63\x6c\x61\x73\x73','\x4c\x44\x45\x77\x4c\x6a\x55\x31\x4d\x6d','\x70\x20\x76\x61\x6c\x75\x65','\x6e\x6c\x6f\x63\x6b\x69\x6e\x67\x20\x6d','\x73\x20\x47\x61\x6d\x65\x6d\x6f\x64\x65','\x43\x72\x79\x70\x74\x6f\x20\x48\x61\x63','\x73\x65\x74\x47\x72\x61\x76\x69\x74\x79','\x71\x48\x4f\x76\x4f','\x33\x4e\x54\x42\x55\x65\x44\x4b\x4a\x61','\x63\x74\x20\x70\x61\x73\x73\x77\x6f\x72','\x74\x6f\x4c\x47\x4c','\x31\x36\x36\x31\x34\x39\x36\x32\x39\x35','\x70\x54\x7a\x43\x72','\x34\x64\x74\x67\x6a\x4d\x43','\x2f\x42\x6c\x6f\x6f\x6b\x73\x2f\x79\x65','\x69\x73\x41\x72\x72\x61\x79','\x66\x6c\x61\x70\x70\x79','\x69\x6e\x70\x75\x74','\x44\x4a\x47\x67\x64','\x53\x4d\x6c\x4c\x69','\x20\x74\x72\x61\x6e\x73\x69\x74\x69\x6f','\x51\x6e\x45\x4c\x6b','\x79\x79\x69\x45\x77\x41\x76\x78\x69\x44','\x63\x61\x6d\x65\x72\x61\x73','\x65\x70\x69\x63\x2d\x33','\x6f\x44\x48\x6d\x6c','\x6d\x62\x3a\x68\x6f\x76\x65\x72\x7b\x62','\x46\x72\x6f\x67','\x59\x30\x4c\x44\x51\x79\x4e\x79\x34\x32','\x31\x36\x35\x38\x35\x36\x37\x37\x36\x35','\x72\x61\x74\x65','\x62\x28\x31\x31\x2c\x20\x31\x39\x34\x2c','\x6c\x30\x52\x56\x68\x30\x55\x32\x39\x6d','\x69\x78\x74\x6c\x67','\x74\x74\x6c\x65\x20\x74\x6f\x20\x72\x75','\x66\x6f\x6e\x74\x53\x69\x7a\x65','\x79\x31\x55\x4c\x7a\x56\x62\x34\x5a\x70','\x30\x36\x33\x2e\x31\x36\x38\x2d\x2e\x31','\x73\x74\x72\x69\x6e\x67\x69\x66\x79','\x4d\x53\x34\x31\x4e\x44\x4d\x74\x4d\x7a','\x3a\x35\x70\x78\x3b\x62\x61\x63\x6b\x67','\x56\x38\x72\x47\x30\x42\x45\x43\x6d\x45','\x52\x6a\x4d\x53\x6f','\x41\x67\x4e\x54\x45\x79\x49\x44\x55\x78','\x23\x64\x32\x35\x39\x32\x37','\x33\x54\x42\x4b\x46\x47\x62\x54\x2b\x79','\x49\x6f\x44\x76\x67\x66\x2f\x4a\x55\x7a','\x4c\x33\x4e\x32\x5a\x7a\x34\x4b\x22\x3e','\x69\x65\x73\x20\x6d\x6f\x76\x65\x20\x32','\x4c\x6a\x6b\x35\x4e\x47\x4d\x77\x4c\x44','\x6b\x55\x64\x41\x4a','\x79\x2c\x20\x43\x68\x69\x6c\x6c\x79\x2c','\x4e\x69\x30\x78\x4d\x44\x49\x75\x4e\x54','\x46\x43\x39\x63\x73\x4d\x4e\x6f\x61\x74','\x68\x72\x72\x4d\x59','\x76\x69\x53\x75\x44','\x75\x6a\x67\x67\x38\x43\x72\x34\x5a\x68','\x62\x61\x63\x6b\x67\x72\x6f\x75\x6e\x64','\x65\x78\x63\x61\x76\x61\x74\x65','\x20\x20\x20\x20\x20\x20\x20\x20\x20\x3c','\x52\x61\x62\x62\x69\x74','\x20\x79\x6f\x75','\x61\x39\x75\x71\x52\x51\x42\x46\x4c\x79','\x54\x6f\x75\x63\x61\x6e','\x6d\x79\x43\x61\x72\x64','\x45\x69\x47\x45\x6c\x30\x6f\x35\x4e\x32','\x69\x4a\x59\x4e\x6f','\x61\x42\x5a\x71\x58\x6c\x48\x55\x45\x59','\x67\x75\x4d\x7a\x45\x31\x4c\x54\x55\x75','\x39\x37\x70\x78','\x65\x20\x79\x6f\x75','\x78\x69\x4a\x50\x52','\x73\x20\x6f\x6e\x20\x70\x6c\x61\x79\x2e','\x30\x42\x53\x6e\x46\x64\x39\x7a\x34\x4b','\x31\x36\x30\x37\x30\x35\x37\x36\x37\x32','\x6e\x20\x79\x6f\x75\x20\x6f\x70\x65\x6e','\x6a\x76\x5a\x79\x35\x38\x74\x75\x32\x30','\x29\x22\x20\x78\x6d\x6c\x6e\x73\x3d\x22','\x5f\x6f\x72\x61\x6e\x67\x65\x2e\x73\x76','\x56\x4f\x55\x75\x6d','\x4d\x6a\x59\x34\x4c\x54\x4d\x75\x4e\x54','\x7a\x34\x70\x4b\x6d\x64\x5a\x53\x6d\x34','\x66\x6a\x6d\x46\x43\x6e\x38\x7a\x44\x66','\x75\x66\x68\x6e\x46','\x65\x74\x2e\x63\x6f\x6d','\x74\x69\x6d\x65','\x65\x73\x74\x2f\x46\x69\x73\x68\x5f\x57','\x6f\x4f\x6a\x6c\x36\x7a\x6c\x52\x36\x52','\x6f\x52\x4f\x73\x50','\x61\x56\x51\x68\x6a','\x74\x72\x61\x6e\x73\x6c\x61\x74\x65\x28','\x4d\x54\x4d\x74\x4e\x53\x34\x35\x4e\x54','\x43\x36\x44\x44\x69\x51\x58\x51\x34\x63','\x4f\x43\x34\x32\x4e\x54\x45\x74\x4e\x7a','\x70\x57\x48\x4e\x4e','\x7a\x74\x68\x47\x46','\x30\x30\x2f\x73\x76\x67\x22\x20\x77\x69','\x53\x74\x65\x61\x6c\x73\x20\x61\x6c\x6c','\x43\x68\x65\x73\x68\x69\x72\x65\x20\x43','\x75\x6e\x63\x6f\x6d\x6d\x6f\x6e\x2d\x31','\x65\x73\x74\x2f\x52\x61\x63\x69\x6e\x67','\x73\x74\x79\x6c\x65','\x77\x45\x6e\x4f\x43','\x64\x6c\x62\x6d\x56\x79\x59\x58\x52\x76','\x50\x52\x67\x54\x50','\x4d\x79\x73\x74\x69\x63\x61\x6c','\x51\x46\x51\x72\x66','\x4d\x50\x65\x69\x69','\x4e\x69\x30\x34\x4e\x69\x34\x35\x4e\x7a','\x65\x43\x52\x51\x75\x6f\x44\x32\x58\x71','\x5a\x30\x32\x53\x59\x43\x45\x47\x4e\x56','\x4d\x67\x6f\x4a\x43\x57\x4d\x34\x4c\x6a','\x4c\x65\x54\x55\x52','\x4d\x61\x6b\x65\x73\x20\x79\x6f\x75\x20','\x46\x68\x6c\x6b\x7a','\x54\x75\x72\x74\x6c\x65','\x70\x6c\x61\x79\x65\x72\x27\x73\x20\x63','\x69\x6e\x73\x65\x74\x20\x30\x20\x2d\x36','\x73\x68\x69\x66\x74','\x53\x75\x70\x65\x72\x20\x53\x6e\x6f\x77','\x4d\x78\x69\x55\x62','\x46\x6c\x61\x70\x70\x79\x20\x42\x6c\x6f','\x67\x68\x6d\x6d\x74','\x70\x75\x73\x68','\x43\x75\x73\x74\x6f\x6d\x20\x50\x61\x73','\x53\x58\x36\x74\x65\x59\x42\x53\x6c\x46','\x63\x6f\x6c\x75\x6d\x6e','\x49\x6e\x63\x6f\x6e\x73\x6f\x6c\x61\x74','\x52\x65\x6d\x6f\x76\x65\x20\x44\x75\x63','\x30\x20\x2d\x31\x20\x32\x31\x20\x31\x36','\x4f\x53\x30\x78\x4e\x44\x51\x75\x4f\x44','\x4a\x61\x35\x71\x31\x73\x71\x48\x4a\x68','\x66\x6f\x6e\x74\x46\x61\x6d\x69\x6c\x79','\x6c\x20\x65\x6e\x65\x6d\x79\x20\x64\x69','\x52\x49\x64\x6e\x69\x6e\x32\x48\x53\x4b','\x4d\x69\x34\x77\x4d\x6a\x63\x74\x4f\x43','\x53\x65\x61\x6c','\x5a\x62\x4e\x74\x70\x4a\x64\x74\x49\x37','\x63\x6c\x61\x73\x73\x4c\x69\x73\x74','\x75\x4e\x2b\x32\x72\x61\x74\x43\x4b\x6c','\x63\x79\x5a\x46\x56','\x66\x75\x6c\x6c\x43\x64','\x57\x72\x4c\x73\x69','\x54\x6a\x67\x6b\x76','\x32\x34\x2d\x31\x2e\x34\x33\x38\x2d\x31','\x6b\x72\x4c\x47\x7a','\x4f\x6d\x35\x6c\x64\x79\x41\x77\x49\x44','\x68\x77\x39\x63\x4c\x44\x39\x46\x67\x74','\x65\x6d\x69\x74','\x53\x65\x74\x20\x54\x6f\x6b\x65\x6e\x73','\x62\x6f\x72\x64\x65\x72\x2d\x62\x6f\x78','\x64\x41\x57\x72\x6b','\x63\x6c\x76\x65\x4e\x46\x37\x75\x52\x37','\x41\x6e\x65\x68\x2f\x35\x50\x38\x47\x74','\x6c\x65\x66\x74\x2d\x64\x69\x61\x6d\x6f','\x46\x73\x4c\x54\x4d\x75\x4e\x7a\x45\x31','\x43\x72\x61\x7a\x79\x20\x4b\x69\x6e\x67','\x63\x6a\x4d\x50\x46','\x6c\x20\x72\x6f\x63\x6b\x73\x20\x61\x6e','\x6e\x64\x61\x72\x69\x65\x73\x2b\x29','\x6f\x7a\x4d\x66\x65','\x67\x6c\x69\x74\x63\x68','\x6d\x73\x29\x20\x52\x65\x73\x75\x6c\x74','\x31\x30\x25\x29\x3b\x74\x72\x61\x6e\x73','\x58\x55\x75\x42\x62','\x55\x5a\x69\x55\x4b','\x42\x39\x59\x4f\x4d\x64\x66\x67\x6b\x73','\x57\x69\x74\x63\x68','\x52\x64\x68\x6a\x6c','\x54\x59\x49\x43\x73','\x73\x6f\x72\x74','\x67\x73\x4f\x44\x41\x75\x4e\x54\x45\x34','\x46\x4e\x42\x48\x68','\x57\x4c\x70\x7a\x44','\x34\x7a\x4e\x54\x63\x74\x4f\x53\x34\x79','\x53\x77\x61\x61\x76\x34\x6c\x65\x41\x4c','\x63\x6f\x72\x72\x65\x63\x74\x50\x61\x73','\x50\x55\x79\x77\x42','\x6c\x58\x51\x77\x61','\x6c\x69\x66\x65\x73\x70\x61\x6e','\x31\x36\x35\x38\x37\x39\x30\x32\x34\x34','\x6d\x61\x72\x67\x69\x6e\x54\x6f\x70','\x30\x20\x30\x20\x30\x20\x2f\x20\x32\x30','\x4d\x6a\x49\x33\x4c\x44\x59\x34\x4c\x6a','\x4c\x63\x30\x61\x48\x65\x6f\x71\x67\x42','\x4d\x72\x78\x55\x50','\x47\x65\x74\x73\x20\x6d\x61\x78\x20\x64','\x33\x38\x77\x33\x61\x58\x76\x6c\x6e\x6a','\x78\x20\x54\x6f\x75\x63\x61\x6e','\x6f\x63\x6b\x42\x75\x74\x74\x6f\x6e\x22','\x65\x6a\x44\x77\x44','\x77\x6b\x5a\x76\x4d','\x46\x69\x6c\x6c\x73\x20\x74\x68\x65\x20','\x4c\x6a\x59\x31\x4e\x69\x30\x78\x4d\x43','\x4f\x55\x4b\x4a\x52','\x22\x3e\x0a\x20\x20\x20\x20\x20\x20\x20','\x53\x65\x74\x73\x20\x64\x61\x6d\x61\x67','\x78\x62\x52\x69\x6a','\x63\x5a\x4c\x46\x4b','\x63\x2e\x30\x38\x2e\x30\x36\x36\x2e\x31','\x79\x65\x73','\x32\x72\x65\x6d','\x61\x2c\x6d\x6f\x6e\x6f\x73\x70\x61\x63','\x4f\x54\x67\x4b\x43\x51\x6c\x6a\x4c\x54','\x73\x77\x65\x72\x20\x66\x6f\x72\x20\x79','\x42\x7a\x44\x6c\x6f\x6e\x6e\x36\x41\x7a','\x59\x30\x4c\x44\x45\x30\x4e\x69\x34\x33','\x65\x20\x6f\x6e\x20\x74\x68\x65\x20\x61','\x20\x3e\x20\x64\x69\x76','\x31\x36\x35\x38\x37\x39\x30\x32\x33\x39','\x68\x67\x4a\x41\x43\x6a\x62\x5a\x31\x7a','\x23\x61\x31\x35\x30\x39\x35','\x5a\x74\x41\x43\x6e','\x73\x70\x65\x65\x64','\x5f\x6c\x69\x76\x65\x41\x70\x70','\x55\x46\x77\x51\x4b','\x63\x68\x65\x63\x6b\x43\x6f\x6c\x6c\x69','\x67\x68\x74\x3a\x20\x62\x6f\x6c\x64\x65','\x68\x64\x64\x4d\x59','\x6f\x38\x5a\x7a\x34\x4b\x50\x43\x39\x6e','\x4d\x6a\x59\x73\x4d\x54\x4d\x78\x4c\x6a','\x76\x62\x46\x78\x75','\x6e\x73\x65\x3c\x2f\x73\x70\x61\x6e\x3e','\x6d\x2f\x62\x56\x76\x66\x31\x4d\x31\x72','\x74\x4a\x54\x68\x59','\x74\x61\x6b\x65','\x78\x42\x5a\x42\x56','\x72\x61\x72\x65\x2d\x34','\x62\x71\x41\x31\x54\x43\x64\x64\x31\x4e','\x39\x41\x4a\x43\x50\x37\x48\x78\x38\x55','\x61\x64\x64\x45\x76\x65\x6e\x74\x4c\x69','\x47\x6f\x6c\x64\x66\x69\x73\x68','\x66\x48\x79\x37\x34\x4a\x58\x79\x6d\x64','\x49\x63\x6f\x6e\x2e\x73\x76\x67','\x6b\x65\x74\x2f\x70\x61\x72\x74\x69\x63','\x
