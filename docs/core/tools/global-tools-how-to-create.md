---
title: 'Tutorial: Crie uma ferramenta .NET Core'
description: Aprenda a criar uma ferramenta .NET Core. Uma ferramenta é um aplicativo de console que é instalado usando o .NET Core CLI.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156719"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Tutorial: Crie uma ferramenta .NET Core usando o .NET Core CLI

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

Este tutorial ensina como criar e empacotar uma ferramenta .NET Core. O .NET Core CLI permite que você crie um aplicativo de console como uma ferramenta, que outros podem instalar e executar. As ferramentas .NET Core são pacotes NuGet instalados a partir do .NET Core CLI. Para obter mais informações sobre ferramentas, consulte [a visão geral das ferramentas .NET Core](global-tools.md).

A ferramenta que você criará é um aplicativo de console que leva uma mensagem como entrada e exibe a mensagem junto com linhas de texto que criam a imagem de um robô.

Este é o primeiro de uma série de três tutoriais. Neste tutorial, você cria e empacota uma ferramenta. Nos próximos dois tutoriais você [usa a ferramenta como uma ferramenta global](global-tools-how-to-use.md) e usa a ferramenta como uma ferramenta [local.](local-tools-how-to-use.md)

## <a name="prerequisites"></a>Pré-requisitos

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou uma versão posterior.

  Este tutorial e o tutorial a seguir [para ferramentas globais](global-tools-how-to-use.md) aplicam-se às versões .NET Core SDK 2.1 e posteriores porque as ferramentas globais estão disponíveis a partir dessa versão. Mas este tutorial pressupõe que você instalou o 3.1 ou posterior para que você tenha a opção de continuar no [tutorial de ferramentas locais](local-tools-how-to-use.md). As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0. Os procedimentos para criar uma ferramenta são os mesmos, quer você a use como uma ferramenta global ou como uma ferramenta local.
  
- Um editor de texto ou editor de código de sua escolha.

## <a name="create-a-project"></a>Criar um projeto

1. Abra um prompt de comando e crie uma pasta chamada *repositório*.

1. Navegue até a pasta do *repositório* e digite o seguinte comando:

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   O comando cria uma nova pasta chamada *microsoft.botsay* a pasta *de repositório.*

1. Navegue até a pasta *microsoft.botsay.*

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Adicionar o código

1. Abra `Program.cs` o arquivo com seu editor de código.

1. Adicione a `using` seguinte diretiva à parte superior do arquivo:

   ```csharp
   using System.Reflection;
   ```

1. Substitua `Main` o método pelo seguinte código para processar os argumentos da linha de comando para o aplicativo.

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   Se nenhum argumento for aprovado, uma mensagem de ajuda curta será exibida. Caso contrário, todos os argumentos são concatenados em uma `ShowBot` única seqüência e impressos chamando o método que você cria na próxima etapa.

1. Adicione um novo `ShowBot` método chamado que leva um parâmetro de seqüência. O método imprime a mensagem e uma imagem de um robô usando linhas de texto.

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. Salve suas alterações.

## <a name="test-the-application"></a>Testar o aplicativo

Execute o projeto e veja a saída. Experimente essas variações na linha de comando para ver diferentes resultados:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Todos os argumentos após o delimitador `--` são passados para o aplicativo.

## <a name="package-the-tool"></a>Empacote a ferramenta

Antes de empacotar e distribuir o aplicativo como uma ferramenta, você precisa modificar o arquivo do projeto.

1. Abra o arquivo *microsoft.botsay.csproj* e adicione três novos nodes XML ao final do `<PropertyGroup>` nó:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`é um elemento opcional que especifica o comando que invocará a ferramenta depois de instalada. Se esse elemento não for fornecido, o nome de comando da ferramenta é o nome do arquivo do projeto sem a extensão *.csproj.*

   `<PackageOutputPath>`é um elemento opcional que determina onde o pacote NuGet será produzido. O pacote NuGet é o que o .NET Core CLI usa para instalar sua ferramenta.

   O arquivo do projeto agora se parece com o seguinte exemplo:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. Crie um pacote NuGet executando o comando [dotnet pack:](dotnet-pack.md)

   ```dotnetcli
   dotnet pack
   ```

   O arquivo *microsoft.botsay.1.0.0.nupkg* é criado na `<PackageOutputPath>` pasta identificada pelo valor do arquivo *microsoft.botsay.csproj,* que neste exemplo é a pasta *./nupkg.*
  
   Quando você quiser liberar uma ferramenta publicamente, você pode carregá-la para `https://www.nuget.org`. Uma vez que a ferramenta esteja disponível no NuGet, os desenvolvedores podem instalar a ferramenta usando o comando [dotnet tool install.](dotnet-tool-install.md) Para este tutorial você instala o pacote diretamente da pasta *nupkg* local, para que não haja necessidade de carregar o pacote para NuGet.

## <a name="troubleshoot"></a>Solucionar problemas

Se você receber uma mensagem de erro ao seguir o tutorial, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um aplicativo de console e o embalou como uma ferramenta. Para aprender como usar a ferramenta como ferramenta global, avance para o próximo tutorial.

> [!div class="nextstepaction"]
> [Instale e use uma ferramenta global](global-tools-how-to-use.md)

Se preferir, você pode pular o tutorial de ferramentas globais e ir diretamente para o tutorial de ferramentas locais.

> [!div class="nextstepaction"]
> [Instale e use uma ferramenta local](local-tools-how-to-use.md)
