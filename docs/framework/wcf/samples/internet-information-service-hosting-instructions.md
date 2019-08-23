---
title: Instruções de hospedagem de serviço de informação de internet
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929105"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="92bc7-102">Instruções de hospedagem de serviço de informação de internet</span><span class="sxs-lookup"><span data-stu-id="92bc7-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="92bc7-103">Para executar os exemplos hospedados pelo Serviços de Informações da Internet (IIS), você deve verificar se o IIS está instalado corretamente e está em execução.</span><span class="sxs-lookup"><span data-stu-id="92bc7-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="92bc7-104">Para instalar o IIS versão 7,5 no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="92bc7-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="92bc7-105">Em **Gerenciador do servidor**, selecione **funções.**</span><span class="sxs-lookup"><span data-stu-id="92bc7-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="92bc7-106">Em **Resumo de funções**, clique em **adicionar funções**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="92bc7-107">Clique em **Avançar** para exibir a caixa de diálogo **selecionar funções de servidor** .</span><span class="sxs-lookup"><span data-stu-id="92bc7-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="92bc7-108">Selecione **servidor de aplicativos** na lista **funções** e clique em **Avançar** duas vezes para exibir a caixa de diálogo **selecionar serviços de função** para a função servidor de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="92bc7-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="92bc7-109">Marque a caixa de seleção **servidor Web (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="92bc7-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="92bc7-110">Se for solicitado que você instale recursos e serviços de função adicionais, clique em **Adicionar recursos necessários**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="92bc7-111">Clique em **Avançar** duas vezes para exibir a caixa de diálogo **selecionar serviços de função** para a função do servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="92bc7-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="92bc7-112">Expanda **ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade de gerenciamento do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="92bc7-113">Selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="92bc7-114">Se for solicitado que você instale recursos e serviços de função adicionais, clique em **Adicionar serviços de função necessários**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="92bc7-115">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="92bc7-116">Se o resumo das seleções estiver correto, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="92bc7-117">Quando a instalação for concluída, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="92bc7-118">Para instalar o IIS versão 7,5 no Windows 7</span><span class="sxs-lookup"><span data-stu-id="92bc7-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="92bc7-119">Clique em **Iniciar**e em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="92bc7-120">Abra o grupo **programas** .</span><span class="sxs-lookup"><span data-stu-id="92bc7-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="92bc7-121">Em **programas e recursos**, clique em **Ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="92bc7-122">A caixa de diálogo **controle de conta de usuário** é exibida.</span><span class="sxs-lookup"><span data-stu-id="92bc7-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="92bc7-123">Clique em **Continue**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="92bc7-124">A caixa de diálogo **recursos do Windows** é exibida.</span><span class="sxs-lookup"><span data-stu-id="92bc7-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="92bc7-125">Expanda o item rotulado **serviços de informações da Internet**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="92bc7-126">Expanda o item rotulado **World Wide Web serviços**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="92bc7-127">Expanda o item rotulado **recursos de desenvolvimento de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="92bc7-128">Verifique se os seguintes itens estão selecionados:</span><span class="sxs-lookup"><span data-stu-id="92bc7-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="92bc7-129">**Extensibilidade do .NET**</span><span class="sxs-lookup"><span data-stu-id="92bc7-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="92bc7-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="92bc7-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="92bc7-131">**Extensões ISAPI**</span><span class="sxs-lookup"><span data-stu-id="92bc7-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="92bc7-132">**Filtros ISAPI**</span><span class="sxs-lookup"><span data-stu-id="92bc7-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="92bc7-133">Sob o item rotulado **World Wide Web serviços**, expanda **recursos http comuns**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="92bc7-134">Certifique-se de que **conteúdo estático** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="92bc7-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="92bc7-135">Sob o item rotulado **World Wide Web serviços**, expanda **segurança**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="92bc7-136">Verifique se a **autenticação do Windows** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="92bc7-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="92bc7-137">No diretório **serviços de informações da Internet** , expanda o item rotulado **ferramentas de gerenciamento da Web**e selecione **console de gerenciamento do IIS**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="92bc7-138">Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="92bc7-139">No diretório **serviços de informações da Internet** , expanda o item rotulado **Microsoft .NET Framework 3.5.1**e, em seguida, selecione **Windows Communication Foundation ativação http**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="92bc7-140">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="92bc7-141">Para instalar o IIS versão 7,0 no Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="92bc7-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="92bc7-142">Em **Gerenciador do servidor**, selecione **funções**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="92bc7-143">Em **Resumo de funções**, clique em **adicionar funções**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="92bc7-144">Clique em **Avançar** para exibir a caixa de diálogo **selecionar funções de servidor** .</span><span class="sxs-lookup"><span data-stu-id="92bc7-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="92bc7-145">Selecione **servidor de aplicativos** na lista **funções** e clique em **Avançar** duas vezes para exibir a caixa de diálogo **selecionar serviços de função** para a função servidor de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="92bc7-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="92bc7-146">Selecione a caixa **de seleção servidor Web (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="92bc7-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="92bc7-147">Se for solicitado que você instale recursos e serviços de função adicionais, clique em **Adicionar recursos necessários**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="92bc7-148">Clique em **Avançar** duas vezes para exibir a caixa de diálogo **selecionar serviços de função** para a função do servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="92bc7-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="92bc7-149">Expanda **ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade de gerenciamento do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="92bc7-150">Selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="92bc7-151">Se for solicitado que você instale recursos e serviços de função adicionais, clique em **Adicionar serviços de função necessários**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="92bc7-152">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="92bc7-153">Se o resumo das seleções estiver correto, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="92bc7-154">Quando a instalação for concluída, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="92bc7-155">Para instalar o IIS versão 7,0 no Windows Vista</span><span class="sxs-lookup"><span data-stu-id="92bc7-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="92bc7-156">Clique em Iniciar e em painel de controle.</span><span class="sxs-lookup"><span data-stu-id="92bc7-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="92bc7-157">Selecione o grupo **programas** .</span><span class="sxs-lookup"><span data-stu-id="92bc7-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="92bc7-158">Em **programas e recursos**, clique em **Ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="92bc7-159">A caixa de diálogo **controle de conta de usuário** é exibida.</span><span class="sxs-lookup"><span data-stu-id="92bc7-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="92bc7-160">Clique em **Continue**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="92bc7-161">A caixa de diálogo **recursos do Windows** é exibida.</span><span class="sxs-lookup"><span data-stu-id="92bc7-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="92bc7-162">Expanda o item rotulado **serviços de informações da Internet**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="92bc7-163">Expanda o item rotulado **World Wide Web serviços**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="92bc7-164">Expanda o item rotulado **recursos de desenvolvimento de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="92bc7-165">Verifique se os seguintes itens estão selecionados:</span><span class="sxs-lookup"><span data-stu-id="92bc7-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="92bc7-166">**Extensibilidade do .NET**</span><span class="sxs-lookup"><span data-stu-id="92bc7-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="92bc7-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="92bc7-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="92bc7-168">**Extensões ISAPI**</span><span class="sxs-lookup"><span data-stu-id="92bc7-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="92bc7-169">**Filtros ISAPI**</span><span class="sxs-lookup"><span data-stu-id="92bc7-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="92bc7-170">Expanda o item rotulado **ferramentas de gerenciamento da Web**e selecione **console de gerenciamento do IIS**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="92bc7-171">Sob o item rotulado **World Wide Web serviços**, expanda **recursos http comuns**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="92bc7-172">Certifique-se de que **conteúdo estático** esteja selecionado.</span><span class="sxs-lookup"><span data-stu-id="92bc7-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="92bc7-173">Sob o item rotulado **World Wide Web serviços**, expanda **segurança**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="92bc7-174">Verifique se a **autenticação do Windows** está selecionada.</span><span class="sxs-lookup"><span data-stu-id="92bc7-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="92bc7-175">Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="92bc7-176">Expanda o item rotulado **Microsoft .NET Framework 3,0**e, em seguida, selecione **Windows Communication Foundation ativação http**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="92bc7-177">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="92bc7-178">Para instalar o IIS versão 6,0 no Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="92bc7-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="92bc7-179">Em **gerenciar seu servidor**, clique em **Adicionar ou remover uma função**e, em seguida, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="92bc7-180">Selecione **servidor de aplicativos (IIS, ASP.net)** na lista **função de servidor** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="92bc7-181">Marque a caixa de seleção **habilitar ASP.net** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="92bc7-182">Se o resumo das seleções estiver correto, clique em Avançar.</span><span class="sxs-lookup"><span data-stu-id="92bc7-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="92bc7-183">Para instalar o IIS versão 5,1 no Windows XP com Service Pack 2 e Service Pack 3 instalados</span><span class="sxs-lookup"><span data-stu-id="92bc7-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="92bc7-184">No painel de controle, clique em **Adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="92bc7-185">Na caixa de diálogo **Adicionar ou remover programas** , clique em **Adicionar/remover componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="92bc7-186">No **Assistente de componentes do Windows**, marque a caixa de seleção **serviços de informações da Internet (IIS)** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="92bc7-187">Se a caixa de diálogo **arquivos necessários** for exibida, insira o disco de instalação do sistema operacional, navegue até a pasta i386 e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="92bc7-188">Quando a instalação for concluída, clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="92bc7-189">Feche a caixa de diálogo **Adicionar ou remover programas** e, em seguida, feche o **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="92bc7-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="92bc7-190">Para verificar a instalação do IIS e do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92bc7-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="92bc7-191">Salve o arquivo HTML encontrado no final deste tópico no diretório root \InetPub\wwwroot e nomeie-o como default. aspx.</span><span class="sxs-lookup"><span data-stu-id="92bc7-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="92bc7-192">Abra uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="92bc7-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="92bc7-193">Digite `http://localhost/Default.aspx` na caixa endereço e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="92bc7-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="92bc7-194">Uma página da Web com o texto "Olá, Mundo" deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="92bc7-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92bc7-195">Sempre que você instalar uma nova versão do .NET Framework, deverá registrar novamente o aspnet_isapi como uma extensão de serviço da Web para o IIS.</span><span class="sxs-lookup"><span data-stu-id="92bc7-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="92bc7-196">Para fazer isso, emita o `aspnet_regiis –I –enable` comando.</span><span class="sxs-lookup"><span data-stu-id="92bc7-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="92bc7-197">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="92bc7-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
