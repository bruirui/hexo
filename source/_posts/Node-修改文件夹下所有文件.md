---
title: Node 修改文件夹下所有文件
date: 2018-09-03 15:00:48
tags: Node
---

> Node
  node文件系统-fs

#### 应用场景：获取某个文件夹下所有html文件,将html页面标题设置为html文件名且拼接css文件

```
var fs = require('fs');
/**
 * [editHTML description]
 * @param  {[type]} dirName [文件夹路径]
 * @param  {[type]} name    [文件名]
 * @param  {[type]} file    [当前文件]
 * @return {[type]}         [description]
 */
function editHTML(dirName,name,file) {
    var _fileN = dirName+"/"+file;
    fs.readFile(_fileN, 'utf8', function (err, data) {
        if (err) throw err; // we'll not consider error handling for now
        //改写文件，替换title
        // console.log(name);
        var _newData = data;
        if(_newData.indexOf('<title></title>') > 0){
            _newData = _newData.replace('<title></title>','<title>'+name+'</title>');
            _newData = _newData.replace('</style>','</style><link rel="stylesheet" type="text/css" href="./prorecruitmentruledetial.css">');
            var s_index = _newData.indexOf('<title>'),
                e_index = _newData.indexOf('</title>'),
                equalFlag = _newData.substring(s_index+7, e_index) == name;
            console.log(_newData.substring(s_index+7, e_index)+"====="+name+"====="+equalFlag);
            fs.writeFile(_fileN, _newData, function (err) {
                if (err) console.error(err);
            });
        }
    });
}

/**
 * [readDirAllFiles 读取文件夹下的所有文件]
 * @param  {[type]} dirName  [文件夹路径]
 * @param  {[type]} fileType [规定该操作作用的文件类型]
 * @return {[type]}          [description]
 */
function readDirAllFiles(dirName,fileType) {
    fs.readdir(dirName,function(err, data) {
        data.forEach(function(item,index) {
            var type = item.split('.');
            if(type[type.length-1] == fileType){
                editHTML(dirName,type[0],item);
            }
        })
    })
}

//读取./aa文件夹下的所有文件，当文件后缀为.html时，替换html内title，并添加prorecruitmentruledetial.css的link链接
readDirAllFiles('./aa','html');
```