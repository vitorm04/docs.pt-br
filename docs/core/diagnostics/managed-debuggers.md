---
title: Depuradores gerenciados-.NET Core
description: Uma visão geral do Visual Studio e Visual Studio Code depuradores gerenciados.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 3741011d22ab6c4240b7f88a9ab790ea61ecd0d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926435"
---
# <a name="net-core-managed-debuggers"></a><span data-ttu-id="d9d3d-103">Depurador gerenciados do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9d3d-103">.NET Core managed debuggers</span></span>

<span data-ttu-id="d9d3d-104">Os depuradores permitem que os programas sejam pausados ou executados passo a passo.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-104">Debuggers allow programs to be paused or executed step-by-step.</span></span> <span data-ttu-id="d9d3d-105">Quando em pausa, o estado atual do processo pode ser exibido.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-105">When paused, the current state of the process can be viewed.</span></span> <span data-ttu-id="d9d3d-106">Percorrendo as seções principais, você tem noções básicas sobre seu código e por que ele produz o resultado que ele faz.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-106">By stepping through key sections, you gain understanding of your code and why it produces the result that it does.</span></span>

<span data-ttu-id="d9d3d-107">A Microsoft fornece depuradores para código gerenciado no **Visual Studio** e **Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-107">Microsoft provides debuggers for managed code in **Visual Studio** and **Visual Studio Code**.</span></span>

## <a name="visual-studio-managed-debugger"></a><span data-ttu-id="d9d3d-108">Depurador gerenciado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9d3d-108">Visual Studio managed debugger</span></span>

<span data-ttu-id="d9d3d-109">O **Visual Studio** é um ambiente de desenvolvimento integrado com o depurador mais abrangente disponível.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-109">**Visual Studio** is an integrated development environment with the most comprehensive debugger available.</span></span> <span data-ttu-id="d9d3d-110">O Visual Studio é uma excelente opção para os desenvolvedores que trabalham no Windows.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-110">Visual Studio is an excellent choice for developers working on Windows.</span></span>

- [<span data-ttu-id="d9d3d-111">Tutorial-depuração de um aplicativo .NET Core no Windows com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9d3d-111">Tutorial - Debugging a .NET Core application on Windows with Visual Studio</span></span>](../tutorials/debugging-with-visual-studio.md)

<span data-ttu-id="d9d3d-112">Embora o Visual Studio seja um aplicativo do Windows, ele ainda pode ser usado para depurar aplicativos Linux e macOS remotamente.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-112">While Visual Studio is a Windows application, it can still be used to debug Linux and macOS apps remotely.</span></span>

- [<span data-ttu-id="d9d3d-113">Depurando um aplicativo .NET Core no Linux/OSX com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9d3d-113">Debugging a .NET Core application on Linux/OSX with Visual Studio</span></span>](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 <span data-ttu-id="d9d3d-114">A depuração ASP.NET Core aplicativos requer instruções um pouco diferentes.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-114">Debugging ASP.NET Core apps require slightly different instructions.</span></span>

- [<span data-ttu-id="d9d3d-115">Depurar ASP.NET Core aplicativos no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9d3d-115">Debug ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a><span data-ttu-id="d9d3d-116">Visual Studio Code depurador gerenciado</span><span class="sxs-lookup"><span data-stu-id="d9d3d-116">Visual Studio Code managed debugger</span></span>

<span data-ttu-id="d9d3d-117">**Visual Studio Code** é um editor de código de plataforma cruzada leve.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-117">**Visual Studio Code** is a lightweight cross-platform code editor.</span></span> <span data-ttu-id="d9d3d-118">Ele usa a mesma implementação do depurador do .NET Core que o Visual Studio, mas com uma interface do usuário simplificada.</span><span class="sxs-lookup"><span data-stu-id="d9d3d-118">It uses the same .NET Core debugger implementation as Visual Studio, but with a simplified user interface.</span></span>

- [<span data-ttu-id="d9d3d-119">Tutorial-depuração de um aplicativo .NET Core com Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d9d3d-119">Tutorial - Debugging a .NET Core application with Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md#debug)
- [<span data-ttu-id="d9d3d-120">Depurando no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d9d3d-120">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)
