---
title: Publicar aplicativos .NET Core com a CLI
description: Saiba como publicar um aplicativo .NET Core com as ferramentas da CLI (interface de linha de comando) do SDK do .NET Core.
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: 00064b774145e7267fe26b31ef3bba4d5271a5c3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181515"
---
# <a name="publish-net-core-apps-with-the-cli"></a>Publicar aplicativos .NET Core com a CLI

Este artigo demonstra como você pode publicar seu aplicativo .NET Core por meio da linha de comando. O .NET Core fornece três maneiras de publicar seus aplicativos. A implantação dependente de estrutura produz um arquivo .dll multiplataforma que usa o tempo de execução do .NET Core instalado localmente. O executável dependente de estrutura produz um executável específico da plataforma que usa o tempo de execução do .NET Core instalado localmente. O executável autossuficiente produz um executável específico da plataforma e inclui uma cópia local do tempo de execução do .NET Core.

Para obter uma visão geral desses modos de publicação, confira [Implantação de aplicativos .NET Core](index.md).

Procurando uma ajuda rápida de como usar a CLI? A tabela a seguir mostra alguns exemplos de como publicar o aplicativo. Especifique a estrutura de destino com o parâmetro `-f <TFM>` ou editando o arquivo de projeto. Para obter mais informações, confira [Noções básicas de publicação](#publishing-basics).

| Modo de publicação | Versão do SDK | Comando |
| ------------ | ----------- | ------- |
| Implantação dependente de estrutura | 2.x | `dotnet publish -c Release` |
| Executável dependente de estrutura | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Implantação autocontida      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\* Ao usar a versão 3.0 do SDK, o executável dependente de estrutura será o modo de publicação padrão durante a execução do comando `dotnet publish` básico. Isso só se aplica quando o projeto visa o **.NET Core 2.1** ou o **.NET Core 3.0**.

## <a name="publishing-basics"></a>Noções básicas de publicação

A configuração `<TargetFramework>` do arquivo de projeto especifica a estrutura de destino padrão quando o aplicativo é publicado. Altere a estrutura de destino para qualquer [TFM](../../standard/frameworks.md) (Moniker da Estrutura de Destino) válido. Por exemplo, se o projeto usa `<TargetFramework>netcoreapp2.2</TargetFramework>`, um binário direcionado ao .NET Core 2.2 é criado. O TFM especificado nessa configuração é o destino padrão usado pelo comando [`dotnet publish`](../tools/dotnet-publish.md).

Caso deseje definir mais de uma estrutura como destino, defina a configuração `<TargetFrameworks>` com mais de um valor TFM separado por ponto-e-vírgula. Publique uma das estruturas com o comando `dotnet publish -f <TFM>`. Por exemplo, se você tem `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` e executa `dotnet publish -f netcoreapp2.1`, um binário direcionado ao .NET Core 2.1 é criado.

Se não estiver definido de outro modo, o diretório de saída do comando [`dotnet publish`](../tools/dotnet-publish.md) será `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. O modo **CONFIGURAÇÃO DE BUILD** padrão é **Depuração**, a menos que seja alterado com o parâmetro `-c`. Por exemplo, `dotnet publish -c Release -f netcoreapp2.1` publica em `myfolder/bin/Release/netcoreapp2.1/publish/`.

Se você usa o SDK do .NET Core 3.0, o modo de publicação padrão para aplicativos direcionados ao .NET Core versões 2.1, 2.2 ou 3.0 é o executável dependente de estrutura.

Se você usa o SDK do .NET Core 2.1, o modo de publicação padrão para aplicativos direcionados ao .NET Core versões 2.1 ou 2.2 é a implantação dependente de estrutura.

### <a name="native-dependencies"></a>Dependências nativas

Se o aplicativo tiver dependências nativas, ele poderá não ser executado em um sistema operacional diferente. Por exemplo, se o aplicativo usar a API nativa do Windows, ele não será executado no macOS nem no Linux. Você precisará fornecer um código específico da plataforma e compilar um executável para cada plataforma.

Considere também que, se uma biblioteca referenciada tiver uma dependência nativa, o aplicativo poderá não ser executado em todas as plataformas. No entanto, é possível que um pacote NuGet referenciado tenha incluído versões específicas da plataforma para lidar com as dependências nativas necessárias para você.

Ao distribuir um aplicativo com dependências nativas, talvez você precise usar a opção `dotnet publish -r <RID>` para especificar a plataforma de destino na qual deseja publicar. Para obter uma lista de identificadores de tempo de execução, confira o [Catálogo do RID (Identificador de Tempo de Execução)](../rid-catalog.md).

Mais informações sobre binários específicos da plataforma são abordadas nas seções [Executável dependente de estrutura](#framework-dependent-executable) e [Implantação autossuficiente](#self-contained-deployment).

## <a name="sample-app"></a>Aplicativo de exemplo

Você pode usar o aplicativo a seguir para explorar os comandos de publicação. O aplicativo é criado pela execução dos seguintes comandos no terminal:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

O arquivo `Program.cs` ou `Program.vb` gerado pelo modelo de console precisa ser alterado para o seguinte:

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Quando você executa o aplicativo ([`dotnet run`](../tools/dotnet-run.md)), a seguinte saída é exibida:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Implantação dependente de estrutura

Para a CLI do SDK do .NET Core 2.x, a FDD (implantação dependente de estrutura) é o modo padrão para o comando `dotnet publish` básico.

Quando você publica o aplicativo como uma FDD, um arquivo `<PROJECT-NAME>.dll` é criado na pasta `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Para executar o aplicativo, navegue para a pasta de saída e use o comando `dotnet <PROJECT-NAME>.dll`.

O aplicativo está configurado para ser direcionado a uma versão específica do .NET Core. O tempo de execução do .NET Core de destino deve estar no computador em que você deseja executar o aplicativo. Por exemplo, se o aplicativo for direcionado ao .NET Core 2.2, qualquer computador no qual o aplicativo é executado precisará ter o tempo de execução do .NET Core 2.2 instalado. Conforme indicado na seção [Noções básicas de publicação](#publishing-basics), você pode editar o arquivo de projeto para alterar a estrutura de destino padrão ou para definir mais de uma estrutura como destino.

A publicação de uma FDD cria um aplicativo que efetua roll forward automaticamente para o último patch de segurança do .NET Core disponível no sistema que executa o aplicativo. Para obter mais informações sobre a associação de versão no tempo de compilação, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Executável dependente de estrutura

Para a CLI do SDK do .NET Core 3. x, o executável dependente da estrutura (FDE) é o modo padrão para `dotnet publish` o comando básico. Você não precisa especificar outros parâmetros, desde que queira definir o sistema operacional atual como destino.

Nesse modo, um host do executável específico da plataforma é criado para hospedar o aplicativo multiplataforma. Esse modo é semelhante ao FDD, pois o FDD exige um host na forma do comando `dotnet`. O nome de arquivo executável do host varia de acordo com a plataforma e recebe um nome semelhante a `<PROJECT-FILE>.exe`. Execute esse executável diretamente em vez de chamar `dotnet <PROJECT-FILE>.dll`, o que ainda é uma forma aceitável de executar o aplicativo.

O aplicativo está configurado para ser direcionado a uma versão específica do .NET Core. O tempo de execução do .NET Core de destino deve estar no computador em que você deseja executar o aplicativo. Por exemplo, se o aplicativo for direcionado ao .NET Core 2.2, qualquer computador no qual o aplicativo é executado precisará ter o tempo de execução do .NET Core 2.2 instalado. Conforme indicado na seção [Noções básicas de publicação](#publishing-basics), você pode editar o arquivo de projeto para alterar a estrutura de destino padrão ou para definir mais de uma estrutura como destino.

A publicação de um FDE cria um aplicativo que efetua roll forward automaticamente para o último patch de segurança do .NET Core disponível no sistema que executa o aplicativo. Para obter mais informações sobre a associação de versão no tempo de compilação, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md#framework-dependent-apps-roll-forward).

Você precisará (exceto para o .NET Core 3.x quando você definir a plataforma atual como destino) usar as seguintes opções com o comando `dotnet publish` para publicar um FDE:

- `-r <RID>` Essa opção usa um RID (identificador) para especificar a plataforma de destino. Para obter uma lista de identificadores de tempo de execução, confira o [Catálogo do RID (Identificador de Tempo de Execução)](../rid-catalog.md).

- `--self-contained false` Essa opção instrui o SDK do .NET Core a criar um executável como um FDE.

Sempre que você usa a opção `-r`, o caminho da pasta de saída é alterado para: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Se você usar o [aplicativo de exemplo](#sample-app), execute `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Esse comando cria o seguinte executável: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Reduza o tamanho total da implantação habilitando o **modo invariável de globalização**. Esse modo é útil para aplicativos que não têm reconhecimento global e que podem usar as convenções de formatação, as convenções de uso de maiúsculas, a comparação de cadeia de caracteres e a ordem de classificação da [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture). Para obter mais informações sobre o **modo invariável de globalização** e como habilitá-lo, confira [Modo invariável de globalização do .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Implantação autocontida

Quando você publica uma SCD (implantação autossuficiente), o SDK do .NET Core cria um executável específico da plataforma. A publicação de uma SCD inclui todos os arquivos do .NET Core necessários para executar seu aplicativo, mas não inclui as [dependências nativas do .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Essas dependências precisam estar presentes no sistema antes da execução do aplicativo.

A publicação de uma SCD cria um aplicativo que não efetua roll forward para o último patch de segurança disponível do .NET Core. Para obter mais informações sobre a associação de versão no tempo de compilação, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

É necessário usar as seguintes opções com o comando `dotnet publish` para publicar uma SCD:

- `-r <RID>` Essa opção usa um RID (identificador) para especificar a plataforma de destino. Para obter uma lista de identificadores de tempo de execução, confira o [Catálogo do RID (Identificador de Tempo de Execução)](../rid-catalog.md).

- `--self-contained true` Essa opção instrui o SDK do .NET Core a criar um executável como uma SCD.

> [!NOTE]
> Reduza o tamanho total da implantação habilitando o **modo invariável de globalização**. Esse modo é útil para aplicativos que não têm reconhecimento global e que podem usar as convenções de formatação, as convenções de uso de maiúsculas, a comparação de cadeia de caracteres e a ordem de classificação da [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture). Para obter mais informações sobre o **modo invariável de globalização** e como habilitá-lo, confira [Modo invariável de globalização do .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="see-also"></a>Consulte também

- [Visão geral da implantação de aplicativos .NET Core](index.md)
- [Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)
