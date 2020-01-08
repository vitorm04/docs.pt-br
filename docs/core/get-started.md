---
title: Introdução ao .NET Core
description: Encontre recursos para aprender a criar aplicativos .NET Core no Windows, Linux e macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bcf9ea0bb9a8346284c49060786afefa0f77745e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341383"
---
# <a name="get-started-with-net-core"></a>Introdução ao .NET Core

Este artigo fornece informações de como começar a usar o .NET Core. O .NET Core pode ser instalado no Windows, no Linux e no macOS. Você pode codificar em seu editor de texto favorito e produzir aplicativos e bibliotecas multiplataforma.

Se você não souber exatamente o que é o .NET Core ou como ele se relaciona com outras tecnologias do .NET, comece com a visão geral [O que é o .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet). Resumindo, o .NET Core é uma implementação open-source e multiplataforma do .NET.

## <a name="create-an-application"></a>Criar um aplicativo

Primeiro, baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) em seu computador.

Em seguida, abra um terminal, como o **PowerShell**, um **prompt de comando** ou o **Bash**. Digite os seguintes comandos de `dotnet` para criar e executar um aplicativo C#:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Você deverá ver a seguinte saída:

```console
Hello World!
```

Parabéns! Você criou um aplicativo simples do .NET Core. Também é possível usar o [Visual Studio Code](./tutorials/with-visual-studio-code.md), o [Visual Studio](./tutorials/with-visual-studio.md) (somente Windows) ou o [Visual Studio para Mac](./tutorials/using-on-mac-vs.md) (somente macOS), para criar um aplicativo .NET Core.

## <a name="tutorials"></a>Tutoriais

Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

- [Criar seu primeiro aplicativo de console do .NET Core no Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Criar uma biblioteca de classes com .NET Standard no Visual Studio](./tutorials/library-with-visual-studio.md)
- [Introdução ao .NET Core usando o CLI do .NET Core](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](./media/video-icon.png "Assista a um vídeo") | Assista ao vídeo [como instalar e usar o Visual Studio Code e o .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) no Channel 9. |
| ![ícone de câmera para vídeo](./media/video-icon.png "Assista a um vídeo") | Assista aos vídeos do [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) no YouTube. |

Consulte o artigo [dependências e requisitos do .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) para obter uma lista das versões do Windows com suporte.

Consulte o artigo [dependências de SDK do .NET Core e tempo de execução](install/dependencies.md?pivots=os-windows) para obter uma lista das versões do Windows com suporte.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:

- [Introdução ao .NET Core usando a linha de comando](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](./media/video-icon.png "Assista a um vídeo") | Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Consulte o artigo [dependências de SDK do .NET Core e tempo de execução](install/dependencies.md?pivots=os-linux) para obter uma lista das versões e distribuições do Linux com suporte.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:

- [Introdução ao .NET Core no macOS usando o Visual Studio Code](./tutorials/using-on-macos.md)
- [Introdução ao .NET Core usando a linha de comando](./tutorials/cli-create-console-app.md)
- [Introdução ao .NET Core no macOS usando o Visual Studio para Mac](./tutorials/using-on-mac-vs.md)
- [Criar uma solução completa do .NET Core no macOS usando Visual Studio para Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](media/video-icon.png "Assista a um vídeo") | Assista a um vídeo sobre a [introdução ao Visual Studio Code C# usando o e o .NET Core no MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Consulte o artigo [dependências de SDK do .NET Core e tempo de execução](install/dependencies.md?pivots=os-macos) para obter uma lista das versões do os X/MacOS com suporte.

---
