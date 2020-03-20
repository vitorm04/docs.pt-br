---
title: Solução de problemas 'Este aplicativo não pôde ser iniciado'
description: Saiba o que fazer se você ver uma caixa de diálogo 'Este aplicativo não pode ser iniciado'.
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965900"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="77886-103">Solução de problemas uma mensagem de erro 'Este aplicativo não poderia ser iniciado'</span><span class="sxs-lookup"><span data-stu-id="77886-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="77886-104">Os aplicativos desenvolvidos para o .NET Framework normalmente exigem que uma versão específica do .NET Framework seja instalada no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="77886-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="77886-105">Em alguns casos, você pode tentar executar um aplicativo sem uma versão instalada ou a versão esperada do Quadro .NET presente.</span><span class="sxs-lookup"><span data-stu-id="77886-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="77886-106">Isso muitas vezes produz uma caixa de diálogo de erro como a seguinte:</span><span class="sxs-lookup"><span data-stu-id="77886-106">This often produces an error dialog box like the following:</span></span>

![Não foi possível iniciar o aplicativo](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="77886-108">Isso normalmente indica uma das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="77886-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="77886-109">Uma instalação do .NET Framework no seu sistema ficou corrompida.</span><span class="sxs-lookup"><span data-stu-id="77886-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="77886-110">A versão do .NET Framework necessário pelo seu aplicativo não pode ser detectada.</span><span class="sxs-lookup"><span data-stu-id="77886-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="77886-111">Para resolver esse problema para que você possa executar sua aplicação, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="77886-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="77886-112">Baixe a [ferramenta de reparo do framework .NET (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="77886-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="77886-113">A ferramenta é executada automaticamente quando o download é concluído.</span><span class="sxs-lookup"><span data-stu-id="77886-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="77886-114">Se a ferramenta de reparo do framework .NET recomendar qualquer ação adicional, como as mostradas na figura a seguir, selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="77886-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Alterações recomendadas](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="77886-116">As ferramentas de reparo do framework .NET exibem uma caixa de diálogo mostrada na figura a seguir para indicar que as alterações estão concluídas.</span><span class="sxs-lookup"><span data-stu-id="77886-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="77886-117">Deixe a caixa de diálogo aberta enquanto tenta executar novamente sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="77886-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="77886-118">Isso deve ser bem-sucedido se a ferramenta de reparo do framework .NET tiver identificado e corrigido uma instalação corrompida do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77886-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Alterações recomendadas](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="77886-120">Se o aplicativo for executado com sucesso, selecione o botão **Concluir.**</span><span class="sxs-lookup"><span data-stu-id="77886-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="77886-121">Caso contrário, selecione o botão **Seguinte.**</span><span class="sxs-lookup"><span data-stu-id="77886-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="77886-122">Se você selecionou o botão **Seguinte,** a Ferramenta de Reparo do Quadro .NET exibirá uma caixa de diálogo como a seguinte.</span><span class="sxs-lookup"><span data-stu-id="77886-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="77886-123">Selecione o botão **Concluir** para enviar informações de diagnóstico para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="77886-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Incapaz de resolver o problema](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="77886-125">Se você ainda não puder executar o aplicativo, instale a versão mais recente do .NET Framework suportado pela sua versão do Windows, como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="77886-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="77886-126">Versão do Windows</span><span class="sxs-lookup"><span data-stu-id="77886-126">Windows version</span></span>|<span data-ttu-id="77886-127">Instalação do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77886-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="77886-128">Atualização de aniversário do Windows 10 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="77886-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="77886-129">.NET Framework 4.8 Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="77886-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="77886-130">Windows 10, Windows 10 Atualização de Novembro</span><span class="sxs-lookup"><span data-stu-id="77886-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="77886-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="77886-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="77886-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="77886-132">Windows 8.1</span></span>|[<span data-ttu-id="77886-133">.NET Framework 4.8 Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="77886-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="77886-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="77886-134">Windows 8</span></span>|[<span data-ttu-id="77886-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="77886-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="77886-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="77886-136">Windows 7 SP1</span></span>|[<span data-ttu-id="77886-137">.NET Framework 4.8 Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="77886-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="77886-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="77886-138">Windows Vista SP2</span></span>|[<span data-ttu-id="77886-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="77886-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="77886-140">.NET Framework 4.8 está pré-instalado no Windows 10 May 2019 Update.</span><span class="sxs-lookup"><span data-stu-id="77886-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="77886-141">Tente iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="77886-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="77886-142">Em alguns casos, você pode ver uma caixa de diálogo como a seguinte, que pede que você instale o .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="77886-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="77886-143">Selecione **Baixar e instalar esse recurso** para instalar o .NET Framework 3.5 e, em seguida, inicie o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="77886-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Incapaz de resolver o problema](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="77886-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="77886-145">See also</span></span>

- [<span data-ttu-id="77886-146">Requisitos do sistema do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77886-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="77886-147">Guia de instalação do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77886-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="77886-148">Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77886-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
