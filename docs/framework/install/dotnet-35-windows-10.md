---
title: Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8
description: Saiba como instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8.
author: rlander
ms.author: mairaw
keywords: ".Net Framework, Instalação"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="9a3b3-104">Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8</span><span class="sxs-lookup"><span data-stu-id="9a3b3-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="9a3b3-105">Talvez você precise do .NET Framework 3.5 para executar um aplicativo no Windows 10, no Windows 8.1 e no Windows 8.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="9a3b3-106">Você também pode usar essas instruções para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="9a3b3-107">Instalação do .NET Framework 3.5 sob demanda</span><span class="sxs-lookup"><span data-stu-id="9a3b3-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="9a3b3-108">Se você tentar executar um aplicativo que exige o .NET Framework 3.5, você verá a seguinte caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="9a3b3-109">Escolha **Instalar este recurso** para habilitar o .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="9a3b3-110">Essa opção exige uma conexão com a Internet.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-110">This option requires an Internet connection.</span></span>

![Diálogo Instalação do .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="9a3b3-112">Habilitar o .NET Framework 3.5 no Painel de Controle</span><span class="sxs-lookup"><span data-stu-id="9a3b3-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="9a3b3-113">Você pode habilitar o .NET Framework 3.5 por meio do Painel de Controle do Windows.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="9a3b3-114">Essa opção exige uma conexão com a Internet.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="9a3b3-115">Pressione a tecla Windows ![logotipo do Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) no teclado, digite “Recursos do Windows” e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="9a3b3-116">A caixa de diálogo **Ativar ou desativar recursos do Windows** é exibida.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="9a3b3-117">Marque a caixa de seleção **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0)**, selecione **OK** e reinicialize o computador, se isso for solicitado.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Instalar o .NET com o painel de controle](./media/dotnet-control-panel.png)

   <span data-ttu-id="9a3b3-119">Não é necessário selecionar os itens filho para a **Ativação HTTP do WCF (Windows Communication Foundation)** e para a **Ativação Não HTTP do WCF (Windows Communication Foundation)**, a menos que você seja um desenvolvedor ou administrador de servidor que exija essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="9a3b3-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>
