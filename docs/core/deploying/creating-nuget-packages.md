---
title: Crie um pacote NuGet com o .NET Core CLI
description: Saiba como criar um pacote do NuGet com o comando 'dotnet pack'.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920915"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>Como criar um pacote NuGet com o .NET Core CLI

> [!NOTE]
> Veja a seguir exemplos de linha de comando usando o Unix. O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.

Espera-se que as bibliotecas .NET Standard e .NET Core sejam distribuídas como pacotes NuGet. Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas. Isso é realizado mais facilmente com o comando `dotnet pack`.

Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet. Você pode criar um pacote NuGet com ferramentas multiplataforma para fazer exatamente isso! O exemplo a seguir assume uma biblioteca `netstandard1.0`chamada **SuperAwesomeLibrary** que tem como alvo .

Se você tem dependências transitivas, ou seja, um projeto que depende de outro pacote, certifique-se de restaurar pacotes para toda a solução com o `dotnet restore` comando antes de criar um pacote NuGet. Se não o fizer, `dotnet pack` o comando não funcionará corretamente.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:

```console
cd src/SuperAwesomeLibrary
```

Depois disso, basta apenas um único comando da linha de comando:

```dotnetcli
dotnet pack
```

Sua *pasta /bin/Debug* agora será assim:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Isso produz um pacote que é capaz de ser depurado. Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `--configuration` (ou `-c`) e usar `release` como argumento.

```dotnetcli
dotnet pack --configuration release
```

Sua *pasta /bin* agora terá uma pasta *de versão* contendo seu pacote NuGet com binários de liberação:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

E agora você tem os arquivos necessários para publicar um pacote NuGet.

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Não confunda `dotnet pack` com `dotnet publish`

É importante observar que em nenhum momento o comando `dotnet publish` está envolvido. O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.

## <a name="see-also"></a>Confira também

- [Início Rápido: Criar e publicar um pacote](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
