---
title: Introdução ao .NET Core
description: Encontre recursos para aprender a criar aplicativos .NET Core no Windows, Linux e macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 78066f2904f6a874b71165e4fe1769b6b778ae41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428874"
---
# <a name="get-started-with-net-core"></a>Introdução ao .NET Core

Este artigo fornece informações de como começar a usar o .NET Core. O .NET Core pode ser instalado no Windows, no Linux e no macOS. Você pode codificar em seu editor de texto favorito e produzir aplicativos e bibliotecas multiplataforma. 

Se você não souber exatamente o que é o .NET Core ou como ele se relaciona com outras tecnologias do .NET, comece com a visão geral [O que é o .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet). Resumindo, o .NET Core é uma implementação open-source e multiplataforma do .NET.

## <a name="create-an-application"></a>Criar um aplicativo

Primeiro, baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) em seu computador.

Em seguida, abra um terminal, como o **PowerShell**, um **prompt de comando** ou o **Bash**. Digite os seguintes comandos de `dotnet` para criar e executar C# um aplicativo:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Você deverá ver a seguinte saída:

```console
Hello World!
```

Parabéns! Você criou um aplicativo simples do .NET Core. Também é possível usar o [Visual Studio Code](tutorials/with-visual-studio-code.md), o [Visual Studio](tutorials/with-visual-studio.md) (somente Windows) ou o [Visual Studio para Mac](tutorials/using-on-mac-vs.md) (somente macOS), para criar um aplicativo .NET Core.

## <a name="tutorials"></a>Tutoriais

Você pode começar a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo.

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

- [Compilar um aplicativo “Olá, Mundo” em C# com o .NET Core no Visual Studio 2017.](./tutorials/with-visual-studio.md)
- [Criar uma biblioteca de classes em C# e com o .NET Core no Visual Studio 2017.](./tutorials/library-with-visual-studio.md)
- [Criar um aplicativo “Olá, Mundo” em Visual Basic com o .NET Core no Visual Studio 2017.](./tutorials/vb-with-visual-studio.md)
- [Criar uma biblioteca de classes com Visual Basic e o .NET Core no Visual Studio 2017.](./tutorials/vb-library-with-visual-studio.md)  
- Assista a um vídeo sobre [como instalar e usar o Visual Studio Code e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).
- Assista a um vídeo sobre [como instalar e usar o Visual Studio 2017 e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).
- [Introdução ao .NET Core usando a linha de comando.](tutorials/using-with-xplat-cli.md)

Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) para obter uma lista das versões do Windows com suporte.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Você pode começar a desenvolver o aplicativo .NET Core seguindo estes tutoriais passo a passo:

- [Introdução ao .NET Core usando a linha de comando.](tutorials/using-with-xplat-cli.md)
- Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-linux) para obter uma lista das versões e distribuições do Linux com suporte.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Você pode começar a desenvolver o aplicativo .NET Core seguindo estes tutoriais passo a passo:

- Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).
- [Introdução ao .NET Core no macOS usando o Visual Studio Code.](tutorials/using-on-macos.md)
- [Introdução ao .NET Core usando a linha de comando.](tutorials/using-with-xplat-cli.md)
- [Introdução ao .NET Core no macOS usando o Visual Studio para Mac.](tutorials/using-on-mac-vs.md)
- [Compilar uma solução completa do .NET Core no macOS usando o Visual Studio para Mac.](tutorials/using-on-mac-vs-full-solution.md)

Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-macos) para obter uma lista das versões do os X/MacOS com suporte.

---
