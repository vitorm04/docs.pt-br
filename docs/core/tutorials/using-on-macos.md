---
title: "Introdução ao .NET Core no macOS | Microsoft Docs"
description: "Este documento fornece as etapas e o fluxo de trabalho para criar uma Solução do .NET Core usando o Visual Studio Code."
keywords: .NET, .NET Core, Mac, macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.translationtype: Human Translation
ms.sourcegitcommit: 890c058bd09893c2adb185e1d8107246eef2e20a
ms.openlocfilehash: 6c08f16690a8c081ac17484c6bc7a331d9041356
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---

# <a name="getting-started-with-net-core-on-macos"></a>Guia de Introdução ao .NET Core no macOS

Este documento fornece as etapas e o fluxo de trabalho para criar uma solução do .NET Core para macOS. Saiba como criar projetos, testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](https://www.nuget.org/).

> [!NOTE]
> Esse artigo usa o [Visual Studio Code](http://code.visualstudio.com) no macOS.

## <a name="prerequisites"></a>Pré-requisitos

Instalar o [SDK do .NET Core](https://www.microsoft.com/net/core). O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do tempo de execução.

Instalar o [Visual Studio Code](http://code.visualstudio.com). No decorrer deste artigo, você também instalará as extensões do VS Code que melhorarão a experiência de desenvolvimento do .NET Core.

Instale a extensão C# do VS Code abrindo o VS Code e pressionando <kbd>F1</kbd> para abrir o palete do VS Code. Digite **ext install** para ver a lista de extensões. Selecione a extensão de C#. Reinicie o VS Code para ativar a extensão. Para obter mais informações, consulte a [Documentação da Extensão de C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="getting-started"></a>Introdução

Neste tutorial, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca. Você pode [exibir ou baixar a fonte](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) para este tópico no repositório dotnet/docs do GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Inicie o Visual Studio Code. Pressione <kbd>Ctrl</kbd>+<kbd>\`</kbd> (o caractere de acento grave) ou selecione **Exibir > Terminal Integrado** no menu para abrir um terminal inserido no VS Code. Você ainda pode abrir um shell externo com o comando **Open in Command Prompt** do Gerenciador (**Open in Terminal** no Mac ou no Linux) se preferir trabalhar fora do VS Code.

Comece criando um arquivo de solução, que serve como um contêiner para um ou mais projetos do .NET Core. No terminal, crie uma pasta *golden* e abra a pasta. Essa pasta é a raiz da sua solução. Execute o comando [`dotnet new`](../tools/dotnet-new.md) para criar uma nova solução, *golden.sln*:

```console
dotnet new sln
```

Na pasta *golden*, execute o seguinte comando para criar um projeto de biblioteca, que produz dois arquivos, *library.csproj* e *Class1.cs*, na pasta *library*:

```console
dotnet new classlib -o library
```

Execute o comando [`dotnet sln`](../tools/dotnet-sln.md) para adicionar o projeto *library.csproj* recém-criado à solução:

```console
dotnet sln add library/library.csproj
```

O arquivo *library.csproj* contém as seguintes informações:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

Nossos métodos da biblioteca serializam e desserializam os objetos no formato JSON. Para dar suporte à serialização e desserialização JSON, adicione uma referência ao pacote NuGet `Newtonsoft.Json`. O comando `dotnet add` adiciona novos itens a um projeto. Para adicionar uma referência a um pacote NuGet, use o comando [`dotnet add package`](../tools/dotnet-add-package.md) e especifique o nome do pacote:

```console
dotnet add library package Newtonsoft.Json
```

Isso adiciona `Newtonsoft.Json` e suas dependências ao projeto de biblioteca. Como alternativa, edite manualmente o arquivo *library.csproj* e adicione o seguinte nó:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

Execute [`dotnet restore`](../tools/dotnet-restore.md), que restaura as dependências e cria uma pasta *obj* dentro de *library* com três arquivos nele, incluindo um arquivo *project.assets.json*:

```console
dotnet restore
```

Na pasta *library*, renomeie o arquivo *Class1.cs* como *Thing.cs*. Substitua o código pelo seguinte:

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

A classe `Thing` contém um método público, `Get`, que retorna a soma de dois números, mas faz isso ao converter a soma em uma cadeia de caracteres e, em seguida, desserializá-los em um inteiro. Isso usa diversas funcionalidades modernas de C#, tais como [diretivas `using static`](../../csharp/language-reference/keywords/using-static.md), [membros aptos para expressão](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members) e [cadeias de caracteres interpoladas](../../csharp/language-reference/keywords/interpolated-strings.md).

Crie a biblioteca com o comando [`dotnet build`](../tools/dotnet-build.md). Isso produz um arquivo *library.dll* em *golden/library/bin/Debug/netstandard1.4*:

```console
dotnet build
```

## <a name="create-the-test-project"></a>Criar um projeto de teste

Crie um projeto de teste para a biblioteca. Na pasta *golden*, crie um novo projeto de teste:

```console
dotnet new xunit -o test-library
```

Adicione o projeto de teste à solução:

```console
dotnet sln add test-library/test-library.csproj
```

Adicione uma referência do projeto à biblioteca que você criou na seção anterior para que o compilador possa localizar e usar o projeto de biblioteca. Use o comando [`dotnet add reference`](../tools/dotnet-add-reference.md):

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

Como alternativa, edite manualmente o arquivo *test-library.csproj* e adicione o seguinte nó:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Agora que as dependências foram devidamente configuradas, crie os testes para sua biblioteca. Abra *UnitTest1.cs* e substitua o conteúdo pelo seguinte código:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Observe que você declara que o valor 42 não é igual a 19+23 (ou 42) quando você cria o teste de unidade pela primeira vez (`Assert.NotEqual`), que falhará. Uma etapa importante na criação de testes de unidade é criar o teste para falhar uma vez primeiro para confirmar sua lógica.

Na pasta *golden*, execute os seguintes comandos:

```console
dotnet restore
dotnet test test-library/test-library.csproj
```

Esses comandos localizarão recursivamente todos os projetos para restaurar dependências, para compilá-las e para ativar o executor de teste xUnit para executar os testes. O teste único falha, conforme esperado.

Edite o arquivo *UnitTest1.cs* e altere a asserção de `Assert.NotEqual` para `Assert.Equal`. Execute o seguinte comando da pasta *golden* para executar o teste novamente, que é aprovado dessa vez:

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Criar o aplicativo de console

O aplicativo de console criado ao longo das etapas a seguir usa uma dependência no projeto de biblioteca criado anteriormente e chama seu método de biblioteca quando é executado. Usando esse padrão de desenvolvimento, você verá como criar bibliotecas reutilizáveis para vários projetos.

Crie um novo aplicativo de console da pasta *golden*:

```console
dotnet new console -o app
```

Adicione o projeto de aplicativo de console à solução:

```console
dotnet sln add app/app.csproj
```

Crie a dependência na biblioteca executando o comando `dotnet add reference`:

```console
dotnet add app/app.csproj reference library/library.csproj
```

Execute `dotnet restore` para restaurar as dependências dos três projetos na solução. Abra *Program.cs* e substitua o conteúdo do método `Main` pela seguinte linha:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Adicione duas diretivas `using` à parte superior do arquivo *Program.cs*:

```csharp
using static System.Console;
using Library;
```

Execute o seguinte comando `dotnet run` para executar o executável, em que a opção `-p` para `dotnet run` especifica o projeto para o aplicativo principal. O aplicativo produz a cadeia de caracteres "A resposta é 42".

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Depurar o aplicativo

Defina um ponto de interrupção na instrução `WriteLine` no método `Main`. Faça isso pressionando a tecla <kbd>F9</kbd> quando o cursor estiver sobre a linha `WriteLine` ou clicando com o mouse na margem esquerda na linha em que deseja definir o ponto de interrupção. Um círculo vermelho será exibido na margem ao lado da linha de código. Quando o ponto de interrupção for atingido, a execução do código será interrompida *antes* de a linha do ponto de interrupção ser executada.

Abra a guia do depurador selecionando o ícone Depurar na barra de ferramentas do VS Code, selecionando **Exibir > Depurar** na barra de menus ou usando o atalho de teclado <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:

![Depurador do VS Code](./media/using-on-macos/vscodedebugger.png)

Pressione o botão Reproduzir para iniciar o aplicativo no depurador. O aplicativo inicia a execução e é executado até o ponto de interrupção, quando ele para. Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos. Confirme se a resposta é 42.

