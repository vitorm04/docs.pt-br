---
title: Como criar uma Ferramenta Global do .NET Core
description: Descreve como criar uma Ferramenta Global. A Ferramenta Global é um aplicativo de console instalado por meio da CLI do .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3860aad5e2c13714298d50bb9ac10daec3aadf01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47231193"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Criar uma Ferramenta Global do .NET Core usando a CLI do .NET Core

Este artigo ensina a criar e empacotar uma ferramenta Global do .NET Core. A CLI do .NET Core permite que você crie um aplicativo de console como uma Ferramenta Global, o que outras pessoas podem instalar e executar facilmente. Ferramentas Globais do .NET Core são pacotes NuGet que são instalados por meio da CLI do .NET Core. Para obter mais informações sobre as Ferramentas Globais, veja [Visão geral de Ferramentas Globais do .NET Core][global-tool-info].

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Criar um projeto

Este artigo usa a CLI do .NET Core para criar e gerenciar um projeto.

Nossa ferramenta de exemplo será um aplicativo de console que gera um bot ASCII e imprime uma mensagem. Primeiro, crie um novo Aplicativo de Console do .NET Core.

```console
dotnet new console -o botsay
```

Navegue até o diretório `botsay` criado pelo comando anterior.

## <a name="add-the-code"></a>Adicionar o código

Abra o arquivo `Program.cs` com o seu editor de texto favorito, como o `vim` ou o [Visual Studio Code](https://code.visualstudio.com/).

Adicione a diretiva `using` a seguir na parte superior do arquivo, isso ajuda a reduzir o código para exibir as informações de versão do aplicativo.

```csharp
using System.Reflection;
```

Em seguida, mova para baixo até o método `Main`. Substitua o método com o código a seguir para processar os argumentos de linha de comando para seu aplicativo. Se nenhum argumento foi passado, uma breve mensagem de ajuda é exibida. Caso contrário, todos os argumentos são transformados em uma cadeia de caracteres e impressos com o bot.

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

### <a name="create-the-bot"></a>Criar o bot

Em seguida, adicione um novo método chamado `ShowBot` que usa um parâmetro de cadeia de caracteres. Esse método imprime a mensagem e o bot de ASCII. O código de bot ASCII foi obtido do exemplo [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs).

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

### <a name="test-the-tool"></a>Testar a ferramenta

Execute o projeto e veja a saída. Experimente estas variações de linha de comando para ver resultados diferentes:

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Todos os argumentos após o delimitador `--` são passados para o aplicativo.

## <a name="setup-the-global-tool"></a>Configurar a ferramenta global

Antes de poder empacotar e distribuir o aplicativo como uma Ferramenta Global, você precisa modificar o arquivo de projeto. Abra o arquivo `botsay.csproj` e adicione três novos nós XML ao nó `<Project><PropertyGroup>`:

- `<PackAsTool>`  
[OBRIGATÓRIO] Indica que o aplicativo será empacotado para instalação como uma Ferramenta Global.

- `<ToolCommandName>`  
[OPCIONAL] Um nome alternativo para a ferramenta, caso contrário, o nome do comando para a ferramenta será nomeado após o arquivo de projeto. Você pode ter várias ferramentas em um pacote, sendo que escolher um nome amigável e exclusivo ajuda a diferenciar de outras ferramentas no mesmo pacote.

- `<PackageOutputPath>`  
[OPCIONAL] O local em que o pacote NuGet será produzido. O pacote NuGet é o que as Ferramentas Globais da CLI do .NET Core usam para instalar a ferramenta.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

Embora `<PackageOutputPath>` seja opcional, use-o neste exemplo. Verifique se você o definiu: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Em seguida, crie um pacote NuGet para seu aplicativo.

```console
dotnet pack
```

O arquivo `botsay.1.0.0.nupkg` é criado na pasta identificada pelo valor XML `<PackageOutputPath>` do arquivo `botsay.csproj`, que neste exemplo é a pasta `./nupkg`. Isso torna mais fácil instalar e testar. Quando você desejar liberar uma ferramenta para o público, carregue-a para [https://www.nuget.org](https://www.nuget.org).

Agora que você tem um pacote, instale a ferramenta desse pacote: 

```console
dotnet tool install --global --add-source ./nupkg botsay
```

O parâmetro `--add-source` instrui a CLI do .NET Core a usar temporariamente a pasta `./nupkg` (nossa pasta `<PackageOutputPath>`) como uma fonte adicional de feed para pacotes NuGet. Para obter mais informações sobre a instalação das Ferramentas Globais, veja [Visão geral de Ferramentas Globais do .NET Core][global-tool-info].

Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Agora você deve ser capaz de digitar `botsay` e obter uma resposta da ferramenta.

> [!NOTE]
> Se a instalação for bem-sucedida, mas não for possível usar o comando `botsay`, talvez você precise abrir um novo terminal para atualizar o PATH.

## <a name="remove-the-tool"></a>Remover a ferramenta

Quando terminar suas experiências com a ferramenta, você poderá removê-la com o comando a seguir:

```console
dotnet tool uninstall -g botsay
```

[global-tool-info]: global-tools.md
