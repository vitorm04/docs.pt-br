---
title: Solução de problemas ' este aplicativo não pôde ser iniciado '
description: Saiba o que fazer se você vir uma caixa de diálogo ' este aplicativo não pôde ser iniciado '.
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 8fa8381f1b05445f259b4e4af5cc17fa487b2ce0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319175"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="24b6b-103">Solução de problemas de uma mensagem de erro "este aplicativo não pôde ser iniciado"</span><span class="sxs-lookup"><span data-stu-id="24b6b-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="24b6b-104">Os aplicativos desenvolvidos para o .NET Framework normalmente exigem que uma versão específica do .NET Framework seja instalada em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="24b6b-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="24b6b-105">Em alguns casos, você pode tentar executar um aplicativo sem uma versão instalada ou a versão esperada do .NET Framework presente.</span><span class="sxs-lookup"><span data-stu-id="24b6b-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="24b6b-106">Isso geralmente produz uma caixa de diálogo de erro semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="24b6b-106">This often produces an error dialog box like the following:</span></span>

![Não foi possível iniciar o aplicativo](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="24b6b-108">Isso normalmente indica uma das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="24b6b-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="24b6b-109">Uma instalação do .NET Framework no sistema foi corrompida.</span><span class="sxs-lookup"><span data-stu-id="24b6b-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="24b6b-110">A versão do .NET Framework necessário para seu aplicativo não pode ser detectada.</span><span class="sxs-lookup"><span data-stu-id="24b6b-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="24b6b-111">Para resolver esse problema para que você possa executar o aplicativo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="24b6b-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="24b6b-112">Baixe a [ferramenta de reparo de .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="24b6b-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="24b6b-113">A ferramenta é executada automaticamente quando o download é concluído.</span><span class="sxs-lookup"><span data-stu-id="24b6b-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="24b6b-114">Se a ferramenta de reparo de .NET Framework recomendar qualquer ação adicional, como as mostradas na figura a seguir, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="24b6b-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Alterações recomendadas](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="24b6b-116">O .NET Framework reparar ferramentas exibe uma caixa de diálogo mostrada na figura a seguir para indicar que as alterações foram concluídas.</span><span class="sxs-lookup"><span data-stu-id="24b6b-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="24b6b-117">Deixe a caixa de diálogo aberta enquanto você tenta executar novamente o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24b6b-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="24b6b-118">Isso deverá ter sucesso se a ferramenta de reparo de .NET Framework tiver identificado e corrigido uma instalação de .NET Framework corrompida.</span><span class="sxs-lookup"><span data-stu-id="24b6b-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Alterações recomendadas](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="24b6b-120">Se o aplicativo for executado com êxito, selecione o botão **concluir** .</span><span class="sxs-lookup"><span data-stu-id="24b6b-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="24b6b-121">Caso contrário, selecione o botão **Avançar** .</span><span class="sxs-lookup"><span data-stu-id="24b6b-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="24b6b-122">Se você selecionou o botão **Avançar** , a ferramenta de reparo de .NET Framework exibirá uma caixa de diálogo semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="24b6b-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="24b6b-123">Selecione o botão **concluir** para enviar informações de diagnóstico à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="24b6b-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Não é possível resolver o problema](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="24b6b-125">Se você ainda não puder executar o aplicativo, instale a versão mais recente do .NET Framework com suporte na sua versão do Windows, conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="24b6b-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="24b6b-126">Versão do Windows</span><span class="sxs-lookup"><span data-stu-id="24b6b-126">Windows version</span></span>|<span data-ttu-id="24b6b-127">Instalação do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="24b6b-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="24b6b-128">Atualização de aniversário do Windows 10 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="24b6b-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="24b6b-129">Tempo de execução do .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="24b6b-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="24b6b-130">Windows 10, atualização de novembro do Windows 10</span><span class="sxs-lookup"><span data-stu-id="24b6b-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="24b6b-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="24b6b-131">.NET Framework 4.6.2</span></span>](https://www.microsoft.com/download/details.aspx?id=53345)|
   |<span data-ttu-id="24b6b-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="24b6b-132">Windows 8.1</span></span>|[<span data-ttu-id="24b6b-133">Tempo de execução do .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="24b6b-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="24b6b-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="24b6b-134">Windows 8</span></span>|[<span data-ttu-id="24b6b-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="24b6b-135">.NET Framework 4.6.1</span></span>](https://www.microsoft.com/download/details.aspx?id=49981)|
   |<span data-ttu-id="24b6b-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="24b6b-136">Windows 7 SP1</span></span>|[<span data-ttu-id="24b6b-137">Tempo de execução do .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="24b6b-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="24b6b-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="24b6b-138">Windows Vista SP2</span></span>|[<span data-ttu-id="24b6b-139">.NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="24b6b-139">.NET Framework 4.6</span></span>](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   > <span data-ttu-id="24b6b-140">.NET Framework 4,8 é pré-instalado no Windows 10 pode ser 2019 atualização.</span><span class="sxs-lookup"><span data-stu-id="24b6b-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="24b6b-141">Tentativa de iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24b6b-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="24b6b-142">Em alguns casos, você pode ver uma caixa de diálogo semelhante à seguinte, que solicita que você instale o .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="24b6b-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="24b6b-143">Selecione **baixar e instalar este recurso** para instalar o .NET Framework 3,5 e, em seguida, inicie o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="24b6b-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Não é possível resolver o problema](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="24b6b-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24b6b-145">See also</span></span>

- [<span data-ttu-id="24b6b-146">Requisitos do sistema do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="24b6b-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="24b6b-147">Guia de instalação do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="24b6b-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="24b6b-148">Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="24b6b-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
