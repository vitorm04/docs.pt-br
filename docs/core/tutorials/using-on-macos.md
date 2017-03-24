---
title: "Guia de Introdução ao .NET Core no macOS"
description: "Introdução ao .NET Core em macOS usando o Visual Studio Code"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: c4d1b7690ca87f2a1a9ced4d82e47aee2f7ecc9f
ms.lasthandoff: 03/07/2017

---

# <a name="getting-started-with-net-core-on-macos-using-visual-studio-code"></a>Introdução ao .NET Core em macOS usando o Visual Studio Code

Este documento fornece um tour das etapas e fluxo de trabalho para criar uma Solução do .NET Core usando o [Visual Studio Code](http://code.visualstudio.com).
Você aprenderá a criar projetos, criar testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](http://nuget.org).

Esse artigo usa o Visual Studio Code no Mac OS. Onde há diferenças, ele as destaca na plataforma Windows.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, você precisará instalar o [SDK do .NET Core](https://www.microsoft.com/net/core). O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do tempo de execução.

Você também precisará instalar o [Visual Studio Code](http://code.visualstudio.com).
No decorrer deste artigo, você também instalará as extensões que melhoram a experiência de desenvolvimento do .NET Core.

## <a name="getting-started"></a>Guia de Introdução

A fonte deste tutorial está disponível no [GitHub](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden).

Inicie o Visual Studio Code. Pressione Ctrl + '\`' (o caractere de acento grave) para abrir um terminal inserido no VS Code. (Como alternativa, você pode usar uma janela de terminal separada, se preferir).

Quando estiver pronto, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca. 

Vamos começar criando essas pastas. No terminal, crie um diretório “golden”. No VS Code, abra o diretório *golden*. Esse diretório é a raiz da sua solução. Execute o comando [`dotnet new`](../tools/dotnet-new.md) para criar uma nova solução:

```
dotnet new sln
```

Esse comando cria um arquivo *golden.sln* para toda a solução.

Sua próxima tarefa é criar a biblioteca. Na janela do terminal (no terminal inserido no VS Code ou em outro terminal), execute o cd para *golden/* e digite o comando:

```
dotnet new classlib -o library
```

Isso cria um projeto de biblioteca com dois arquivos: *library.csproj* e *Class1.cs* no diretório *library*. Você deseja que o projeto de biblioteca seja incluído na solução. Execute o comando [`dotnet sln`](../tools/dotnet-sln.md) para adicionar o projeto *library.csproj* re-cém-criado à solução:

```
dotnet sln add library/library.csproj
```

Vamos examinar o projeto criado. O arquivo *library.csproj* contém as seguintes informações:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Esse projeto de biblioteca usará a representação JSON de objetos, portanto, você deve adicionar uma referência ao pacote `Newtonsoft.Json` do NuGet. O comando `dotnet add` adiciona novos itens a um projeto. Para adicionar uma referência a um pacote NuGet, use o comando `package` e especifique o nome do pacote. 

```
dotnet add library package Newtonsoft.Json
```

Isso adiciona `Newtonsoft.Json` e suas dependências ao projeto de Biblioteca. Como alternativa, é possível editar manualmente o arquivo *library.csproj* e adicionar o seguinte nó:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1</Version>
  </PackageReference>
</ItemGroup>
```

Depois de terminar de adicionar essas dependências, você precisa instalar os pacotes no espaço de trabalho. Execute o comando `dotnet restore` para atualizar todas as dependências e grave um arquivo *obj/project.assets.json* no diretório do projeto. Esse arquivo contém a árvore de dependência completa de todas as dependências em seu projeto. Você não precisa ler este arquivo, ele é usado pelas ferramentas do SDK do .NET Core.

Agora, vamos atualizar o código C#. Vamos criar uma classe `Thing` que contém um método público. Este método retornará a soma de dois números, porém isso será feito ao converter esse número em uma cadeia de caracteres JSON e então desserializando-o. Renomeie o arquivo *Class1.cs* como *Thing.cs*. Em seguida, substitua o código existente (para a Class1 gerada pelo modelo) pelo seguinte:

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

Isso utiliza diversos recursos modernos de C#, tais como usos estáticos, membros com corpos de expressão e cadeias de caracteres interpoladas, sobre os quais você pode aprender na seção [Aprenda C#](../../csharp/index.md).

Agora que você atualizou o código, poderá criar a biblioteca usando `dotnet build`.

Agora você criou um arquivo *library.dll* em *golden/library/bin/Debug/netstandard1.4*.

### <a name="writing-the-test-project"></a>Escrevendo o projeto de teste

Vamos criar um projeto de teste para esta biblioteca que você compilou. Mude para o diretório *golden*. Execute `dotnet new xunit -o test-library` para criar um projeto de teste. É recomendável adicionar esse projeto à solução também executando `dotnet sln add test-library/test-library.csproj`.

Você precisará adicionar um nó de dependência para a biblioteca que você escreveu nas etapas acima. O comando `dotnet add reference` faz o seguinte:

```
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Se preferir, é possível editar manualmente o arquivo *test-library.csproj* e adicionar o seguinte nó:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

O nó `library` especifica que essa dependência deve ser resolvida para um projeto no espaço de trabalho atual. Sem especificar isso explicitamente, é possível que o projeto de teste seria compilado em um pacote NuGet de mesmo nome.

Agora que as dependências foram devidamente configuradas, vamos criar os testes para sua biblioteca. Abra *UnitTest1.cs* e substitua o conteúdo pelo seguinte código:

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

Agora, execute `dotnet restore` e `dotnet build`. Esses comandos localizarão todos os projetos recursivamente para restaurar as dependências e compilá-las.
Por fim, execute `dotnet test test-library/test-library.csproj` para executar os testes.
O executor de teste de console xUnit executará um teste e relatará que ele foi aprovado. 

### <a name="writing-the-console-app"></a>Escrevendo o aplicativo de console

No terminal, execute `dotnet new console -o app` para criar um novo aplicativo de console. Este projeto também faz parte da solução; portanto, execute `dotnet sln add app/app.csproj` para adicioná-lo à solução.

Seu aplicativo de console depende da biblioteca criada e testada nas etapas anteriores. É necessário indicar isso executando `dotnet add reference` novamente:

```
dotnet add app/app.csproj reference library/library.csproj
```

Execute `dotnet restore` para restaurar todas as dependências. Abra *program.cs* e substitua o conteúdo do método `Main` por esta linha:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Você precisará adicionar algumas diretivas `using` ao topo do arquivo:

```csharp
using static System.Console;
using Library;
```

Em seguida, execute `dotnet build`. Isso cria os assemblies e você pode digitar `dotnet run -p app/app.csproj` para ativar o executável.
O argumento `-p` para `dotnet run` especifica o projeto do aplicativo principal.

### <a name="debugging-your-application"></a>Depurando seu aplicativo

Você pode depurar seu código no VS Code usando a extensão do C#.
Instale essa extensão pressionando `F1` para abrir a paleta do VS Code. Digite `ext install` para ver a lista de extensões. Selecione a extensão de C#. (Mais detalhes estão disponíveis na página [Documentação da extensão C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).)

Depois de instalar a extensão, o VS Code solicitará que você reinicie o aplicativo para carregar a nova extensão. Depois de instalar a extensão, você pode abrir a guia do depurador (veja a figura).

![Depurador do VS Code](./media/using-on-macos/vscodedebugger.png)

Defina um ponto de interrupção na instrução `WriteLine` em `Main`. Você pode fazer isso pressionando a tecla `F9` ou clicando com o mouse na margem esquerda na linha escolhida para ser o ponto de interrupção. Abra o depurador pressionando o ícone de depuração à esquerda da tela do VS Code (veja a figura). Em seguida, pressione o botão Play para iniciar o aplicativo no depurador.

Você deverá atingir o ponto de interrupção. Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos. Verifique se a resposta é, na verdade, 42.

