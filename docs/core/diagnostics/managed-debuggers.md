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
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="86112-103">Depuradores gerenciados pelo .NET Core</span><span class="sxs-lookup"><span data-stu-id="86112-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="86112-104">Os depuradores permitem que os programas sejam pausados ou executados passo a passo.</span><span class="sxs-lookup"><span data-stu-id="86112-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="86112-105">Quando pausado, o estado atual do processo pode ser visualizado.</span><span class="sxs-lookup"><span data-stu-id="86112-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="86112-106">Ao passar por seções-chave, você ganha a compreensão do seu código e por que ele produz o resultado que ele faz.</span><span class="sxs-lookup"><span data-stu-id="86112-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="86112-107">A Microsoft fornece depuradores para código gerenciado no **Visual Studio** e Visual **Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="86112-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="86112-108">Depurador gerenciado pelo Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86112-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="86112-109">**Visual Studio** é um ambiente de desenvolvimento integrado com o depurador mais abrangente disponível.</span><span class="sxs-lookup"><span data-stu-id="86112-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="86112-110">Visual Studio é uma excelente escolha para desenvolvedores que trabalham no Windows.</span><span class="sxs-lookup"><span data-stu-id="86112-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="86112-111">Tutorial - Depurando um aplicativo .NET Core no Windows com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86112-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="86112-112">Embora o Visual Studio seja um aplicativo do Windows, ele ainda pode ser usado para depurar aplicativos Linux e macOS remotamente.</span><span class="sxs-lookup"><span data-stu-id="86112-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="86112-113">Depuração de um aplicativo .NET Core no Linux/OSX com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86112-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="86112-114">A depuração ASP.NET aplicativos Core requerem instruções ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="86112-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="86112-115">Debug ASP.NET aplicativos Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86112-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="86112-116">Depurador gerenciado pelo Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86112-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="86112-117">**Visual Studio Code** é um editor de código multiplataforma leve.</span><span class="sxs-lookup"><span data-stu-id="86112-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="86112-118">Ele usa a mesma implementação de depurador .NET Core como Visual Studio, mas com uma interface de usuário simplificada.</span><span class="sxs-lookup"><span data-stu-id="86112-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="86112-119">Tutorial - Depuração de um aplicativo .NET Core com visual studio code</span><span class="sxs-lookup"><span data-stu-id="86112-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="86112-120">Depurar no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="86112-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
