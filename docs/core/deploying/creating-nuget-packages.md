---
title: "Criando um pacote NuGet com várias Ferramentas de Plataforma Cruzada"
description: "Criando um pacote NuGet com várias Ferramentas de Plataforma Cruzada"
keywords: .NET, .NET Core, NuGet
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
translationtype: Human Translation
ms.sourcegitcommit: 300a0304e316cfa265634a3faf74c81c7a8a5e08
ms.openlocfilehash: d863587fbfee2bf713f8566a3e5b294d49ae50e9

---

# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Como criar um pacote NuGet com várias Ferramentas de Plataforma Cruzada

> [!NOTE]
> Veja a seguir exemplos de linha de comando usando o Unix.  O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.

Para .NET Core 1.0, espera-se que as bibliotecas sejam distribuídas como pacotes NuGet.  Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas.  Isso é realizado mais facilmente com o comando `dotnet pack`.

Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet.  Você pode criar um pacote NuGet com várias ferramentas de plataforma cruzada para fazer exatamente isso.  O exemplo a seguir pressupõe uma biblioteca chamada **SuperAwesomeLibrary** direcionada para `netstandard1.0`.

Se você tiver dependências transitivas, ou seja, um projeto que depende de outro projeto, precisará verificar se os pacotes foram restaurados para toda sua solução com o comando `dotnet restore` antes de criar um pacote NuGet.  Caso contrario, o comando `dotnet pack` não funcionará corretamente.

Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:

`$ cd src/SuperAwesomeLibrary`

Depois disso, basta apenas um único comando da linha de comando:
    
`$ dotnet pack`

Sua pasta `/bin/Debug` agora será assemelhará a esta:

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Observe que isso gerará um pacote que pode ser depurado.  Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `-c`/`--configuration` e usar `release` como argumento.

`$ dotnet pack --configuration release`

Sua pasta `/bin` agora terá uma pasta `release` que contém o pacote NuGet com binários de versão:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

E agora você tem os arquivos necessários para publicar um pacote NuGet.

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Não confunda `dotnet pack` com `dotnet publish`

É importante observar que em nenhum momento o comando `dotnet publish` está envolvido.  O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.



<!--HONumber=Nov16_HO3-->


