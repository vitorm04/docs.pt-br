---
title: Instruções de definição de diretório virtual
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 3ff578b69590071ef2135e777b3105e7c226563e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806907"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="b4565-102">Instruções de definição de diretório virtual</span><span class="sxs-lookup"><span data-stu-id="b4565-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="b4565-103">Os exemplos do Windows Communication Foundation (WCF) devem compartilhar um diretório virtual comum denominado servicemodelsamples que é mapeada para a pasta %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4565-104">% SystemDrive % normalmente é c: ou d:., dependendo do local de unidade em que os serviços de informações da Internet (IIS) está instalado.</span><span class="sxs-lookup"><span data-stu-id="b4565-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="b4565-105">Você pode executar os arquivos de Setupvroot.bat e Cleanupvroot.bat o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) para criar o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="b4565-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="b4565-106">Se você preferir criar o diretório virtual manualmente, use os procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4565-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="b4565-107">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="b4565-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="b4565-108">Para criar um diretório virtual no IIS 7.0 ou 7.5</span><span class="sxs-lookup"><span data-stu-id="b4565-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="b4565-109">Do **iniciar** menu, clique em **executar**, em seguida, digite **inetmgr** para abrir o snap-in MMC de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="b4565-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="b4565-110">No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o **Sites** nó.</span><span class="sxs-lookup"><span data-stu-id="b4565-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="b4565-111">Clique com botão direito **Default Web Site**e, em seguida, selecione **Adicionar aplicativo** para abrir o **janela Adicionar aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="b4565-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="b4565-112">Na janela, digite `servicemodelsamples` como o alias do diretório virtual que você está criando.</span><span class="sxs-lookup"><span data-stu-id="b4565-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="b4565-113">Crie o seguinte diretório: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="b4565-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="b4565-114">Defina o caminho físico para % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="b4565-115">A maioria dos exemplos do WCF copia arquivos executáveis de serviço para esse local quando compilado.</span><span class="sxs-lookup"><span data-stu-id="b4565-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="b4565-116">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4565-116">Click **OK**.</span></span> <span data-ttu-id="b4565-117">O aplicativo Web é criado para os exemplos do WCF.</span><span class="sxs-lookup"><span data-stu-id="b4565-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4565-118">Essa tarefa deve ser executada apenas uma vez, porque todos os exemplos WCF usam o servicemodelsamples mesmo aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="b4565-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4565-119">Para fins desta documentação, o termo `virtual directory` é sinônimo de `Web application`.</span><span class="sxs-lookup"><span data-stu-id="b4565-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="b4565-120">Além de criar o diretório virtual, você também deve definir suas propriedades para habilitar os serviços do WCF executar.</span><span class="sxs-lookup"><span data-stu-id="b4565-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="b4565-121">Veja mais detalhes a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4565-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="b4565-122">Para criar um diretório virtual no IIS 5.1 ou 6.0</span><span class="sxs-lookup"><span data-stu-id="b4565-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="b4565-123">Abra uma janela de prompt de comando e digite `start inetmgr` para abrir o snap-in MMC de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="b4565-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="b4565-124">No painel esquerdo, expanda o nó com o nome do computador e, em seguida, expanda o **Sites da Web** nó.</span><span class="sxs-lookup"><span data-stu-id="b4565-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="b4565-125">Clique com botão direito **Default Web Site** e selecione **novo, o diretório Virtual** para abrir o Assistente de criação de diretório Virtual.</span><span class="sxs-lookup"><span data-stu-id="b4565-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="b4565-126">No assistente, digite `servicemodelsamples` como o alias do diretório virtual que você está criando.</span><span class="sxs-lookup"><span data-stu-id="b4565-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="b4565-127">Defina o caminho % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="b4565-128">A maioria dos exemplos do WCF copia arquivos executáveis de serviço para esse local quando compilado.</span><span class="sxs-lookup"><span data-stu-id="b4565-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="b4565-129">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="b4565-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="b4565-130">Por padrão, as seguintes caixas de seleção são selecionadas:</span><span class="sxs-lookup"><span data-stu-id="b4565-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="b4565-131">**Leitura**</span><span class="sxs-lookup"><span data-stu-id="b4565-131">**Read**</span></span>  
  
    -   <span data-ttu-id="b4565-132">**Executar scripts (como ASP)**</span><span class="sxs-lookup"><span data-stu-id="b4565-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="b4565-133">Clique em **próximo**e, em seguida, clique em **concluir** para concluir o assistente.</span><span class="sxs-lookup"><span data-stu-id="b4565-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4565-134">Essa tarefa deve ser executada apenas uma vez porque todos os exemplos WCF usam o mesmo diretório virtual servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="b4565-135">Para definir propriedades adicionais de diretório virtual no IIS 7.0 ou 7.5</span><span class="sxs-lookup"><span data-stu-id="b4565-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="b4565-136">Clique no nó servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="b4565-137">Na parte inferior da janela, duas exibições são listadas.</span><span class="sxs-lookup"><span data-stu-id="b4565-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="b4565-138">Selecione **exibição de recursos** se ainda não estiver selecionada.</span><span class="sxs-lookup"><span data-stu-id="b4565-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="b4565-139">Clique duas vezes na entrada de **pesquisa no diretório**.</span><span class="sxs-lookup"><span data-stu-id="b4565-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="b4565-140">No painel Ações, selecione o **habilitar** opção.</span><span class="sxs-lookup"><span data-stu-id="b4565-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="b4565-141">Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que é útil quando a depuração de um serviço.</span><span class="sxs-lookup"><span data-stu-id="b4565-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="b4565-142">Por fim, você deve definir as propriedades de segurança da pasta servicemodelsamples para permitir que ele seja acessado por outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="b4565-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="b4565-143">Veja mais detalhes a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4565-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="b4565-144">Para definir propriedades adicionais de diretório virtual no IIS 5.1 ou 6.0</span><span class="sxs-lookup"><span data-stu-id="b4565-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="b4565-145">Com o botão direito no nó servicemodelsamples e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b4565-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b4565-146">Por padrão, as seguintes caixas de seleção são selecionadas:</span><span class="sxs-lookup"><span data-stu-id="b4565-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="b4565-147">**Leitura**</span><span class="sxs-lookup"><span data-stu-id="b4565-147">**Read**</span></span>  
  
    -   <span data-ttu-id="b4565-148">**Criar log de visitantes**</span><span class="sxs-lookup"><span data-stu-id="b4565-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="b4565-149">**Indexar este recurso**</span><span class="sxs-lookup"><span data-stu-id="b4565-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="b4565-150">Selecione o **pesquisa no diretório** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="b4565-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="b4565-151">Isso permite que você acesse o diretório do diretório usando o Internet Explorer, que é útil quando a depuração de um serviço.</span><span class="sxs-lookup"><span data-stu-id="b4565-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="b4565-152">Para definir propriedades de segurança da pasta no IIS 7.0 ou 7.5</span><span class="sxs-lookup"><span data-stu-id="b4565-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="b4565-153">Navegue até % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="b4565-154">Clique na pasta servicemodelsamples e clique em **compartilhamento** ou **compartilhamento com**.</span><span class="sxs-lookup"><span data-stu-id="b4565-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="b4565-155">Clique na seta para baixo à esquerda do **adicionar** botão.</span><span class="sxs-lookup"><span data-stu-id="b4565-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="b4565-156">Selecione o **localizar** entrada.</span><span class="sxs-lookup"><span data-stu-id="b4565-156">Select the **Find** entry.</span></span> <span data-ttu-id="b4565-157">O **selecionar usuários ou grupos** janela será aberta.</span><span class="sxs-lookup"><span data-stu-id="b4565-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="b4565-158">Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="b4565-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="b4565-159">Clique em **locais**.</span><span class="sxs-lookup"><span data-stu-id="b4565-159">Click **Locations**.</span></span> <span data-ttu-id="b4565-160">O **locais** janela agora está aberta.</span><span class="sxs-lookup"><span data-stu-id="b4565-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="b4565-161">Selecione a entrada para o computador que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="b4565-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="b4565-162">É importante selecionar o computador local e não uma entrada para qualquer domínios ou redes que estão listadas.</span><span class="sxs-lookup"><span data-stu-id="b4565-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="b4565-163">Depois de selecionar o computador, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b4565-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="b4565-164">Clique em **Localizar agora**.</span><span class="sxs-lookup"><span data-stu-id="b4565-164">Click **Find Now**.</span></span> <span data-ttu-id="b4565-165">Isso preenche os resultados da pesquisa com os objetos associados ao computador local.</span><span class="sxs-lookup"><span data-stu-id="b4565-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="b4565-166">Localizar o **IIS_IUSRS** entrada o **nome (nome distinto relativo)** coluna.</span><span class="sxs-lookup"><span data-stu-id="b4565-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="b4565-167">Selecione a entrada e clique em **Okey** fechar a pesquisa de janela de resultados.</span><span class="sxs-lookup"><span data-stu-id="b4565-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="b4565-168">Clique em **Okey** para fechar o **selecionar usuários ou grupos** janela.</span><span class="sxs-lookup"><span data-stu-id="b4565-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="b4565-169">Clique em **compartilhamento** para manter as alterações.</span><span class="sxs-lookup"><span data-stu-id="b4565-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="b4565-170">Depois que as alterações para permitir o compartilhamento forem concluídas, clique em **feito** para fechar o **compartilhamento de arquivos** janela.</span><span class="sxs-lookup"><span data-stu-id="b4565-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="b4565-171">Para definir propriedades de segurança da pasta no IIS 5.1 ou 6.0</span><span class="sxs-lookup"><span data-stu-id="b4565-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="b4565-172">Navegue até % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b4565-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="b4565-173">Clique com botão direito do **servicemodelsamples** pasta e clique **compartilhamento e segurança.**</span><span class="sxs-lookup"><span data-stu-id="b4565-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="b4565-174">Clique na guia **Segurança**.</span><span class="sxs-lookup"><span data-stu-id="b4565-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="b4565-175">Se você estiver usando o IIS 6.0 no **nomes de grupo ou usuário** caixa de seleção se **conta de convidado da Internet** está listado.</span><span class="sxs-lookup"><span data-stu-id="b4565-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="b4565-176">Se não estiver listado:</span><span class="sxs-lookup"><span data-stu-id="b4565-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="b4565-177">Clique em **iniciar** e, em seguida, clique em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="b4565-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="b4565-178">Se você não vir o **contas de usuário** ícone, clique em **alternar para modo de exibição de categoria**.</span><span class="sxs-lookup"><span data-stu-id="b4565-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="b4565-179">Clique o **contas de usuário** ícone.</span><span class="sxs-lookup"><span data-stu-id="b4565-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="b4565-180">Em "ou um ícone do painel de controle," clique **contas de usuário**.</span><span class="sxs-lookup"><span data-stu-id="b4565-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="b4565-181">No **contas de usuário** caixa de diálogo, clique o **avançado** guia.</span><span class="sxs-lookup"><span data-stu-id="b4565-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="b4565-182">Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="b4565-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="b4565-183">No **usuários e grupos locais** caixa de diálogo, clique para expandir o **usuários** pasta.</span><span class="sxs-lookup"><span data-stu-id="b4565-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="b4565-184">No painel direito, clique duas vezes em **conta de convidado da Internet**.</span><span class="sxs-lookup"><span data-stu-id="b4565-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="b4565-185">No **propriedades** caixa de diálogo, copie o nome usado como a conta de convidado da Internet.</span><span class="sxs-lookup"><span data-stu-id="b4565-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="b4565-186">Por padrão, o nome começa com "USR_" seguido do nome do computador.</span><span class="sxs-lookup"><span data-stu-id="b4565-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="b4565-187">Feche a caixa de diálogo **Propriedades** .</span><span class="sxs-lookup"><span data-stu-id="b4565-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="b4565-188">Fechar o **usuários e grupos locais** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="b4565-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="b4565-189">Fechar o **contas de usuário** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="b4565-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="b4565-190">Feche o outro **contas de usuário** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="b4565-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="b4565-191">No **servicemodelsamples propriedades** caixa de diálogo de **segurança** , clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b4565-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="b4565-192">Digite o nome do computador seguido por uma barra invertida e, em seguida, cole o nome da conta de usuário de Internet, por exemplo, myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="b4565-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="b4565-193">Clique em **verificar nomes** para verificar a adição.</span><span class="sxs-lookup"><span data-stu-id="b4565-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="b4565-194">Se ele for válido, o nome está em letras maiusculas e está sublinhado.</span><span class="sxs-lookup"><span data-stu-id="b4565-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="b4565-195">Para o IIS 6.0, verifique também se o serviço de rede está listado no **nomes de grupo ou usuário** caixa.</span><span class="sxs-lookup"><span data-stu-id="b4565-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="b4565-196">Se o serviço de rede não estiver listado:</span><span class="sxs-lookup"><span data-stu-id="b4565-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="b4565-197">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="b4565-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="b4565-198">No **selecionar usuários ou grupos** caixa de diálogo, digite o nome do computador seguido por uma barra invertida.</span><span class="sxs-lookup"><span data-stu-id="b4565-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="b4565-199">Tipo **serviço** após a barra invertida (sem espaço).</span><span class="sxs-lookup"><span data-stu-id="b4565-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="b4565-200">Clique em **verificar nomes**.</span><span class="sxs-lookup"><span data-stu-id="b4565-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="b4565-201">Se forem localizados vários nomes, selecione **serviço de rede** e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="b4565-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="b4565-202">Clique em **Okey** para fechar o **selecionar usuários ou grupos** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="b4565-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="b4565-203">Se você estiver usando o Windows XP SP2 com o IIS 5.1, verifique se a conta de convidado da Internet e ASPNET estão listados no **nomes de grupo ou usuário** caixa.</span><span class="sxs-lookup"><span data-stu-id="b4565-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="b4565-204">Observe que o usuário ASPNET pode ser um membro de interno **usuários** grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="b4565-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="b4565-205">Nesse caso, se, em seguida, o **usuários** grupo está listado na caixa de diálogo, você não precisa adicioná-lo como um item separado para a lista de usuários autorizados.</span><span class="sxs-lookup"><span data-stu-id="b4565-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="b4565-206">Para verificar se ASPNET faz parte do **usuários** grupo de segurança:</span><span class="sxs-lookup"><span data-stu-id="b4565-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="b4565-207">Sobre o **iniciar** menu, clique em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="b4565-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="b4565-208">Clique o **contas de usuário** ícone.</span><span class="sxs-lookup"><span data-stu-id="b4565-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="b4565-209">No **grupo** coluna, verifique se o valor de **ASPNET** for "Users".</span><span class="sxs-lookup"><span data-stu-id="b4565-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4565-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4565-210">See Also</span></span>  
 [<span data-ttu-id="b4565-211">Instruções de hospedagem do Serviços de Informações da Internet</span><span class="sxs-lookup"><span data-stu-id="b4565-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
