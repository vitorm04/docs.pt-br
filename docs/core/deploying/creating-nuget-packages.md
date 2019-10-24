---
title: Criar um pacote NuGet com ferramentas da interface de linha de comando (CLI) do .NET Core
description: Saiba como criar um pacote do NuGet com o comando 'dotnet pack'.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 2d876f921d079972e2a638788195aa69a2423c49
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771940"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Como criar um pacote NuGet com ferramentas da interface de linha de comando (CLI) do .NET Core

> [!NOTE]
> Veja a seguir exemplos de linha de comando usando o Unix. O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.

Espera-se que as bibliotecas .NET Standard e .NET Core sejam distribuídas como pacotes NuGet. Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas. Isso é realizado mais facilmente com o comando `dotnet pack`.

Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet. Você pode criar um pacote NuGet com várias ferramentas de plataforma cruzada para fazer exatamente isso. O exemplo a seguir pressupõe uma biblioteca chamada **SuperAwesomeLibrary** direcionada para `netstandard1.0`.

Se você tiver dependências transitivas, ou seja, um projeto que depende de outro pacote, será preciso garantir a restauração dos pacotes para toda a sua solução com o comando `dotnet restore` antes de criar um pacote NuGet. Caso contrario, o comando `dotnet pack` não funcionará corretamente.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:

```console
cd src/SuperAwesomeLibrary
```

Depois disso, basta apenas um único comando da linha de comando:

```dotnetcli
dotnet pack
```

Sua pasta */bin/Debug* agora terá esta aparência:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Observe que isso gerará um pacote que pode ser depurado. Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `--configuration` (ou `-c`) e usar `release` como argumento.

```dotnetcli
dotnet pack --configuration release
```

Sua pasta */bin* agora terá uma pasta *Release* que contém o pacote NuGet com binários de versão:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

E agora você tem os arquivos necessários para publicar um pacote NuGet.

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Não confunda `dotnet pack` com `dotnet publish`

É importante observar que em nenhum momento o comando `dotnet publish` está envolvido. O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.

## <a name="see-also"></a>Consulte também

- [Início Rápido: Criar e publicar um pacote](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
