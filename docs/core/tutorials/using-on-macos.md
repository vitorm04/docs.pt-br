---
title: "Guia de Introdução ao .NET Core no macOS"
description: "Introdução ao .NET Core em macOS usando o Visual Studio Code"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 2339be6aef7e2ff942f1f1999a12f48ee4a77ee8
ms.openlocfilehash: b9d53f32347572614a67e1cc432089f8e18d7cdf

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>Introdução ao .NET Core em macOS usando o Visual Studio Code

por [Bertrand Le Roy](https://github.com/bleroy), [Phillip Carter](https://github.com/cartermp) e [Bill Wagner](https://github.com/billwagner)

Contribuições de [Toni Solarin-Sodara](https://github.com/tsolarin)

Este documento fornece um tour das etapas e fluxo de trabalho para criar uma Solução do .NET Core usando o [Visual Studio Code](http://code.visualstudio.com).
Você aprenderá a criar projetos, criar testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](http://nuget.org).

Esse artigo usa o Visual Studio Code no Mac OS. Onde há diferenças, ele as destaca na plataforma Windows.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, você precisará instalar o [SDK do .NET Core](https://www.microsoft.com/net/core), atualmente versão de visualização. O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do tempo de execução.

Você também precisará instalar o [Visual Studio Code](http://code.visualstudio.com).
No decorrer deste artigo, você também instalará as extensões que melhoram a experiência de desenvolvimento do .NET Core.

Você poderá encontrar links para todas elas na [home page do .NET](http://dot.net).

## <a name="getting-started"></a>Guia de Introdução

A fonte deste tutorial está disponível no [GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden).

Inicie o Visual Studio Code. Pressione Ctrl + '\`' (o caractere de acento grave) para abrir um terminal inserido no VS Code. (Como alternativa, você pode usar uma janela de terminal separada, se preferir).

Quando estiver pronto, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca. Você seguirá uma estrutura de pasta padrão para os três projetos. Seguir essa estrutura de pasta padrão significa que as ferramentas do SDK do .NET Core entendem a relação entre seus projetos de código de produção e de teste. Isso torna sua experiência de desenvolvimento mais produtiva.

Vamos começar criando essas pastas. No terminal, crie um diretório “golden”. Nesse diretório, crie os diretórios `src` e `test`. Em `src`, criar os diretórios `app` e `library`. Em `test`, crie um diretório `test-library`. Você pode fazer isso usando o terminal no VS Code ou clicando na pasta pai do VS Code e selecionando o ícone “Nova pasta”.

No VS Code, abra o diretório “golden”. Esse diretório é a raiz da sua solução.

Em seguida, crie um arquivo `global.json` no diretório raiz para a solução.
O conteúdo de `global.json` é:

```json
{
    "projects": [
        "src",
        "test"
    ]
}
```

Neste ponto, sua árvore de diretório deve ser semelhante a:


```
/golden
|__global.json
|__/src
   |__/app
   |__/library
|__/test
   |__/test-library
```

### <a name="writing-the-library"></a>Escrevendo a biblioteca

Sua próxima tarefa é criar a biblioteca. Na janela do terminal (no terminal inserido no VS Code ou em outro terminal), use o cd para `golden/src/library` e digite o comando `dotnet new -t lib`.
Isso cria um projeto de biblioteca com dois arquivos: `project.json` e `Library.cs`.

`project.json` contém as seguintes informações:

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {},
  "frameworks": {
    "netstandard1.6": {
      "dependencies": {
        "NETStandard.Library": "1.6.0"
      }
    }
  }
}
```


Esse projeto de biblioteca usará a representação JSON de objetos, portanto, você deve adicionar uma referência ao pacote `Newtonsoft.Json` do NuGet. No`project.json`, adicione a versão pré-lançamento mais recente do pacote como uma dependência:

```json
"dependencies": {
    "Newtonsoft.Json": "9.0.1-beta1"
},
```

Depois de terminar de adicionar essas dependências, você precisa instalar os pacotes no espaço de trabalho. Execute o comando `dotnet restore` para atualizar todas as dependências e escrever um arquivo `project.lock.json` no diretório do projeto. Esse arquivo contém a árvore de dependência completa de todas as dependências em seu projeto. Você não precisa ler este arquivo, ele é usado pelas ferramentas do SDK do .NET Core.

Agora, vamos atualizar o código C#. Vamos criar uma classe `Thing` que contém um método público. Este método retornará a soma de dois números, porém isso será feito ao converter esse número em uma cadeia de caracteres JSON e então desserializando-o. Renomeie o arquivo `Library.cs` para `Thing.cs`. Em seguida, substitua o código existente (para a Class1 gerada pelo modelo) pelo seguinte:

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

Isso utiliza diversos recursos modernos de C#, tais como usings estáticos, membros com corpos de expressão e cadeias de caracteres interpoladas, sobre os quais você pode aprender na seção [Aprenda C#](../../csharp/index.md).

Agora que você atualizou o código, poderá criar a biblioteca usando `dotnet build`.

Agora você tem um arquivo `library.dll` de compilação em `golden/src/library/bin/Debug/netstandard1.6`.

### <a name="writing-the-test-project"></a>Escrevendo o projeto de teste

Vamos criar um projeto de teste para esta biblioteca que você compilou. Execute cd no diretório `test/test-library`. Execute `dotnet new -t xunittest` para criar um projeto de teste. 

Você precisará adicionar um nó de dependência para a biblioteca que você escreveu nas etapas acima. Abra `project.json` e atualize a seção de dependências para o seguinte (incluindo o nó `library`, que é o último nó abaixo):

```json
"dependencies": {
  "System.Runtime.Serialization.Primitives": "4.1.1",
  "xunit": "2.1.0",
  "dotnet-test-xunit": "1.0.0-rc2-192208-24",
  "library": {
    "target": "project"
  }
}
```

O nó `library` especifica que essa dependência deve ser resolvida para um projeto no espaço de trabalho atual. Sem especificar isso explicitamente, é possível que o projeto de teste seria compilado em um pacote NuGet de mesmo nome.

Agora que as dependências foram devidamente configuradas, vamos criar os testes para sua biblioteca. Abra `Tests.cs` e substitua seu conteúdo pelo seguinte código:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.Equal(42, new Thing().Get(19, 23));
        }
    }
}
```

Agora, execute `dotnet restore`, `dotnet build` e `dotnet test`.
O executor de teste de console xUnit executará um teste e relatará que ele foi aprovado. 

### <a name="writing-the-console-app"></a>Escrevendo o aplicativo de console

No seu terminal, execute cd para o diretório `golden/src/app`. Execute `dotnet new` para criar um novo aplicativo de console.

Seu aplicativo de console depende da biblioteca criada e testada nas etapas anteriores. Você precisa indicar isso editando `project.json` para adicionar essa dependência.  No nó `dependencies`, adicione o nó `library` da seguinte maneira:

```json
"dependencies": {
  "library": {
    "target": "project"
  }
}
```

O nó `project` é importante aqui, assim como era na biblioteca de teste. Ele indica que se trata de um projeto na solução atual e não um pacote NuGet.

Execute `dotnet restore` para restaurar todas as dependências. Abra `program.cs` e substitua o conteúdo do método `Main` por essa linha:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Você precisará adicionar algumas diretivas `using` ao topo do arquivo:

```csharp
using static System.Console;
using Library;
```

Em seguida, execute `dotnet build`. Isso cria os assemblies e você pode digitar `dotnet run` para ativar o executável.

### <a name="debugging-your-application"></a>Depurando seu aplicativo

Você pode depurar seu código no VS Code usando a extensão do C#.
Instale essa extensão pressionando `F1` para abrir a paleta do VS Code. Digite `ext install` para ver a lista de extensões. Selecione a extensão de C#. (Mais detalhes estão disponíveis na página [Documentação da extensão C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).)

Depois de instalar a extensão, o VS Code solicitará que você reinicie o aplicativo para carregar a nova extensão. Depois de instalar a extensão, você pode abrir a guia do depurador (veja a figura).

![Depurador do VS Code](./media/using-on-macos/vscodedebugger.png)


Quando iniciar o depurador, o VS Code instruirá você a configurar o depurador. Quando fizer isso, ele criará um diretório `.vscode` com dois arquivos: `tasks.json` e `launch.json`. Esses dois arquivos controlam a configuração do depurador. Na maioria dos projetos, esse diretório não está incluído no controle do código-fonte.
Ele está incluído no exemplo associado a este passo a passo para ver as edições que você precisa fazer.

Sua solução contém vários projetos, portanto, você deve modificar cada um desses arquivos para executar os comandos corretos. Primeiramente, abra `tasks.json`. A tarefa é executada de build padrão executa `dotnet build` no diretório de origem do espaço de trabalho. Em vez disso, você deve executá-lo no diretório `src/app`. Você precisa adicionar um nó `options` para definir o diretório de trabalho atual para:

```json
"options": {
    "cwd": "${workspaceRoot}/src/app"
}
```

Em seguida, você precisará abrir `launch.json` e atualizar o caminho do programa. Você verá um nó em “configurações” que descreve o programa. Você verá:

```json
"program": "${workspaceRoot}/bin/Debug/<target-framework>/<project-name.dll>",
```

Você alterará isso para:

```json
"program": "${workspaceRoot}/src/app/bin/Debug/netcoreapp1.0/app.dll",
```

Se estiver executando no Windows, será necessário atualizar o `project.json` do Aplicativo (no diretório `src/app`) para gerar arquivos PDB portáteis (isso acontece por padrão no Mac OSX e no Linux).
Adicione o nó `debugType` dentro de `buildOptions`. Você precisará adicionar o nó `debugType` em `project.json` para ambas as pastas `src/app` e `src/library`.

```json
  "buildOptions": {
    "debugType": "portable"
  },
```

Defina um ponto de interrupção na instrução `WriteLine` em `Main`. Você pode fazer isso pressionando a tecla `F9` ou clicando com o mouse na margem esquerda na linha escolhida para ser o ponto de interrupção. Abra o depurador pressionando o ícone de depuração à esquerda da tela do VS Code (veja a figura). Em seguida, pressione o botão Play para iniciar o aplicativo no depurador.

Você deverá atingir o ponto de interrupção. Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos. Verifique se a resposta é, na verdade, 42.



<!--HONumber=Nov16_HO4-->


