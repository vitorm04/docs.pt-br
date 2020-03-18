---
title: 'Tutorial: Crie uma solução .NET Core no macOS usando o Visual Studio Code'
description: Este documento fornece as etapas e o fluxo de trabalho para criar uma Solução do .NET Core usando o Visual Studio Code.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156589"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Tutorial: Crie uma solução .NET Core no macOS usando o Visual Studio Code

Este documento fornece as etapas e o fluxo de trabalho para criar uma solução do .NET Core para macOS. Saiba como criar projetos, testes de unidade, usar as ferramentas de depuração e incorporar bibliotecas de terceiros por meio do [NuGet](https://www.nuget.org/).

> [!NOTE]
> Esse artigo usa o [Visual Studio Code](https://code.visualstudio.com) no macOS.

## <a name="prerequisites"></a>Pré-requisitos

Instale o [.NET Core SDK](https://dotnet.microsoft.com/download). O SDK do .NET Core inclui a versão mais recente da estrutura do .NET Core e do runtime.

Instale [o Visual Studio Code](https://code.visualstudio.com). No decorrer deste artigo, você vai instalar as extensões do Visual Studio Code que melhoram a experiência de desenvolvimento do .NET Core.

Instale a extensão Visual Studio Code C# abrindo visual studio code e pressionando <kbd>Fn</kbd>+<kbd>F1</kbd> para abrir a paleta Visual Studio Code. Digite **ext install** para ver a lista de extensões. Selecione a extensão de C#. Reinicie o Visual Studio Code para ativar a extensão. Para obter mais informações, consulte a [Documentação da Extensão de C# do Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Introdução

Neste tutorial, você criará três projetos: um projeto de biblioteca, testes para esse projeto de biblioteca e um aplicativo de console que usa a biblioteca. Você pode [visualizar ou baixar a fonte](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) deste artigo no repositório dotnet/samples no GitHub. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Inicie o Visual Studio Code. Pressione <kbd>Ctrl</kbd> <kbd>\`</kbd> (o caractere backquote ou backtick) ou selecione **'Exibir** > **terminal'** no menu para abrir um terminal incorporado no Visual Studio Code. Você ainda pode abrir um shell externo com o comando Explorer **Open in Command Prompt** **(Abrir no Terminal** no macOS ou Linux) se preferir trabalhar fora do Visual Studio Code.

Comece criando um arquivo de solução, que serve como um contêiner para um ou mais projetos do .NET Core. No terminal, execute [`dotnet new`](../tools/dotnet-new.md) o comando para criar uma nova solução *golden.sln* dentro de uma nova pasta chamada *golden*:

```dotnetcli
dotnet new sln -o golden
```

Navegue até a nova pasta *dourada* e execute o seguinte comando para criar um projeto de biblioteca, que produz dois arquivos,*library.csproj* e *Class1.cs*, na *pasta* biblioteca:

```dotnetcli
dotnet new classlib -o library
```

Execute [`dotnet sln`](../tools/dotnet-sln.md) o comando para adicionar o projeto *biblioteca.csproj* recém-criado à solução:

```dotnetcli
dotnet sln add library/library.csproj
```

O arquivo *library.csproj* contém as seguintes informações:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Nossos métodos da biblioteca serializam e desserializam os objetos no formato JSON. Para dar suporte à serialização e desserialização JSON, adicione uma referência ao pacote NuGet `Newtonsoft.Json`. O comando `dotnet add` adiciona novos itens a um projeto. Para adicionar uma referência a um [`dotnet add package`](../tools/dotnet-add-package.md) pacote NuGet, use o comando e especifique o nome do pacote:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Isso adiciona `Newtonsoft.Json` e suas dependências ao projeto de biblioteca. Como alternativa, edite manualmente o arquivo *library.csproj* e adicione o seguinte nó:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Execute [`dotnet restore`](../tools/dotnet-restore.md),[(veja nota)](#dotnet-restore-note)que restaura dependências e cria uma pasta *obj* dentro *da biblioteca* com três arquivos nela, incluindo um arquivo *project.assets.json:*

```dotnetcli
dotnet restore
```

Na pasta *library*, renomeie o arquivo *Class1.cs* como *Thing.cs*. Substitua o código pelo seguinte código:

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

A classe `Thing` contém um método público, `Get`, que retorna a soma de dois números, mas faz isso ao converter a soma em uma cadeia de caracteres e, em seguida, desserializá-los em um inteiro. Isso faz uso de uma série de recursos modernos c#, como [ `using static` diretivas,](../../csharp/language-reference/keywords/using-static.md) [membros encorpados de expressão](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)e [interpolação de cordas](../../csharp/language-reference/tokens/interpolated.md).

Construa a [`dotnet build`](../tools/dotnet-build.md) biblioteca com o comando. Isso produz um arquivo *library.dll* em *golden/library/bin/Debug/netstandard1.4*:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Criar um projeto de teste

Crie um projeto de teste para a biblioteca. Na pasta *golden*, crie um novo projeto de teste:

```dotnetcli
dotnet new xunit -o test-library
```

Adicione o projeto de teste à solução:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Adicione uma referência do projeto à biblioteca que você criou na seção anterior para que o compilador possa localizar e usar o projeto de biblioteca. Use [`dotnet add reference`](../tools/dotnet-add-reference.md) o comando:

```dotnetcli
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
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Observe que você declara que o valor 42 não é igual a 19+23 (ou 42) quando você cria o teste de unidade pela primeira vez (`Assert.NotEqual`), que falhará. Uma etapa importante na criação de testes de unidade é criar o teste para falhar uma vez primeiro para confirmar sua lógica.

Na pasta *golden*, execute os seguintes comandos:

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Esses comandos localizarão recursivamente todos os projetos para restaurar dependências, para compilá-las e para ativar o executor de teste xUnit para executar os testes. O teste único falha, conforme esperado.

Edite o arquivo *UnitTest1.cs* e altere a asserção de `Assert.NotEqual` para `Assert.Equal`. Execute o seguinte comando da pasta *golden* para executar o teste novamente, que é aprovado dessa vez:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Criar o aplicativo de console

O aplicativo de console criado ao longo das etapas a seguir usa uma dependência no projeto de biblioteca criado anteriormente e chama seu método de biblioteca quando é executado. Usando esse padrão de desenvolvimento, você verá como criar bibliotecas reutilizáveis para vários projetos.

Crie um novo aplicativo de console da pasta *golden*:

```dotnetcli
dotnet new console -o app
```

Adicione o projeto de aplicativo de console à solução:

```dotnetcli
dotnet sln add app/app.csproj
```

Crie a dependência na biblioteca executando o comando `dotnet add reference`:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Execute `dotnet restore` ([veja observação](#dotnet-restore-note)) para restaurar as dependências dos três projetos na solução. Abra *Program.cs* e substitua o conteúdo do método `Main` pela seguinte linha:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Adicione duas diretivas `using` à parte superior do arquivo *Program.cs*:

```csharp
using static System.Console;
using Library;
```

Execute o seguinte comando `dotnet run` para executar o executável, em que a opção `-p` para `dotnet run` especifica o projeto para o aplicativo principal. O aplicativo produz a cadeia de caracteres "A resposta é 42".

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Depurar o aplicativo

Defina um ponto de interrupção na instrução `WriteLine` no método `Main`. Faça isso pressionando a tecla <kbd>Fn</kbd>+<kbd>F9</kbd> quando `WriteLine` o cursor estiver sobre a linha ou clicando no mouse na margem esquerda na linha onde você deseja definir o ponto de ruptura. Um círculo vermelho será exibido na margem ao lado da linha de código. Quando o ponto de interrupção for atingido, a execução do código será interrompida *antes* de a linha do ponto de interrupção ser executada.

Abra a guia de depurador selecionando o ícone Debug na barra de ferramentas Visual Studio Code, selecionando **Exibir** > **depuração** na barra de menus ou usando o atalho do teclado <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D</kbd>:

![Depurador do Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

Pressione o botão Reproduzir para iniciar o aplicativo no depurador. Você criou um projeto de teste e um aplicativo neste projeto. O depurador pergunta qual projeto você quer iniciar. Selecione o projeto "app". O aplicativo inicia a execução e é executado até o ponto de interrupção, quando ele para. Inspecione o método `Get` e verifique se você transmitiu os argumentos corretos. Confirme se a resposta é 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
