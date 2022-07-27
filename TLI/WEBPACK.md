webpack
프론트엔드 애플리케이션 배포를 위해서 가장 많이 사용하는 번들러

여러 개의 파일을 하나의 파일로 합쳐주는 모듈 번들러

모듈 번들러? HTML, CSS, JavaScript 등의 자원을 전부 각각의 모듈로 보고 이를 조합해 하나의 묶음으로 번들링(빌드)하는 도구

Webpack에서의 모듈은 JavaScript의 모듈에만 국한하지 않습니다. HTML, CSS, 혹은 .jpg나 .png 같은 이미지 파일들도 전부 포함한 포괄적임



webpack을 쓰는 이유?
웹 애플리케이션의 빠른 로딩 속도와 높은 성능을 위함

웹페이지를 구성하는 코드의 양이 많은 것을 “무겁다”라고 표현하는데, 이것이 무거우면 무거울수록 웹 페이지의 로딩 속도와 성능은 저하가 됨


코드 난독화, 압축, 최적화 작업을 지원하기도 하여 사용자가 느끼기에 더욱 쾌적한 환경 및 보안까지 신경쓰면서 노출시킬 수 있다는 점에서 웹팩을 사용해야됨

webpack 핵심기능
1. Entry
webpack이 내부의 디펜던시 그래프를 생성하기 위해 사용해야 하는 모듈

//기본 값
module.exports = {
	...
  entry: "./src/index.js",
};

//지정 값
module.exports = {
	...
  entry: "./src/script.js",
};
2. Output
Output 속성은 생성된 번들을 내보낼 위치와 이 파일의 이름을 지정하는 방법을 webpack에 알려주는 역할

const path = require('path');

module.exports = {
	...
  output: {
    path: path.resolve(__dirname, "docs"), // 절대 경로로 설정을 해야 합니다. 
    filename: "app.bundle.js",
    clean: true
  },
};
3. Loader
Webpack이 다른 유형의 파일을 처리하거나, 그들을 유효한 모듈로 변환해 애플리케이션에 사용하거나 디펜던시 그래프에 추가할 수 있음

module.exports = {
	...
 module: {
   rules: [
     {
       test: /\.css$/,
       use: [MiniCssExtractPlugin.loader, "css-loader"],
       exclude: /node_modules/,
     },
   ],
 },
};
4. Plugin
Plugins를 사용하면 번들을 최적화하거나 에셋을 관리하고, 또는 환경변수 주입 등의 광범위한 작업을 수행할 수 있음

const webpack = require('webpack');
const HtmlWebpackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

module.exports = {
  ...
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, "src", "index.html"),
    }),
    new MiniCssExtractPlugin(),
  ],
};