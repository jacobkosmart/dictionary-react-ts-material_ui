# π Jacob Dictionary App

<a href="https://dic.jacobko.info/" target="_blank">Live Demo</a>

![Animation2](https://user-images.githubusercontent.com/28912774/131269977-3e227840-34c2-4f3b-8004-aba1d3ad7065.gif)

## π» 1.νλ‘μ νΈ μκ°

### π μ¬μ©κΈ°μ  λ° μΈμ΄

- Create React App with TypeScript

- Material UI

- Free Dictionary AIP

- Sass

- axios

### β° κ°λ° κΈ°κ°

2021-08-23 ~ 2021-08-29

## π 2.νλ‘μ νΈ λ΄μ©

### π μ£Όμ κΈ°λ₯

- λ¨μ΄μ λ», μμ, λμμ΄, λ°μμ¬μ΄λ (Only English) λ₯Ό κ²μν  μ μλ μ¬μ  App

- 12 κ°μ μΈμ΄ κ²μκ°λ₯

- Dark / Light mode μ§μ

- Fully responsive web design

#### π μ€μΉ ν¨ν€μ§

```bash
# CRA
npx create-react-app PROJECT --template typescript

# node-sass
yarn add node-sass@4.14.1


# material-ui
yarn add @material-ui/core @material-ui/icons
yarn add @material-ui/icons

# axios
yarn add axios

# CRACO
yarn add @craco/craco
yarn add craco-alias -D

# react-icons
yarn react-icons

# netlify
yarn add netlify-cli -g
```

## π 3.μ£Όμ μ½λ

1. μ λκ²½λ‘ λ° index.ts μ€μ 

- νλ‘μ νΈμ component κ° κΈΈμ΄μ§ κ²½μ°μ μλκ²½λ‘λ‘ νκ² λλ©΄ κ²½λ‘ μ€μ μ΄ λ³΅μ‘νκ² λλλ° index.ts νμΌμ λ§λ€μ΄ defaultλ κ²½λ‘λ‘ λ§λ€μ΄ μ£Όλ‘ src ν΄λλ₯Ό μ λκ²½λ‘λ‘ μ€μ ν©λλ€

> [μ λ κ²½λ‘ μ€μ  μμΈν λ³΄κΈ°(Jacob's DevLog)](https://jacobko.info/react/react_14/)

```ts
// index.ts

// μ΄λ°μμΌλ‘ index.ts μμ κ΄λ¦¬ν΄μ£Όκ² λλ©΄
export { default as Header } from "./Header";
export { default as Definitions } from "./Definitions";

// import ν λ μ©μνκ² κ΄λ¦¬ ν  μ μμ΅λλ€.
import { Definitions, Header } from "components/index";
```

2.  interface.ts νμΌμ ν΅ν΄ State, props, fetch λ API λ°μ΄ν° λ±μ type μ κ΄λ¦¬νμ¬ μ¬μ©νκΈ°

- TypeScript νμΌλ‘ type κ΄λ¦¬λ νμ μλλ€. interface.ts λΌλ νμΌμμ νλ‘μ νΈμμ μ¬μ©λλ type λ€μ κ΄λ¦¬ν΄μ export ν λ€μμ κ° component μμ import ν΄μ μ¬μ©νλ©΄ λ³΄λ€ μ©μ νκ² type μ€μ μ ν  μ μμ΅λλ€.

```ts
// in interface.ts

export interface HeaderProps {
  word: string;
  setWord: React.Dispatch<React.SetStateAction<string>>;
  category: string;
  setCategory: React.Dispatch<React.SetStateAction<string>>;
  lightMode: boolean;
}

export interface DefinitionsProps {
  word: string;
  category: string;
  fetchmeanings: InitApi[];
  phonetics?: Phonetics[];
  lightMode: boolean;
}

// Fetch Data interface

export interface InitApi {
  phonetics: Phonetics[];
  meanings: Meanings[];
  word: string;
}

export interface FetchData {
  word: string;
  meanings: Meanings;
  phonetics: Phonetics[];
}

export interface Phonetics {
  text: string;
  audio: string;
}

export interface Meanings {
  partOfSpeech: string;
  definitions: Definitions[];
}

export interface Definitions {
  definition: string;
  example: string;
  synonyms: string[];
}
```

```tsx
//  in Header.tsx component

import { HeaderProps } from "./interfaces";

const Header: React.FC<HeaderProps> = ({
  word,
  setWord,
  category,
  setCategory,
  lightMode,
}) => { ....
```

3. Dark Mode

- Material UI μμ μ κ³΅νλ dark mode μ€μ μ ν΅ν΄ μΉ νμ΄μ§μ dark mode λ°°κ²½ λ° κΈμ μμ μ½κ² λ§λ€ μ μμ΅λλ€.

```tsx
//  in Header.tsx

import {
  createTheme,
  MenuItem,
  TextField,
  ThemeProvider,
} from "@material-ui/core";

const Header: React.FC<HeaderProps> = ({
  word,
  setWord,
  category,
  setCategory,
  lightMode,
}) => {


  // Dark mode
  const darkTheme = createTheme({
    palette: {
      primary: {
        main: lightMode ? "#000" : "#fff",
      },
      type: lightMode ? "light" : "dark",
    },
  });


// ThemProvider component λ₯Ό μ¬μ©νμ¬ drakThem μ μ©νκΈ°

<ThemeProvider theme={darkTheme}>
  <TextField
    className="search"
    id="standard-basic"
    label="λ¨μ΄ μ°ΎκΈ°"
    value={word}
    onChange={(e) => setWord(e.target.value)}
  />
  <TextField
    select
    className="select"
    label="μΈμ΄ μ ν"
    value={category}
    onChange={(e) => handleChange(e.target.value)}
  >
    {categories.map((option) => (
      <MenuItem key={option.label} value={option.label}>
        {option.value}
      </MenuItem>
    ))}
  </TextField>
</ThemeProvider>
```

## π‘ 4. Reference

RoadsideCoder - [https://www.youtube.com/watch?v=Nz6Q21ypzT4&t=310s](https://www.youtube.com/watch?v=Nz6Q21ypzT4&t=310s)

Material UI - [https://material-ui.com/](https://material-ui.com/)

Free Dictionary API - [https://github.com/meetDeveloper/freeDictionaryAPI](https://github.com/meetDeveloper/freeDictionaryAPI)
