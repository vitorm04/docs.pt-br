---
title: Instruções de hospedagem de serviço de informação de internet
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 303fe47df987901b09cee8cc4292f12bcda2b74d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071131"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="83432-102">Instruções de hospedagem de serviço de informação de internet</span><span class="sxs-lookup"><span data-stu-id="83432-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="83432-103">Para executar os exemplos que são hospedados por serviços de informações da Internet (IIS), certifique-se de que o IIS está instalado corretamente e está em execução.</span><span class="sxs-lookup"><span data-stu-id="83432-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="83432-104">Para instalar o IIS versão 7.5 no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="83432-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="83432-105">Partir **Gerenciador de servidores**, selecione **funções.**</span><span class="sxs-lookup"><span data-stu-id="83432-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="83432-106">Sob **resumo de funções**, clique em **adicionar funções**.</span><span class="sxs-lookup"><span data-stu-id="83432-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="83432-107">Clique em **próxima** para exibir o **selecionar funções de servidor** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="83432-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="83432-108">Selecione **servidor de aplicativos** da **funções** e, em seguida, clique **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="83432-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="83432-109">Selecione o **servidor Web (IIS)** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="83432-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="83432-110">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**.</span><span class="sxs-lookup"><span data-stu-id="83432-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="83432-111">Clique em **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="83432-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="83432-112">Expandir **as ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade com gerenciamento do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="83432-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="83432-113">Selecione **IIS ferramentas de script 6**.</span><span class="sxs-lookup"><span data-stu-id="83432-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="83432-114">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**.</span><span class="sxs-lookup"><span data-stu-id="83432-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="83432-115">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="83432-115">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="83432-116">Se o resumo das seleções estiver correto, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="83432-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="83432-117">Quando a instalação for concluída, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="83432-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="83432-118">Para instalar o IIS versão 7.5 no Windows 7</span><span class="sxs-lookup"><span data-stu-id="83432-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1.  <span data-ttu-id="83432-119">Clique em **inicie**e, em seguida, clique em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="83432-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="83432-120">Abra o **programas** grupo.</span><span class="sxs-lookup"><span data-stu-id="83432-120">Open the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="83432-121">Sob **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="83432-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="83432-122">O **User Account Control** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="83432-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="83432-123">Clique em **Continue**.</span><span class="sxs-lookup"><span data-stu-id="83432-123">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="83432-124">O **recursos do Windows** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="83432-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="83432-125">Expanda o item rotulado **serviços de informações da Internet**.</span><span class="sxs-lookup"><span data-stu-id="83432-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="83432-126">Expanda o item rotulado **serviços da World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="83432-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="83432-127">Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="83432-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="83432-128">Verifique se que os seguintes itens estão selecionados:</span><span class="sxs-lookup"><span data-stu-id="83432-128">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="83432-129">**Extensibilidade .NET**</span><span class="sxs-lookup"><span data-stu-id="83432-129">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="83432-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="83432-130">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="83432-131">**Extensões ISAPI**</span><span class="sxs-lookup"><span data-stu-id="83432-131">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="83432-132">**Filtros ISAPI**</span><span class="sxs-lookup"><span data-stu-id="83432-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="83432-133">Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.</span><span class="sxs-lookup"><span data-stu-id="83432-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="83432-134">Certifique-se **conteúdo estático** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="83432-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="83432-135">Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.</span><span class="sxs-lookup"><span data-stu-id="83432-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="83432-136">Certifique-se de que **autenticação do Windows** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="83432-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="83432-137">Sob o **serviços de informações da Internet** diretório, expanda o item rotulado **ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento do IIS**.</span><span class="sxs-lookup"><span data-stu-id="83432-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="83432-138">Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="83432-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="83432-139">Sob o **serviços de informações da Internet** diretório, expanda o item rotulado **Microsoft .NET Framework 3.5.1**e, em seguida, selecione **Windows Communication Foundation Http Activation**.</span><span class="sxs-lookup"><span data-stu-id="83432-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="83432-140">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="83432-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="83432-141">Para instalar o IIS versão 7.0 no Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="83432-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="83432-142">Partir **Gerenciador de servidores**, selecione **funções**.</span><span class="sxs-lookup"><span data-stu-id="83432-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="83432-143">Sob **resumo de funções**, clique em **adicionar funções**.</span><span class="sxs-lookup"><span data-stu-id="83432-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="83432-144">Clique em **próxima** para exibir o **selecionar funções de servidor** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="83432-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="83432-145">Selecione **servidor de aplicativos** da **funções** e, em seguida, clique **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="83432-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="83432-146">Selecione **servidor Web (IIS)** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="83432-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="83432-147">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**.</span><span class="sxs-lookup"><span data-stu-id="83432-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="83432-148">Clique em **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="83432-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="83432-149">Expandir **as ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade com gerenciamento do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="83432-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="83432-150">Selecione **IIS ferramentas de script 6**.</span><span class="sxs-lookup"><span data-stu-id="83432-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="83432-151">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**.</span><span class="sxs-lookup"><span data-stu-id="83432-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="83432-152">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="83432-152">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="83432-153">Se o resumo das seleções estiver correto, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="83432-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="83432-154">Quando a instalação for concluída, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="83432-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="83432-155">Para instalar o IIS versão 7.0 no Windows Vista</span><span class="sxs-lookup"><span data-stu-id="83432-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1.  <span data-ttu-id="83432-156">Clique em Iniciar e, em seguida, clique em Painel de controle.</span><span class="sxs-lookup"><span data-stu-id="83432-156">Click Start, and then click Control Panel.</span></span>  
  
2.  <span data-ttu-id="83432-157">Selecione o **programas** grupo.</span><span class="sxs-lookup"><span data-stu-id="83432-157">Select the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="83432-158">Sob **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="83432-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="83432-159">O **User Account Control** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="83432-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="83432-160">Clique em **Continue**.</span><span class="sxs-lookup"><span data-stu-id="83432-160">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="83432-161">O **recursos do Windows** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="83432-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="83432-162">Expanda o item rotulado **serviços de informações da Internet**.</span><span class="sxs-lookup"><span data-stu-id="83432-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="83432-163">Expanda o item rotulado **serviços da World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="83432-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="83432-164">Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="83432-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="83432-165">Verifique se que os seguintes itens estão selecionados:</span><span class="sxs-lookup"><span data-stu-id="83432-165">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="83432-166">**Extensibilidade .NET**</span><span class="sxs-lookup"><span data-stu-id="83432-166">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="83432-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="83432-167">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="83432-168">**Extensões ISAPI**</span><span class="sxs-lookup"><span data-stu-id="83432-168">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="83432-169">**Filtros ISAPI**</span><span class="sxs-lookup"><span data-stu-id="83432-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="83432-170">Expanda o item rotulado **as ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento IIS**.</span><span class="sxs-lookup"><span data-stu-id="83432-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="83432-171">Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.</span><span class="sxs-lookup"><span data-stu-id="83432-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="83432-172">Certifique-se **conteúdo estático** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="83432-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="83432-173">Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.</span><span class="sxs-lookup"><span data-stu-id="83432-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="83432-174">Certifique-se **autenticação do Windows** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="83432-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="83432-175">Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="83432-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="83432-176">Expanda o item rotulado **Microsoft .NET Framework 3.0**e, em seguida, selecione **Windows Communication Foundation Http Activation**.</span><span class="sxs-lookup"><span data-stu-id="83432-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="83432-177">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="83432-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="83432-178">Para instalar o IIS versão 6.0 no Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="83432-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="83432-179">Partir **gerenciar o servidor**, clique em **adicionar ou remover uma função**e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="83432-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="83432-180">Selecione **servidor de aplicativos (IIS, ASP.NET)** da **função de servidor** e, em seguida, clique **próxima**.</span><span class="sxs-lookup"><span data-stu-id="83432-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="83432-181">Selecione **ativar ASP.NET** caixa de seleção e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="83432-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="83432-182">Se o resumo das seleções estiver correto, clique em Avançar.</span><span class="sxs-lookup"><span data-stu-id="83432-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="83432-183">Para instalar o IIS versão 5.1 no Windows XP com Service Pack 2 e Service Pack 3 instalado</span><span class="sxs-lookup"><span data-stu-id="83432-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1.  <span data-ttu-id="83432-184">No painel de controle, clique em **adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="83432-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="83432-185">No **adicionar ou remover programas** caixa de diálogo, clique em **Adicionar/remover componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="83432-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="83432-186">No **Assistente de componentes do Windows**, selecione o **serviços de informações da Internet (IIS)** caixa de seleção e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="83432-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="83432-187">Se o **arquivos necessários** caixa de diálogo é exibida, insira o disco de instalação do sistema operacional, navegue até a pasta i386 e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="83432-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="83432-188">Quando a instalação for concluída, clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="83432-188">When installation completes, click **Finish**.</span></span>  
  
6.  <span data-ttu-id="83432-189">Feche o **adicionar ou remover programas** caixa de diálogo e, em seguida, feche **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="83432-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="83432-190">Para verificar a instalação do IIS e ASP.NET</span><span class="sxs-lookup"><span data-stu-id="83432-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1.  <span data-ttu-id="83432-191">Salve o arquivo HTML encontrado no final deste tópico no diretório raiz \InetPub\wwwroot e nomeie-a como Default. aspx.</span><span class="sxs-lookup"><span data-stu-id="83432-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2.  <span data-ttu-id="83432-192">Abra uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="83432-192">Open a browser window.</span></span>  
  
3.  <span data-ttu-id="83432-193">Tipo `http://localhost/Default.aspx` na caixa de endereço e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="83432-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="83432-194">Uma página da Web com o texto "Hello World" deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="83432-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83432-195">Cada vez que você instala uma nova versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], é necessário registrar novamente aspnet_isapi como uma extensão de serviço da Web do IIS.</span><span class="sxs-lookup"><span data-stu-id="83432-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="83432-196">Para fazer isso, emita o `aspnet_regiis –I –enable` comando.</span><span class="sxs-lookup"><span data-stu-id="83432-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="83432-197">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="83432-197">Sample Code</span></span>  
  
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
