<%*
function toTitleCase(str) {
  return str.replace(
    /\w\S*/g,
    function(txt) {
      return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
    }
  );
}

let file_name = tp.file.title;
const file = tp.file.find_tfile(tp.file.title);

const {update} = app.plugins.plugins["metaedit"].api;
await update("title",file_name.replace(/_/g, " "),file);
-%>
