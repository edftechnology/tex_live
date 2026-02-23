# Como instalar/configurar o `Tex Live` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar o `Tex Live` no `Linux Ubuntu`.

## _Abstract_

_This document contains the main commands and configurations for configuring/installing `Tex Live` on `Linux Ubuntu`._

### Construído com

Esta seção deve listar todas as principais estruturas/bibliotecas usadas para inicializar seu projeto, bem como a sequência de instalação. Deixe quaisquer complementos/plugins para a seção de agradecimentos. Aqui estão alguns exemplos.

* [![Texlive](https://img.shields.io/badge/Texlive-3776AB?style=flat-square&logo=latex&logoColor=white)](https://tug.org/texlive/)

* [![JabRef](https://img.shields.io/badge/JabRef-44A833?style=flat-square&logo=latex&logoColor=white)](https://www.jabref.org/)

* [![Texstudio](https://img.shields.io/badge/Texstudio-008080?style=flat-square&logo=latex&logoColor=white)](https://www.texstudio.org/)

* [![MathPix](https://img.shields.io/badge/MathPix-008080?style=flat-square&logo=MathPix&logoColor=white)](https://mathpix.com/)

<p align="right">(<a href="#readme-top">voltar ao topo</a>)</p>


## Descrição [2]

### `Tex Live`

O `TeX Live` é uma distribuição abrangente e amplamente utilizada do sistema de composição de documentos TeX, desenvolvido por Donald Knuth. Ele inclui uma vasta coleção de pacotes, fontes e utilitários relacionados ao TeX, tornando-o uma escolha popular entre autores e profissionais que precisam criar documentos de alta qualidade, como artigos acadêmicos, livros, relatórios técnicos e documentos matemáticos. O `TeX Live` está disponível em várias plataformas, incluindo Windows, macOS e Linux, e oferece suporte a uma variedade de idiomas e scripts. É uma ferramenta essencial para aqueles que desejam produzir documentos tipograficamente precisos e bem formatados.


## 1. Configurar/Instalar/Usar o `Tex Live` no `Linux Ubuntu` [1]

Você pode instalar o `Tex Live` no `Linux Ubuntu` usando o gerenciador de pacotes `apt`. Aqui está um guia passo a passo:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```


2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    
    ```bash
    sudo apt clean
    ``` 
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do cache local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:
    
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:
    
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: 
    
    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes:
    
    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    
    ```bash
    sudo apt clean
    ``` 
    
    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  
    
    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`:
    
    ```bash
    sudo apt full-upgrade -y
    ```

3. **Instale o `Tex Live`:** Agora você pode instalar o `Tex Live` executando o seguinte comando:

    ```bash
    sudo apt install texlive-full -y
    ```

- Isso instalará o `Tex Live` completo, que inclui uma ampla variedade de pacotes e bibliotecas para a criação de documentos `LaTeX`.

4. **Verifique a instalação:** Depois que a instalação estiver concluída, você pode verificar se o `Tex Live` foi instalado corretamente executando o seguinte comando:

    ```bash
    tex --version
    ```

- Isso deve exibir informações sobre a versão do `Tex Live` instalada.

Agora você tem o `Tex Live` instalado no seu sistema `Linux Ubuntu` e pode começar a criar documentos `LaTeX`. Lembre-se de usar um editor `LaTeX`, como o `TeXworks`, para criar e compilar seus documentos.


## 1.1 Código completo para configur/instalar/usar

Para configurar/instalar/usar o `Tex Live` no `Linux Ubuntu` sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt clean
    sudo apt autoclean
    sudo apt autoremove -y
    sudo apt update
    sudo apt --fix-broken install
    sudo apt clean
    sudo apt list --upgradable
    sudo apt full-upgrade -y
    sudo apt install texlive-full -y
    tex --version
    ```


## 2. Instalar pacote do `LaTeX` pelo `Terminal Emulator`

Para instalar um pacote do `LaTeX` pelo `Terminal Emulator`

### 2.1 Como descobrir qual pacote `apt` fornece `<nome_do_pacote>.sty`

1. Abrir um `Terminal Emulator` e execute:

    ```bash
    sudo apt update
    ```

    para atualizar a lista de pacotes.

2. Procure pelo arquivo `<nome_do_pacote>.sty` via `apt-file` ou `apt-cache`. Se você ainda não tiver o `apt-file` instalado, faça:

    ```bash
    sudo apt install apt-file -y
    sudo apt-file update
    ```

3. Então busque:

    ```bash
    apt-file search algorithm.sty
    ```

    Isso vai listar algo como:

    ```bash
    texlive-latex-extra: /usr/share/texlive/texmf-dist/tex/latex/<nome_do_pacote>.sty
    ```

    Ou seja, o pacote responsável por fornecer o `<nome_do_pacote>.sty` é o `texlive-latex-extra` (ou, em algumas versões `texlive-latex-recommended`, mas normalmente o `\texttt{<nome_do_pacote>}` fica em `\texttt{texlive-latex-extra}`).


### 2.2 Como instalar pelo `apt`
 
1. Uma vez sabido que o pacote correto é o `texlive-latex-extra`, basta executar:

    ```bash
    sudo apt update
    sudo apt install texlive-latex-extra -y
    ```

    Após isso, o arquivo `<nome_do_pacote>.sty` estará instalado na árvore do `TeX Live` do sistema (em `/usr/share/texlive/...`) e o `LaTeX` passará a encontrá-lo normalmente.

2. Se você quiser garantir que outros pacotes comuns de `LaTeX` também estejam presentes, pode instalar ainda:

    ```bash
    sudo apt install texlive-science texlive-fonts-recommended texlive-latex-recommended -y
    ```

    Mas, no mínimo, para resolver o erro do `<nome_do_pacote>.sty`, precise apenas de:

    ```bash
    sudo apt install texlive-latex-extra
    ```


### 2.3 Testar se o `tlmgr` está disponível 

1. **Testar se o `tlmgr` está disponível**: No `Terminal Emulator`, digite:

    ```bash
    tlmgr --version
    ```

    Se aparecer informação sobre a versão do `TeX Live Manager`, você já pode prosseguir. Caso receba `“command not found”`, pode ser que:

    Você não tenha instalado o `TeX Live` via instalador oficial (por exemplo, instalou somente com o gerenciador da sua distribuição `Linux`).

    O diretório bin do `TeX Live` não esteja no seu `$PATH`.

2. **Procurar por um pacote específico**: Suponha que você queira saber se o pacote que oferece, por exemplo, o `algorithm.sty` está presente. No `Terminal Emulator`, execute:

    ```bash
    tlmgr search --file algorithm.sty
    ```
    
    Isso procurará em toda a coleção do `TeX Live` (local e repositório _online_, se configurado) e listará o(s) pacote(s) que fornecem aquele arquivo. Exemplo de saída:

    ```bash
    collection-latexrecommended: texmf-dist/tex/latex/algorithms/algorithm.sty
    algorithms: texmf-dist/tex/latex/algorithms/algorithm.sty
    ```
    
    Na prática, você verá algo parecido com:

    ```bash
    algorithms: /usr/local/texlive/2023/texmf-dist/tex/latex/algorithms/algorithm.sty
    ```

    ou, caso não esteja instalado localmente, apenas exibirá a referência ao repositório _online_.

3. **Verificar informação sobre um pacote**: Se você já sabe o nome aproximado do pacote (por exemplo, `“algorithms”`), pode rodar:

    ```bash
    tlmgr info algorithms
    ```
    
    Isso mostra detalhes como versão instalada, descrição e nome completo do pacote no repositório `TeX Live`.

4. **Instalar o pacote faltante**: Se ao buscar (`“search”`) você descobriu que o pacote que oferece `algorithm.sty` é o `algorithms`, basta rodar:

    ```bash
    sudo tlmgr install algorithms
    ```

Após isso, o `TeX Live Manager` resolverá dependências e fará o _download_/instalação. Quando terminar, o `algorithm.sty` estará disponível para qualquer documento.

## Referências

[1] OPEN AI. ***Instalar o `tex live` no `linux ubuntu` pelo `terminal emulator`.*** Disponível em: <https://chat.openai.com/c/5341e112-5d65-410b-bec5-00b9a61a6650> (texto adaptado). ChatGPT. Acessado em: 29/09/2023 18:56.

[2] OPEN AI. ***Vs code: editor popular.*** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). ChatGPT. Acessado em: 14/11/2023 18:56.

