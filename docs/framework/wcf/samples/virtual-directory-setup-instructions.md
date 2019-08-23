---
title: Instruções de definição de diretório virtual
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: f755fadf6bef2bdd58fd31f3460a143b8f52eddf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966734"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="cb41a-102">Instruções de definição de diretório virtual</span><span class="sxs-lookup"><span data-stu-id="cb41a-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="cb41a-103">Os exemplos de Windows Communication Foundation (WCF) destinam-se a compartilhar um diretório virtual comum denominado servicemodelsamples que é mapeado para a pasta%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb41a-104">% SystemDrive% geralmente é C: ou D:, dependendo do local da unidade em que o Serviços de Informações da Internet (IIS) está instalado.</span><span class="sxs-lookup"><span data-stu-id="cb41a-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="cb41a-105">Você pode executar os arquivos Setupvroot. bat e Cleanupvroot. bat do [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) para criar o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="cb41a-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="cb41a-106">Se preferir criar o diretório virtual manualmente, use os procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb41a-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="cb41a-107">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="cb41a-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="cb41a-108">Para criar um diretório virtual no IIS 7,0 ou 7,5</span><span class="sxs-lookup"><span data-stu-id="cb41a-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cb41a-109">No menu **Iniciar** , clique em **executar**e digite **inetmgr** para abrir o snap-in do MMC serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="cb41a-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="cb41a-110">No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o nó **sites** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="cb41a-111">Clique com o botão direito do mouse em **site padrão**e selecione **Adicionar aplicativo** para abrir a **janela Adicionar aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="cb41a-112">Na janela, digite `servicemodelsamples` como o alias para o diretório virtual que você está criando.</span><span class="sxs-lookup"><span data-stu-id="cb41a-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="cb41a-113">Crie o seguinte diretório:%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="cb41a-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="cb41a-114">Definir o caminho físico como%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="cb41a-115">A maioria dos exemplos do WCF copia arquivos executáveis do serviço para esse local quando compilado.</span><span class="sxs-lookup"><span data-stu-id="cb41a-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="cb41a-116">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-116">Click **OK**.</span></span> <span data-ttu-id="cb41a-117">O aplicativo Web agora é criado para os exemplos do WCF.</span><span class="sxs-lookup"><span data-stu-id="cb41a-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb41a-118">Essa tarefa deve ser executada apenas uma vez, porque todos os exemplos do WCF usam o mesmo aplicativo Web servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb41a-119">Para a finalidade desta documentação, o termo `virtual directory` é sinônimo `Web application`de.</span><span class="sxs-lookup"><span data-stu-id="cb41a-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="cb41a-120">Além de criar o diretório virtual, você também deve definir suas propriedades para permitir que os serviços WCF sejam executados.</span><span class="sxs-lookup"><span data-stu-id="cb41a-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="cb41a-121">Veja mais detalhes a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb41a-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="cb41a-122">Para criar um diretório virtual no IIS 5,1 ou 6,0</span><span class="sxs-lookup"><span data-stu-id="cb41a-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cb41a-123">Abra uma janela de prompt de comando `start inetmgr` e digite para abrir o snap-in do MMC serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="cb41a-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="cb41a-124">No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o nó **sites** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="cb41a-125">Clique com o botão direito do mouse em **site padrão** e selecione **novo, diretório virtual** para abrir o assistente para criação de diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="cb41a-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="cb41a-126">No assistente, digite `servicemodelsamples` como o alias para o diretório virtual que você está criando.</span><span class="sxs-lookup"><span data-stu-id="cb41a-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="cb41a-127">Defina o caminho para%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="cb41a-128">A maioria dos exemplos do WCF copia arquivos executáveis do serviço para esse local quando compilado.</span><span class="sxs-lookup"><span data-stu-id="cb41a-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="cb41a-129">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="cb41a-130">Por padrão, as seguintes caixas de seleção são selecionadas:</span><span class="sxs-lookup"><span data-stu-id="cb41a-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="cb41a-131">**Ler**</span><span class="sxs-lookup"><span data-stu-id="cb41a-131">**Read**</span></span>  
  
    - <span data-ttu-id="cb41a-132">**Executar scripts (como ASP)**</span><span class="sxs-lookup"><span data-stu-id="cb41a-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="cb41a-133">Clique em **Avançar**e em **concluir** para concluir o assistente.</span><span class="sxs-lookup"><span data-stu-id="cb41a-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb41a-134">Esta tarefa deve ser executada apenas uma vez porque todos os exemplos do WCF usam o mesmo diretório virtual servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="cb41a-135">Para definir propriedades de diretório virtual adicionais no IIS 7,0 ou 7,5</span><span class="sxs-lookup"><span data-stu-id="cb41a-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cb41a-136">Clique no nó servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="cb41a-137">Ao longo da parte inferior da janela, são listadas duas exibições.</span><span class="sxs-lookup"><span data-stu-id="cb41a-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="cb41a-138">Selecione **recursos exibir** se ainda não estiver selecionado.</span><span class="sxs-lookup"><span data-stu-id="cb41a-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="cb41a-139">Clique duas vezes na entrada para **pesquisa no diretório**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="cb41a-140">No painel Ações, selecione a opção **habilitar** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="cb41a-141">Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que ajuda a depurar um serviço.</span><span class="sxs-lookup"><span data-stu-id="cb41a-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="cb41a-142">Por fim, você deve definir as propriedades de segurança da pasta servicemodelsamples para permitir que ela seja acessada por outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="cb41a-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="cb41a-143">Veja mais detalhes a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb41a-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="cb41a-144">Para definir propriedades de diretório virtual adicionais no IIS 5,1 ou 6,0</span><span class="sxs-lookup"><span data-stu-id="cb41a-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cb41a-145">Clique com o botão direito do mouse no nó servicemodelsamples e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="cb41a-146">Por padrão, as seguintes caixas de seleção são selecionadas:</span><span class="sxs-lookup"><span data-stu-id="cb41a-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="cb41a-147">**Ler**</span><span class="sxs-lookup"><span data-stu-id="cb41a-147">**Read**</span></span>  
  
    - <span data-ttu-id="cb41a-148">**Registrar visitas**</span><span class="sxs-lookup"><span data-stu-id="cb41a-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="cb41a-149">**Indexar este recurso**</span><span class="sxs-lookup"><span data-stu-id="cb41a-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="cb41a-150">Marque a caixa de seleção **pesquisa no diretório** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="cb41a-151">Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que ajuda a depurar um serviço.</span><span class="sxs-lookup"><span data-stu-id="cb41a-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="cb41a-152">Para definir as propriedades de segurança da pasta no IIS 7,0 ou 7,5</span><span class="sxs-lookup"><span data-stu-id="cb41a-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cb41a-153">Navegue até%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="cb41a-154">Clique com o botão direito do mouse na pasta servicemodelsamples e clique em **compartilhar** ou **compartilhar com**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="cb41a-155">Clique na seta para baixo à esquerda do botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="cb41a-156">Selecione a entrada **Localizar** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-156">Select the **Find** entry.</span></span> <span data-ttu-id="cb41a-157">A janela **Selecionar usuários ou grupos** é aberta.</span><span class="sxs-lookup"><span data-stu-id="cb41a-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="cb41a-158">Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="cb41a-159">Clique em **locais**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-159">Click **Locations**.</span></span> <span data-ttu-id="cb41a-160">A janela **locais** agora está aberta.</span><span class="sxs-lookup"><span data-stu-id="cb41a-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="cb41a-161">Selecione a entrada para o computador que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="cb41a-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="cb41a-162">É importante selecionar o computador local e não uma entrada para todos os domínios ou redes listados.</span><span class="sxs-lookup"><span data-stu-id="cb41a-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="cb41a-163">Depois de selecionar o computador, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="cb41a-164">Clique em **localizar agora**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-164">Click **Find Now**.</span></span> <span data-ttu-id="cb41a-165">Isso popula os resultados da pesquisa com objetos associados ao computador local.</span><span class="sxs-lookup"><span data-stu-id="cb41a-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="cb41a-166">Localize a entrada **IIS_IUSRS** na coluna **nome (nome distinto relativo)** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="cb41a-167">Selecione essa entrada e clique em **OK** para fechar a janela resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="cb41a-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="cb41a-168">Clique em **OK** para fechar a janela **Selecionar usuários ou grupos** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="cb41a-169">Clique em **compartilhar** para manter as alterações.</span><span class="sxs-lookup"><span data-stu-id="cb41a-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="cb41a-170">Depois que as alterações para habilitar o compartilhamento forem concluídas, clique em **concluído** para fechar a janela de **compartilhamento de arquivos** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="cb41a-171">Para definir as propriedades de segurança da pasta no IIS 5,1 ou 6,0</span><span class="sxs-lookup"><span data-stu-id="cb41a-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cb41a-172">Navegue até%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cb41a-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="cb41a-173">Clique com o botão direito do mouse na pasta **servicemodelsamples** e clique em **compartilhamento e segurança.**</span><span class="sxs-lookup"><span data-stu-id="cb41a-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="cb41a-174">Clique na guia **Segurança**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="cb41a-175">Se você estiver usando o IIS 6,0, na caixa **nomes de grupo ou de usuário** , verifique se a conta de convidado da **Internet** está listada.</span><span class="sxs-lookup"><span data-stu-id="cb41a-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="cb41a-176">Se não estiver listado:</span><span class="sxs-lookup"><span data-stu-id="cb41a-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="cb41a-177">Clique em **Iniciar** e em **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="cb41a-178">Se você não vir o ícone **contas de usuário** , clique em **alternar para a exibição de categoria**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="cb41a-179">Clique no ícone **contas de usuário** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="cb41a-180">Em "ou selecione um ícone do painel de controle", clique em **contas de usuário**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="cb41a-181">Na caixa de diálogo **contas de usuário** , clique na guia **avançado** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="cb41a-182">Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="cb41a-183">Na caixa de diálogo **usuários e grupos locais** , clique para expandir a pasta **usuários** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="cb41a-184">No painel direito, clique duas vezes em **conta de convidado da Internet**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="cb41a-185">Na caixa de diálogo **Propriedades** , copie o nome usado como a conta de convidado da Internet.</span><span class="sxs-lookup"><span data-stu-id="cb41a-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="cb41a-186">Por padrão, o nome começa com "USR_" seguido do nome do computador.</span><span class="sxs-lookup"><span data-stu-id="cb41a-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="cb41a-187">Feche a caixa de diálogo **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="cb41a-188">Feche a caixa de diálogo **usuários e grupos locais** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="cb41a-189">Feche a caixa de diálogo **contas de usuário** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="cb41a-190">Feche a caixa de diálogo outras **contas de usuário** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="cb41a-191">Na caixa de diálogo **Propriedades de servicemodelsamples** , na guia **segurança** , clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="cb41a-192">Digite o nome do computador seguido por uma barra invertida e cole o nome da conta de usuário da Internet, por exemplo, MyMachineName\\% InternetGuestAccountName%</span><span class="sxs-lookup"><span data-stu-id="cb41a-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="cb41a-193">Clique em **verificar nomes** para verificar a adição.</span><span class="sxs-lookup"><span data-stu-id="cb41a-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="cb41a-194">Se for válido, o nome estará em letras maiúsculas e será sublinhado.</span><span class="sxs-lookup"><span data-stu-id="cb41a-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="cb41a-195">Para o IIS 6,0, verifique também se serviço de rede está listado na caixa **nomes de grupo ou de usuário** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="cb41a-196">Se o serviço de rede não estiver listado:</span><span class="sxs-lookup"><span data-stu-id="cb41a-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="cb41a-197">Clique em **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="cb41a-198">Na caixa de diálogo **Selecionar usuários ou grupos** , digite o nome do computador seguido por uma barra invertida.</span><span class="sxs-lookup"><span data-stu-id="cb41a-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="cb41a-199">Digite o **serviço** após a barra invertida (sem espaço).</span><span class="sxs-lookup"><span data-stu-id="cb41a-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="cb41a-200">Clique em **verificar nomes**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="cb41a-201">Se vários nomes forem encontrados, selecione **serviço de rede** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="cb41a-202">Clique em **OK** para fechar a caixa de diálogo **Selecionar usuários ou grupos** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="cb41a-203">Se você estiver usando o Windows XP SP2 com o IIS 5,1, verifique se a conta de convidado da Internet e o ASPNET estão listados na caixa **nomes de grupo ou de usuário** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="cb41a-204">Observe que o usuário ASPNET pode ser membro do grupo de segurança **usuários** internos.</span><span class="sxs-lookup"><span data-stu-id="cb41a-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="cb41a-205">Nesse caso, se o grupo **usuários** estiver listado na caixa de diálogo, você não precisará adicioná-lo como um item separado à lista de usuários permitidos.</span><span class="sxs-lookup"><span data-stu-id="cb41a-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="cb41a-206">Para verificar se o ASPNET faz parte do grupo de segurança **usuários** :</span><span class="sxs-lookup"><span data-stu-id="cb41a-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="cb41a-207">No menu **Iniciar** , clique em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="cb41a-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="cb41a-208">Clique no ícone **contas de usuário** .</span><span class="sxs-lookup"><span data-stu-id="cb41a-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="cb41a-209">Na coluna **grupo** , verifique se o valor de **ASPNET** é "Users".</span><span class="sxs-lookup"><span data-stu-id="cb41a-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb41a-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb41a-210">See also</span></span>

- [<span data-ttu-id="cb41a-211">Instruções de hospedagem do Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="cb41a-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
