---

kanban-plugin: basic

---

## TODO

- [ ] @@{00:45}  [[This task]]


## In-process

- [ ] 


## Done

- [ ] 


## Pause

- [ ] ```dataviewjs<br>function callout(text, type) {<br>    const allText = `> [!${type}]\n` + text;<br>    const lines = allText.split('\n');<br>    return lines.join('\n> ') + '\n'<br>}<br><br>const query = `<br><br>filter by function !task.file.path.includes('Work Plan')<br>filter by function task.status.type === 'NON_TASK';<br>path includes ${dv.current().file.folder}<br>`;<br><br>dv.paragraph(callout('```tasks\n' + query + '\n```', 'Paused'));<br>```


***

## Archive

- [ ] filter by function !task.file.path.includes('Work Plan')

%% kanban:settings
```
{"kanban-plugin":"basic"}
```
%%