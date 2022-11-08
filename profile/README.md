# 전자정부 웹사이트 품질진단 자동화 서비스
  
<div align="center">
  
  ![favicons](https://user-images.githubusercontent.com/33208303/200622517-a5333dee-9b60-4935-9bd8-6de9b721c03c.png)

  <div display="flex">
      <img src="https://img.shields.io/badge/macOS-000000?style=flat-square&logo=macOS&logoColor=white"/>
      <a href="https://www.notion.so/pinkishincoloragain/276869bfc4974b2cbcd4fad719eac6b9" target="_blank">
        <img src="https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white"/>
      </a>
      <a href="https://www.figma.com/file/lwGemwXvKRDyM9LWtEN06k/Untitled?node-id=0%3A1" target="_blank">
        <img src="https://img.shields.io/badge/Figma-F24E1E?style=flat-square&logo=figma&logoColor=white"/>
      </a>
  </div>
  <div display="flex">
      <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=white"/>
      <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=white"/>
      <img src="https://img.shields.io/badge/Mui-007FFF?style=flat-square&logo=mui&logoColor=white"/>
      <img src="https://img.shields.io/badge/Chart.js-FF6384?style=flat-square&logo=chart.js&logoColor=white"/>
  </div>
  <div display="flex">
      <img src="https://img.shields.io/badge/SpringBoot-6DB33F?style=flat-square&logo=springboot&logoColor=white"/>
      <img src="https://img.shields.io/badge/Gradle-02303A?style=flat-square&logo=gradle&logoColor=white"/>
      <img src="https://img.shields.io/badge/MySql-4479A1?style=flat-square&logo=mysql&logoColor=white"/>
      <img src="https://img.shields.io/badge/Amazon EC2-FF9900?style=flat-square&logo=amazonec2&logoColor=white"/>
      <img src="https://img.shields.io/badge/Amazon RDS-527FFF?style=flat-square&logo=amazonrds&logoColor=white"/>
  </div>
</div>

## 소개
> QCA: Quality Control Automation

QCA는 수기로 모든 항목을 점검하는 현 전자정부 웹사이트 품질 진단 과정을 자동화하여 평가 결과와 개선점을 제시하는 서비스입니다. <br/>
Google Lighthouse API와 W3C Validator API를 이용해 행정안전부가 개정한 품질관리 수준진단 가이드에 따라 접근성, 호환성, 접속성, 개방성을 진단합니다.

---

## 개발 환경 및 라이브러리
### Client
```
React : 18.2.0
```
라이브러리 : [package.json](https://github.com/bsonCrew/QCA_Client/blob/main/package.json)

### Server
```
Java : 11
SpringBoot : 2.7.2
```
라이브러리 : [build.gradle](https://github.com/bsonCrew/QCA_Server/blob/main/build.gradle)

---

## 오픈 소스
### Google Lighthouse
![QXJ5lmcjHEFLTHg5B4o8](https://user-images.githubusercontent.com/33208303/200625540-42072a49-25e9-4a0c-a539-f2b4b2bd3cbb.jpg)

**Google**에서 2016.08.05부터 관리한 **오픈 소스 소프트웨어**로, 2022.11.09 기준 **오픈된 이슈 528개**, **닫힌 이슈 7914개**, **커밋 수 5433개**로 매우 활발히 발전하고 있습니다.
<br/>
웹 사이트를 다양한 접근성, 호환성, 접속성 지표를 사용하여 평가하고 그 결과를 얻는데 사용합니다.

### W3C Validator
![w3c](https://user-images.githubusercontent.com/33208303/200622895-243fc736-9f6a-4388-b761-be4b5e674ec0.png)

**W3C**에서 2014.10.13부터 관리한 **오픈 소스 소프트웨어**로, 2022.11.09 기준 **오픈된 이슈 157개**, **닫힌 이슈 999개**, **커밋 수 4177개**로 매우 활발히 발전하고 있습니다.
<br/>
웹 사이트 내 HTML / CSS / SVG 에서의 오류를 검출하는데 사용합니다.

---

## 프로젝트 사용법
### Client
```
git clone https://github.com/bsonCrew/QCA_Client.git
```

이후 프로젝트에서 사용할 의존성 설치 명령어는 다음과 같습니다.

#### npm

```sh
npm install
```

#### Yarn

```sh
yarn
```

localhost:3000에서 실행 시에는 다음과 같이 실행할 수 있습니다.

#### npm

```sh
npm start
```

#### Yarn

```sh
yarn start
```

### Server
```
git clone https://github.com/bsonCrew/QCA_Server.git
```

이후 프로젝트 폴더로 이동하여 프로젝트의 설정 정보를 추가해야 합니다.

서버는 Google Lighthouse API와 W3C Validator API를 사용해야 합니다. 따라서 NPM을 설치하고 해당 패키지를 다운받도록 합니다.
- 이때 W3C Validator는 QCA_Server 디렉토리의 상위 디렉토리에서 설치하도록 합니다.

```
// lighthouse 설치
npm install -g lighthouse

// Validator 설치
npm install --save vnu-jar
```

이후 다운받은 패키지들을 사용할 수 있도록 먼저 프로젝트 폴더 내의 `src/main/resources`에 `application.properties` 파일을 추가합니다.
그리고 아래와 같은 4개의 경로 변수를 지정합니다.

```
filePath={QCA_Server의 상위 디렉토리까지의 절대 경로}
utilPath={QCA_Server부터 프로젝트 내의 util 디렉토리까지의 절대 경로}/QCA_Server/src/main/java/com/example/QCA/QualityControlAutomation/common/util
vnuPath=/node_modules/vnu-jar/build/dist/vnu.jar
outputPath=/QCA_Server/src/output/
```

설정을 완료했다면, Lighthouse 결과물을 저장할 src/output 폴더를 생성합니다.

이제 설정이 완료되었습니다. 아래의 명령어를 통해 프로젝트를 정상적으로 빌드하고, 서버를 실행시킬 수 있습니다.

```
gradle build

java -jar QualityControlAutomation-0.0.1-SNAPSHOT.jar
```

## 기여
QCA는 Apache 2.0 License를 따르는 오픈 소스 프로젝트입니다. <br/>
아래의 가이드를 따라 QCA의 일원이 되어주세요.

[Setting up your project for healthy contributions](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions)

### 커밋 컨벤션
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

## FAQ
> **QCA는 어떤 방식으로 동작하나요?**

[데모](https://github.com/bsonCrew/.github/blob/main/%E1%84%83%E1%85%A6%E1%84%86%E1%85%A9.gif)로 확인하실 수 있습니다.
