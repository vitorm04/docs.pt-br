---
title: Depuradores gerenciados - .NET Core
description: Uma visão geral dos depuradores gerenciados do Visual Studio e do Visual Studio Code.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715562"
---
# <a name="net-core-managed-debuggers"></a>Depuradores gerenciados pelo .NET Core

Os depuradores permitem que os programas sejam pausados ou executados passo a passo. Quando pausado, o estado atual do processo pode ser visualizado. Ao passar por seções-chave, você ganha a compreensão do seu código e por que ele produz o resultado que ele faz.

A Microsoft fornece depuradores para código gerenciado no **Visual Studio** e Visual **Studio Code**.

## <a name="visual-studio-managed-debugger"></a>Depurador gerenciado pelo Visual Studio

**Visual Studio** é um ambiente de desenvolvimento integrado com o depurador mais abrangente disponível. Visual Studio é uma excelente escolha para desenvolvedores que trabalham no Windows.

- [Tutorial - Depurando um aplicativo .NET Core no Windows com o Visual Studio](../tutorials/debugging-with-visual-studio.md)

Embora o Visual Studio seja um aplicativo do Windows, ele ainda pode ser usado para depurar aplicativos Linux e macOS remotamente.

- [Depuração de um aplicativo .NET Core no Linux/OSX com o Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 A depuração ASP.NET aplicativos Core requerem instruções ligeiramente diferentes.

- [Debug ASP.NET aplicativos Core no Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Depurador gerenciado pelo Visual Studio Code

**Visual Studio Code** é um editor de código multiplataforma leve. Ele usa a mesma implementação de depurador .NET Core como Visual Studio, mas com uma interface de usuário simplificada.

- [Tutorial - Depuração de um aplicativo .NET Core com visual studio code](../tutorials/with-visual-studio-code.md#debug)
- [Depurar no Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)
