---
title: Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8
description: Saiba como instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8.
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: e81008eca3019860789db548d40998a7a7565d31
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="1e8a8-103">Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8</span><span class="sxs-lookup"><span data-stu-id="1e8a8-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="1e8a8-104">Talvez você precise do .NET Framework 3.5 para executar um aplicativo no Windows 10, no Windows 8.1 e no Windows 8.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="1e8a8-105">Você também pode usar essas instruções para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="1e8a8-106">Instalação do .NET Framework 3.5 sob demanda</span><span class="sxs-lookup"><span data-stu-id="1e8a8-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="1e8a8-107">Se você tentar executar um aplicativo que exige o .NET Framework 3.5, você verá a seguinte caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="1e8a8-108">Escolha **Instalar este recurso** para habilitar o .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="1e8a8-109">Essa opção exige uma conexão com a Internet.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-109">This option requires an Internet connection.</span></span>

![Diálogo Instalação do .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="1e8a8-111">Habilitar o .NET Framework 3.5 no Painel de Controle</span><span class="sxs-lookup"><span data-stu-id="1e8a8-111">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="1e8a8-112">Você pode habilitar o .NET Framework 3.5 por meio do Painel de Controle do Windows.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-112">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="1e8a8-113">Essa opção exige uma conexão com a Internet.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-113">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="1e8a8-114">Pressione a tecla Windows ![logotipo do Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) no teclado, digite “Recursos do Windows” e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-114">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="1e8a8-115">A caixa de diálogo **Ativar ou desativar recursos do Windows** é exibida.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-115">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="1e8a8-116">Marque a caixa de seleção **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0)**, selecione **OK** e reinicialize o computador, se isso for solicitado.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-116">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Instalar o .NET com o painel de controle](./media/dotnet-control-panel.png)

   <span data-ttu-id="1e8a8-118">Não é necessário selecionar os itens filho para a **Ativação HTTP do WCF (Windows Communication Foundation)** e para a **Ativação Não HTTP do WCF (Windows Communication Foundation)**, a menos que você seja um desenvolvedor ou administrador de servidor que exija essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-118">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="1e8a8-119">Solucionar problemas de instalação do .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="1e8a8-119">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="1e8a8-120">Durante a instalação, você poderá se deparar com o erro 0x800f0906, 0x800f0907, 0x800f081f ou 0x800F0922. Nesse caso, consulte [Erro de instalação do .NET Framework 3.5: 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) para descobrir como resolver esses problemas.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-120">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="1e8a8-121">Se algum dos métodos discutidos no artigo anterior falhar ou se você não tiver uma conexão com a Internet, use a mídia de instalação do Windows.</span><span class="sxs-lookup"><span data-stu-id="1e8a8-121">If any of the methods discussed in the previous article fail or if you don't have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="1e8a8-122">Para obter mais informações, consulte [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism) (Implantar o .NET Framework 3.5 usando o DISM (Gerenciamento e Manutenção de Imagens de Implantação)).</span><span class="sxs-lookup"><span data-stu-id="1e8a8-122">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="1e8a8-123">Se você não tiver a mídia de instalação, confira [Criar mídia de instalação para Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span><span class="sxs-lookup"><span data-stu-id="1e8a8-123">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
