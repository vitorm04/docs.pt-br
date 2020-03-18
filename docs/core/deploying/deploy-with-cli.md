---
title: Publicar aplicativos com o .NET Core CLI
description: Aprenda a publicar um aplicativo .NET Core usando os comandos .NET Core CLI.
author: thraka
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f4c2a4ccf551c53e4aa4e125cb5720d6f1cc9601
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399066"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a>Publique os aplicativos .NET Core com o .NET Core CLI

Este artigo demonstra como você pode publicar seu aplicativo .NET Core por meio da linha de comando. O .NET Core fornece três maneiras de publicar seus aplicativos. A implantação dependente de estrutura produz um arquivo .dll multiplataforma que usa o runtime do .NET Core instalado localmente. O executável dependente de estrutura produz um executável específico da plataforma que usa o runtime do .NET Core instalado localmente. O executável autossuficiente produz um executável específico da plataforma e inclui uma cópia local do runtime do .NET Core.

Para obter uma visão geral desses modos de publicação, confira [Implantação de aplicativos .NET Core](index.md).

Procurando uma ajuda rápida de como usar a CLI? A tabela a seguir mostra alguns exemplos de como publicar o aplicativo. Especifique a estrutura de destino com o parâmetro `-f <TFM>` ou editando o arquivo de projeto. Para obter mais informações, confira [Noções básicas de publicação](#publishing-basics).

| Modo de publicação | Versão do SDK | Comando |
| ------------ | ----------- | ------- |
| Implantação dependente de estrutura | 2. x | `dotnet publish -c Release` |
| Executável dependente de estrutura | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Implantação autocontida      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\* Ao usar a versão 3.0 do SDK, o executável dependente de estrutura será o modo de publicação padrão durante a execução do comando `dotnet publish` básico. Isso só se aplica quando o projeto visa o **.NET Core 2.1** ou o **.NET Core 3.0**.

## <a name="publishing-basics"></a>Noções básicas de publicação

A configuração `<TargetFramework>` do arquivo de projeto especifica a estrutura de destino padrão quando o aplicativo é publicado. Altere a estrutura de destino para qualquer [TFM](../../standard/frameworks.md) (Moniker da Estrutura de Destino) válido. Por exemplo, se o projeto usa `<TargetFramework>netcoreapp2.2</TargetFramework>`, um binário direcionado ao .NET Core 2.2 é criado. O TFM especificado nesta configuração é [`dotnet publish`](../tools/dotnet-publish.md) o alvo padrão usado pelo comando.

Caso deseje definir mais de uma estrutura como destino, defina a configuração `<TargetFrameworks>` com mais de um valor TFM separado por ponto-e-vírgula. Publique uma das estruturas com o comando `dotnet publish -f <TFM>`. Por exemplo, se você tem `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` e executa `dotnet publish -f netcoreapp2.1`, um binário direcionado ao .NET Core 2.1 é criado.

A menos que seja definido de [`dotnet publish`](../tools/dotnet-publish.md) outra `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`forma, o diretório de saída do comando é . O modo **CONFIGURAÇÃO DE BUILD** padrão é **Depuração**, a menos que seja alterado com o parâmetro `-c`. Por exemplo, `dotnet publish -c Release -f netcoreapp2.1` publica em `myfolder/bin/Release/netcoreapp2.1/publish/`.

Se você usar o .NET Core SDK 3.0 ou posterior, o modo de publicação padrão para aplicativos que visam as versões .NET Core 2.1, 2.2, 3.0 ou uma versão posterior, é executável dependente de estrutura.

Se você usar o .NET Core SDK 2.1, o modo de publicação padrão para aplicativos que visam as versões .NET Core 2.1 e 2.2 é a implantação dependente da estrutura.

### <a name="native-dependencies"></a>Dependências nativas

Se o aplicativo tiver dependências nativas, ele poderá não ser executado em um sistema operacional diferente. Por exemplo, se o aplicativo usar a API nativa do Windows, ele não será executado no macOS nem no Linux. Você precisará fornecer um código específico da plataforma e compilar um executável para cada plataforma.

Considere também que, se uma biblioteca referenciada tiver uma dependência nativa, o aplicativo poderá não ser executado em todas as plataformas. No entanto, é possível que um pacote NuGet referenciado tenha incluído versões específicas da plataforma para lidar com as dependências nativas necessárias para você.

Ao distribuir um aplicativo com dependências nativas, talvez você precise usar a opção `dotnet publish -r <RID>` para especificar a plataforma de destino na qual deseja publicar. Para obter uma lista de identificadores de runtime, confira o [Catálogo do RID (Identificador de Runtime)](../rid-catalog.md).

Mais informações sobre binários específicos da plataforma são abordadas nas seções [Executável dependente de estrutura](#framework-dependent-executable) e [Implantação autossuficiente](#self-contained-deployment).

## <a name="sample-app"></a>Aplicativo de exemplo

Você pode usar o seguinte aplicativo para explorar os comandos de publicação. O aplicativo é criado pela execução dos seguintes comandos no terminal:

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
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Quando você executa[`dotnet run`](../tools/dotnet-run.md)o aplicativo (), a seguinte saída é exibida:

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

O aplicativo está configurado para ser direcionado a uma versão específica do .NET Core. Esse tempo de execução do .NET Core direcionado é necessário para estar em qualquer máquina onde seu aplicativo é executado. Por exemplo, se o aplicativo for direcionado ao .NET Core 2.2, qualquer computador no qual o aplicativo é executado precisará ter o runtime do .NET Core 2.2 instalado. Conforme indicado na seção [Noções básicas de publicação](#publishing-basics), você pode editar o arquivo de projeto para alterar a estrutura de destino padrão ou para definir mais de uma estrutura como destino.

A publicação de uma FDD cria um aplicativo que efetua roll forward automaticamente para o último patch de segurança do .NET Core disponível no sistema que executa o aplicativo. Para obter mais informações sobre a associação de versão no tempo de compilação, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Executável dependente de estrutura

Para o .NET Core SDK 3.x CLI, o Executável dependente da `dotnet publish` estrutura (FDE) é o modo padrão para o comando básico. Você não precisa especificar outros parâmetros, desde que você queira direcionar o sistema operacional atual.

Nesse modo, um host do executável específico da plataforma é criado para hospedar o aplicativo multiplataforma. Este modo é semelhante ao FDD, pois o FDD requer um host na forma do `dotnet` comando. O nome de arquivo executável host varia por `<PROJECT-FILE>.exe`plataforma e é nomeado algo semelhante a . Você pode executar este executável `dotnet <PROJECT-FILE>.dll`diretamente em vez de ligar, o que ainda é uma maneira aceitável de executar o aplicativo.

O aplicativo está configurado para ser direcionado a uma versão específica do .NET Core. Esse tempo de execução do .NET Core direcionado é necessário para estar em qualquer máquina onde seu aplicativo é executado. Por exemplo, se o aplicativo for direcionado ao .NET Core 2.2, qualquer computador no qual o aplicativo é executado precisará ter o runtime do .NET Core 2.2 instalado. Conforme indicado na seção [Noções básicas de publicação](#publishing-basics), você pode editar o arquivo de projeto para alterar a estrutura de destino padrão ou para definir mais de uma estrutura como destino.

A publicação de um FDE cria um aplicativo que efetua roll forward automaticamente para o último patch de segurança do .NET Core disponível no sistema que executa o aplicativo. Para obter mais informações sobre a associação de versão no tempo de compilação, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md#framework-dependent-apps-roll-forward).

Para o .NET Core 2.2 e anterior, você `dotnet publish` deve usar os seguintes switches com o comando para publicar um FDE:

- `-r <RID>` Essa opção usa um RID (identificador) para especificar a plataforma de destino. Para obter uma lista de identificadores de runtime, confira o [Catálogo do RID (Identificador de Runtime)](../rid-catalog.md).

- `--self-contained false` Essa opção instrui o SDK do .NET Core a criar um executável como um FDE.

Sempre que você usa a opção `-r`, o caminho da pasta de saída é alterado para: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Se você usar o [aplicativo de exemplo](#sample-app), execute `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Esse comando cria o seguinte executável: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Reduza o tamanho total da implantação habilitando o **modo invariável de globalização**. Esse modo é útil para aplicativos que não têm reconhecimento global e que podem usar as convenções de formatação, as convenções de uso de maiúsculas, a comparação de cadeia de caracteres e a ordem de classificação da [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture). Para obter mais informações sobre **o modo invariante da globalização** e como habilitá-lo, consulte [o modo invariante da globalização do .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Implantação autocontida

Quando você publica uma SCD (implantação autossuficiente), o SDK do .NET Core cria um executável específico da plataforma. A publicação de um SCD inclui todos os arquivos .NET Core necessários para executar seu aplicativo, mas ele não inclui as [dependências nativas do .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Essas dependências precisam estar presentes no sistema antes da execução do aplicativo.

Publicar um SCD cria um aplicativo que não encaminha para o patch de segurança .NET Core mais recente disponível. Para obter mais informações sobre a associação de versão no tempo de compilação, confira [Selecionar a versão do .NET Core a ser usada](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

É necessário usar as seguintes opções com o comando `dotnet publish` para publicar uma SCD:

- `-r <RID>` Essa opção usa um RID (identificador) para especificar a plataforma de destino. Para obter uma lista de identificadores de runtime, confira o [Catálogo do RID (Identificador de Runtime)](../rid-catalog.md).

- `--self-contained true` Essa opção instrui o SDK do .NET Core a criar um executável como uma SCD.

> [!NOTE]
> Reduza o tamanho total da implantação habilitando o **modo invariável de globalização**. Esse modo é útil para aplicativos que não têm reconhecimento global e que podem usar as convenções de formatação, as convenções de uso de maiúsculas, a comparação de cadeia de caracteres e a ordem de classificação da [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture). Para obter mais informações sobre **o modo invariante da globalização** e como habilitá-lo, consulte [o modo invariante da globalização do .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="see-also"></a>Confira também

- [Visão geral da implantação de aplicativos .NET Core](index.md)
- [Catálogo do Identificador de Runtime do .NET Core](../rid-catalog.md)
