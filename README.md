# HES System 

## 注意事項

1. 每個內頁都必須包在 `<div id="main">` 中，在最外層styles.scss檔中有宣告。
2. For every new component, please add `canActivate: [AuthguardGuard],` into `const routes: Routes` in `app-routing.module.ts` in order to do auto authguard.
3. Header 已經包含sidebar，所以每個內頁只需include header即可!

## install

1. Click Outside Detect: `npm install --save ng-click-outside`
    [reference](https://www.npmjs.com/package/ng-click-outside)
2. Angular Tree Component: `npm install --save angular-tree-component`
    [reference](https://angular2-tree.readme.io/docs/treemodel)
3. `npm install --save jsonfile`
4. `npm install --save-dev @types/leaflet`
5. `npm install @types/topojson --save-dev`
6. `npm install --save @angular/material @angular/cdk @angular/animations`
7. `npm install @types/leaflet.markercluster`
8. `npm install leaflet@1.3`
9. `npm install @types/leaflet@1.2`
10. `npm install @asymmetrik/ngx-leaflet@4`
------------------------------------------------ 2018.08.14
11. Angular material password 
    (1) `npm i @angular/cdk @angular/material @angular/animations @angular/forms`
    (2) `npm install --save @angular-material-extensions/password-strength`
------------------------------------------------ 2018.08.15
12. Angular data table
  `npm i angular-6-datatable --save`
------------------------------------------------ 2018.08.17
13. Angular Material datepicker
  `npm i --save @angular/material-moment-adapter moment`
  
## Login page design v.1

1. design login page
2. user info initial
3. password security prevent

## Header design

1. fixed header
2. header menu will expand when hovered
3. click on header menu tab will open sidebar and change url show the responsive page

## Sidebar design

1. Pop out if user click on the header menu tab
2. Use tree diagram (change angular-tree-component/dist/angular-tree-component.css file's css design)
3. click outside sidebar window will close the sidebar (by using ng-click-outside)


## loadJson.service
1. A service to load json file(Create a client to listen)
2. Put Json file in asset/JSON folder
3. subscribe loadJson.service function with Json file path :
  `this.loadJsonService.getContentJSON('../../assets/JSON/sysManage.json').subscribe(data => {
      this.contentGeneral = data;
      console.log(this.contentGeneral);
    },
    err => {
      // Log errors if any
      console.log('error: ', err);
    });`
[reference](https://stackoverflow.com/questions/50924901/angular-6-load-json-from-local/50925032)
[problem solve1](https://stackoverflow.com/questions/47713173/angular-service-and-httpclient-type-does-not-exist)
[problem solve2](https://stackoverflow.com/questions/47236963/no-provider-for-httpclient)

## Login page design v.2 & User info page design v.1

1. always login before enter personal pages
2. authguard
3. design user info page
4. enter wrong account or password will avoid login

## Routing

1. Seperate into three main routers (device, operation, admin)
2. Use lazy load
[reference](https://segmentfault.com/a/1190000009265310)

## password security using SHA-512 to secure



## Problem

1. item = document.getElementsByClassName() 該物件無法使用 item.style
  出現error `Property 'style' does not exist on type 'Element'`
    <b>Solution: </b>加上(item as HTMLElement).style 即可
    [reference](https://www.zhihu.com/question/59798764/answer/169043158)
2. npm install fail
   <b>Solution: </b>(1) `npm cache clean --force`
                (2) delete package.lock.json
                (3) `npm set registry https://registry.npmjs.org/`
3. 子路由中 lazy load 出現錯誤 `TypeError: undefined is not a function lazyload`
    <b>Solution: </b> Change to `{ path: 'device', loadChildren: () => deviceModule, },`
  [reference](https://github.com/angular/angular-cli/issues/9825)
4. to use angular material, add `@import "~@angular/material/prebuilt-themes/indigo-pink.css";` to `styles.scss`
  [reference](https://material.angular.io/guide/getting-started)
