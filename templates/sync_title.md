<%*
let file_name = tp.file.title;
const file = tp.file.find_tfile(tp.file.title);

const {update} = app.plugins.plugins["metaedit"].api;
await update("title",file_name.replace(/_/g, " "),file);
-%>
