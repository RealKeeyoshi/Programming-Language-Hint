const express = require('express');
const app = express();
const port = 80;
const path = require('path');

app.use('/static', express.static('static'));
app.use(express.urlencoded())

app.set('view engine', 'pug');
app.set('views', path.join(__dirname, 'templates'));

app.get('/',(req, res)=>{
    const param = {'title': 'PUG'}
    res.status(200).render('index.pug', param)
})


app.post('/',(req, res)=>{
    const param = {'message': 'Successfully Submitted'}
    res.status(200).render('index.pug', param)
})


app.listen(port, ()=>{
    console.log(`this appication run on port ${port}`)
})
