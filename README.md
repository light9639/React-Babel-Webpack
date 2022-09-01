# :zap: React-Babel-WebPack 설치
## :boom: 미리 설정할 것들
### :seedling: package.json 생성
```
npm init -y

yarn init -y
```

### :four_leaf_clover: 리액트관련 라이브러리 추가
```
npm install -D react react-dom

yarn add -D react react-dom
```

### :rose: 웹팩관련 라이브러리 추가
```
npm install -D webpack webpack-cli webpack-dev-server html-webpack-plugin

yarn add -D webpack webpack-cli webpack-dev-server html-webpack-plugin
```

### :leaves: 바벨관련 라이브러리 추가
```
npm install -D @babel/cli @babel/core @babel/preset-env @babel/preset-react

yarn add -D @babel/cli @babel/core @babel/preset-env @babel/preset-react
```

### :herb: 로더관련 라이브러리 추가
```
npm install -D babel-loader html-loader

yarn add -D babel-loader html-loader
```

### :black_nib: babel.config.js 파일 생성
```
module.exports = {
	presets: [
		'@babel/preset-env',
		'@babel/preset-react',
	]
}
```

### :black_nib: webpack.config.js 파일 생성
```
const path = require("path");
const HtmlWebPackPluzn = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/",
  output: {
	path: path.resolve(__dirname, "build"),
	filename: "bundle.js",
  },
  resolve: {
	modules: [path.join(__dirname, "src"), "node_modules"],
	alias: {
		react: path.join(__dirname, "node_modules", "react"),
	},
  },
  module: {
	rules: [
	  {
		test: /\.(js|jsx)$/,
		exclude: "/node_modules",
		use: {
		  loader: "babel-loader",
		},
	  },
	  {
		test: /\.css$/,
		use: [
		  {
			loader: "style-loader",
		  },
		  {
			loader: "css-loader",
		  },
		],
	  },
	  {
		test: /\.html$/,
		use: [
		  {
			loader: "html-loader",
			options: { minimize: true }
		  }
		]
	  }
	],
  },
  plugins: [
	new HtmlWebPackPlugin({
	  template: './src/index.html'
	})
  ]
};
```

## :boom: src 폴더에 index.html, index.js, App.js 파일 생성

### :memo: index.html
```
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>
<body>
	<div id="root"></div>
	<script src="./index.js"></script>
</body>
</html>
```

### :memo: index.js
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

### :memo: App.js
```
import React from 'react';

const App = () => {
	return (
		<>
			<div>
				React + Webpack + Babel
				<h1>Main Component Start!</h1>
				<h2>webpack watch test</h2>
			</div>
		</>
	)
};

export default App;
```

## :black_nib: package.json 파일 수정
```
"scripts": {
    "build": "webpack",
	"start": "npx webpack serve --mode development --port 3000"
}
```

## :white_check_mark: 기타 추가 설치
```
yarn add -D css-loader style-loader babel-loader sass-loader
```

## :rocket: 실행
```
yarn start
```