https://youtu.be/GZzBH3ZRP4s

1. https://github.com/ohmyzsh/ohmyzsh 에서 베이직 인스톨레이션 수행

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

2. ZSH_DISABLE_COMPFIX관련 에러가 뜨면 아래를 수행

   ```
   code ~/.zshrc
   열린 파일에 젤 상단에 ZSH_DISABLE_COMPFIX="true" 를 추가
   ```

3. 결국 이걸 따라 가는 거임 (https://gist.github.com/kevin-smets/8568070)

   1. Get the iTerm color settings -> iTerm용이라서 아래의 것을 깔면 됨 (터미널-환경설정-프로파일-가져오기-Solarized Dark를 기본으로 설정)

      * https://github.com/tomislav/osx-terminal.app-colors-solarized

   2. ```
      git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
      ```

   3. Then edit your `~/.zshrc` and set `ZSH_THEME="powerlevel10k/powerlevel10k"`

      1. 기존 있는 ZSH_THEME 줄은 주석처리 해야함