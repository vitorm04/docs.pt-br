---
title: Introdução ao .NET Core
description: Encontre recursos para aprender a criar aplicativos .NET Core no Windows, Linux e macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714388"
---
# <a name="get-started-with-net-core"></a>Introdução ao .NET Core

Este artigo fornece informações de como começar a usar o .NET Core. O .NET Core pode ser instalado no Windows, no Linux e no macOS. Você pode codificar em seu editor de texto favorito e produzir aplicativos e bibliotecas multiplataforma.

Se você não souber exatamente o que é o .NET Core ou como ele se relaciona com outras tecnologias do .NET, comece com a visão geral [O que é o .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet). Resumindo, o .NET Core é uma implementação open-source e multiplataforma do .NET.

## <a name="create-an-application"></a>Criar um aplicativo

Primeiro, baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) em seu computador.

Em seguida, abra um terminal, como o **PowerShell**, um **prompt de comando** ou o **Bash**. Digite `dotnet` os seguintes comandos para criar e executar um aplicativo C#:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Você deve ver o seguinte resultado:

```console
Hello World!
```

Parabéns! Você criou um aplicativo simples do .NET Core. Também é possível usar o [Visual Studio Code](./tutorials/with-visual-studio-code.md), o [Visual Studio](./tutorials/with-visual-studio.md) (somente Windows) ou o [Visual Studio para Mac](./tutorials/using-on-mac-vs.md) (somente macOS), para criar um aplicativo .NET Core.

## <a name="tutorials"></a>Tutoriais

Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Crie seu primeiro aplicativo de console .NET Core no Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Construa uma biblioteca de classes com .NET Standard no Visual Studio](./tutorials/library-with-visual-studio.md)
- [Comece com o .NET Core usando o .NET Core CLI](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](./media/video-icon.png "Assistir a um vídeo") | Assista [ao vídeo como instalar e usar o Visual Studio Code e o vídeo .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) no Canal 9. |
| ![ícone de câmera para vídeo](./media/video-icon.png "Assistir a um vídeo") | Assista aos vídeos [do .NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) no YouTube. |

Consulte o artigo [de dependências e requisitos](install/dependencies.md?pivots=os-windows) do .NET Core para obter uma lista das versões suportadas do Windows.

# <a name="linux"></a>[Linux](#tab/linux)

Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:

- [Comece com o .NET Core usando a linha de comando](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](./media/video-icon.png "Assistir a um vídeo") | Assista a um vídeo sobre uma [introdução ao Visual Studio Code usando C# e o .NET Core no Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Consulte o artigo [de dependências e requisitos](install/dependencies.md?pivots=os-linux) do .NET Core para obter uma lista das distros e versões do Linux suportadas.

# <a name="macos"></a>[macOS](#tab/macos)

Comece a desenvolver aplicativos .NET Core seguindo estes tutoriais passo a passo:

- [Introdução ao .NET Core no macOS usando o Visual Studio Code](./tutorials/using-on-macos.md)
- [Comece com o .NET Core usando a linha de comando](./tutorials/cli-create-console-app.md)
- [Introdução ao .NET Core no macOS, usando o Visual Studio para Mac](./tutorials/using-on-mac-vs.md)
- [Construa uma solução .NET Core completa no macOS usando o Visual Studio para Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](media/video-icon.png "Assistir a um vídeo") | Assista a um vídeo sobre [como começar com o Visual Studio Code usando C# e .NET Core no macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Consulte o artigo [de dependências e requisitos](install/dependencies.md?pivots=os-macos) do .NET Core para obter uma lista das versões suportadas do OS X /macOS.

---
