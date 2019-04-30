---
title: Instruções de hospedagem de serviço de informação de internet
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: f5aa276bc1178f3e7c61af7505fcf54df8b934e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954850"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="adc5a-102">Instruções de hospedagem de serviço de informação de internet</span><span class="sxs-lookup"><span data-stu-id="adc5a-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="adc5a-103">Para executar os exemplos que são hospedados por serviços de informações da Internet (IIS), certifique-se de que o IIS está instalado corretamente e está em execução.</span><span class="sxs-lookup"><span data-stu-id="adc5a-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="adc5a-104">Para instalar o IIS versão 7.5 no Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="adc5a-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="adc5a-105">Partir **Gerenciador de servidores**, selecione **funções.**</span><span class="sxs-lookup"><span data-stu-id="adc5a-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="adc5a-106">Sob **resumo de funções**, clique em **adicionar funções**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="adc5a-107">Clique em **próxima** para exibir o **selecionar funções de servidor** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="adc5a-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="adc5a-108">Selecione **servidor de aplicativos** da **funções** e, em seguida, clique **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="adc5a-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="adc5a-109">Selecione o **servidor Web (IIS)** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="adc5a-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="adc5a-110">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="adc5a-111">Clique em **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="adc5a-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="adc5a-112">Expandir **as ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade com gerenciamento do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="adc5a-113">Selecione **IIS ferramentas de script 6**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="adc5a-114">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="adc5a-115">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="adc5a-116">Se o resumo das seleções estiver correto, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="adc5a-117">Quando a instalação for concluída, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="adc5a-118">Para instalar o IIS versão 7.5 no Windows 7</span><span class="sxs-lookup"><span data-stu-id="adc5a-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="adc5a-119">Clique em **inicie**e, em seguida, clique em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="adc5a-120">Abra o **programas** grupo.</span><span class="sxs-lookup"><span data-stu-id="adc5a-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="adc5a-121">Sob **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="adc5a-122">O **User Account Control** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="adc5a-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="adc5a-123">Clique em **Continue**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="adc5a-124">O **recursos do Windows** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="adc5a-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="adc5a-125">Expanda o item rotulado **serviços de informações da Internet**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="adc5a-126">Expanda o item rotulado **serviços da World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="adc5a-127">Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="adc5a-128">Verifique se que os seguintes itens estão selecionados:</span><span class="sxs-lookup"><span data-stu-id="adc5a-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="adc5a-129">**Extensibilidade .NET**</span><span class="sxs-lookup"><span data-stu-id="adc5a-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="adc5a-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="adc5a-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="adc5a-131">**Extensões ISAPI**</span><span class="sxs-lookup"><span data-stu-id="adc5a-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="adc5a-132">**Filtros ISAPI**</span><span class="sxs-lookup"><span data-stu-id="adc5a-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="adc5a-133">Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="adc5a-134">Certifique-se **conteúdo estático** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="adc5a-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="adc5a-135">Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="adc5a-136">Certifique-se de que **autenticação do Windows** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="adc5a-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="adc5a-137">Sob o **serviços de informações da Internet** diretório, expanda o item rotulado **ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento do IIS**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="adc5a-138">Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="adc5a-139">Sob o **serviços de informações da Internet** diretório, expanda o item rotulado **Microsoft .NET Framework 3.5.1**e, em seguida, selecione **Windows Communication Foundation Http Activation**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="adc5a-140">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="adc5a-141">Para instalar o IIS versão 7.0 no Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="adc5a-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="adc5a-142">Partir **Gerenciador de servidores**, selecione **funções**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="adc5a-143">Sob **resumo de funções**, clique em **adicionar funções**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="adc5a-144">Clique em **próxima** para exibir o **selecionar funções de servidor** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="adc5a-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="adc5a-145">Selecione **servidor de aplicativos** da **funções** e, em seguida, clique **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para o Função de servidor de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="adc5a-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="adc5a-146">Selecione **servidor Web (IIS)** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="adc5a-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="adc5a-147">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar recursos necessários**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="adc5a-148">Clique em **próxima** duas vezes para exibir o **selecionar serviços de função** caixa de diálogo para a função de servidor Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="adc5a-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="adc5a-149">Expandir **as ferramentas de gerenciamento**e, em seguida, expanda **compatibilidade com gerenciamento do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="adc5a-150">Selecione **IIS ferramentas de script 6**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="adc5a-151">Se você for solicitado a instalar os serviços de função adicionais e recursos, clique em **adicionar serviços de função necessários**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="adc5a-152">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="adc5a-153">Se o resumo das seleções estiver correto, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="adc5a-154">Quando a instalação for concluída, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="adc5a-155">Para instalar o IIS versão 7.0 no Windows Vista</span><span class="sxs-lookup"><span data-stu-id="adc5a-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="adc5a-156">Clique em Iniciar e, em seguida, clique em Painel de controle.</span><span class="sxs-lookup"><span data-stu-id="adc5a-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="adc5a-157">Selecione o **programas** grupo.</span><span class="sxs-lookup"><span data-stu-id="adc5a-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="adc5a-158">Sob **programas e recursos**, clique em **ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="adc5a-159">O **User Account Control** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="adc5a-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="adc5a-160">Clique em **Continue**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="adc5a-161">O **recursos do Windows** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="adc5a-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="adc5a-162">Expanda o item rotulado **serviços de informações da Internet**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="adc5a-163">Expanda o item rotulado **serviços da World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="adc5a-164">Expanda o item rotulado **recursos de desenvolvimento de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="adc5a-165">Verifique se que os seguintes itens estão selecionados:</span><span class="sxs-lookup"><span data-stu-id="adc5a-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="adc5a-166">**Extensibilidade .NET**</span><span class="sxs-lookup"><span data-stu-id="adc5a-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="adc5a-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="adc5a-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="adc5a-168">**Extensões ISAPI**</span><span class="sxs-lookup"><span data-stu-id="adc5a-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="adc5a-169">**Filtros ISAPI**</span><span class="sxs-lookup"><span data-stu-id="adc5a-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="adc5a-170">Expanda o item rotulado **as ferramentas de gerenciamento da Web**e, em seguida, selecione **Console de gerenciamento IIS**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="adc5a-171">Sob o item rotulado **serviços da World Wide Web**, expanda **recursos Http comuns**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="adc5a-172">Certifique-se **conteúdo estático** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="adc5a-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="adc5a-173">Sob o item rotulado **serviços da World Wide Web**, expanda **segurança**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="adc5a-174">Certifique-se **autenticação do Windows** está selecionado.</span><span class="sxs-lookup"><span data-stu-id="adc5a-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="adc5a-175">Expanda o item rotulado **compatibilidade de gerenciamento do IIS 6**e, em seguida, selecione **ferramentas de script do IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="adc5a-176">Expanda o item rotulado **Microsoft .NET Framework 3.0**e, em seguida, selecione **Windows Communication Foundation Http Activation**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="adc5a-177">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="adc5a-178">Para instalar o IIS versão 6.0 no Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="adc5a-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="adc5a-179">Partir **gerenciar o servidor**, clique em **adicionar ou remover uma função**e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="adc5a-180">Selecione **servidor de aplicativos (IIS, ASP.NET)** da **função de servidor** e, em seguida, clique **próxima**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="adc5a-181">Selecione **ativar ASP.NET** caixa de seleção e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="adc5a-182">Se o resumo das seleções estiver correto, clique em Avançar.</span><span class="sxs-lookup"><span data-stu-id="adc5a-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="adc5a-183">Para instalar o IIS versão 5.1 no Windows XP com Service Pack 2 e Service Pack 3 instalado</span><span class="sxs-lookup"><span data-stu-id="adc5a-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="adc5a-184">No painel de controle, clique em **adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="adc5a-185">No **adicionar ou remover programas** caixa de diálogo, clique em **Adicionar/remover componentes do Windows**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="adc5a-186">No **Assistente de componentes do Windows**, selecione o **serviços de informações da Internet (IIS)** caixa de seleção e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="adc5a-187">Se o **arquivos necessários** caixa de diálogo é exibida, insira o disco de instalação do sistema operacional, navegue até a pasta i386 e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="adc5a-188">Quando a instalação for concluída, clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="adc5a-189">Feche o **adicionar ou remover programas** caixa de diálogo e, em seguida, feche **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="adc5a-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="adc5a-190">Para verificar a instalação do IIS e ASP.NET</span><span class="sxs-lookup"><span data-stu-id="adc5a-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="adc5a-191">Salve o arquivo HTML encontrado no final deste tópico no diretório raiz \InetPub\wwwroot e nomeie-a como Default. aspx.</span><span class="sxs-lookup"><span data-stu-id="adc5a-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="adc5a-192">Abra uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="adc5a-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="adc5a-193">Tipo `http://localhost/Default.aspx` na caixa de endereço e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="adc5a-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="adc5a-194">Uma página da Web com o texto "Hello World" deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="adc5a-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adc5a-195">Cada vez que você instala uma nova versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], é necessário registrar novamente aspnet_isapi como uma extensão de serviço da Web do IIS.</span><span class="sxs-lookup"><span data-stu-id="adc5a-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="adc5a-196">Para fazer isso, emita o `aspnet_regiis –I –enable` comando.</span><span class="sxs-lookup"><span data-stu-id="adc5a-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="adc5a-197">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="adc5a-197">Sample Code</span></span>  
  
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
