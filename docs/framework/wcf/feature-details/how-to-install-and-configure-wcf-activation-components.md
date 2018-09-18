---
title: Como instalar e configurar componentes de ativação do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 8b516bb4603f33828069b5356676d8b35dc961d2
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46008925"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="42a4d-102">Como instalar e configurar componentes de ativação do WCF</span><span class="sxs-lookup"><span data-stu-id="42a4d-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="42a4d-103">Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) em [!INCLUDE[wv](../../../../includes/wv-md.md)] para hospedar o Windows Communication Foundation (WCF) protocolos de rede de serviços que não se comunicam por HTTP.</span><span class="sxs-lookup"><span data-stu-id="42a4d-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="42a4d-104">As seções a seguir descrevem as etapas para essa configuração:</span><span class="sxs-lookup"><span data-stu-id="42a4d-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="42a4d-105">Instalar (ou confirmar a instalação do) os componentes de ativação do WCF.</span><span class="sxs-lookup"><span data-stu-id="42a4d-105">Install (or confirm the installation of) the WCF activation components.</span></span>  
  
-   <span data-ttu-id="42a4d-106">Configure o WAS para dar suporte a um protocolo não HTTP.</span><span class="sxs-lookup"><span data-stu-id="42a4d-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="42a4d-107">O procedimento a seguir configura [!INCLUDE[wv](../../../../includes/wv-md.md)] para ativação de TCP.</span><span class="sxs-lookup"><span data-stu-id="42a4d-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="42a4d-108">Depois de instalar e configurar o WAS, consulte [como: hospedar um serviço WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) para os procedimentos para criar um serviço WCF que expõe um ponto de extremidade HTTP não emprega o WAS.</span><span class="sxs-lookup"><span data-stu-id="42a4d-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="42a4d-109">Para instalar os componentes de ativação não HTTP do WCF</span><span class="sxs-lookup"><span data-stu-id="42a4d-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="42a4d-110">Clique o **inicie** botão e, em seguida, clique em **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="42a4d-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="42a4d-111">Clique em **programas**e, em seguida, clique em **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="42a4d-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="42a4d-112">Sobre o **tarefas** menu, clique em **ou desativar recursos do Windows ativar**.</span><span class="sxs-lookup"><span data-stu-id="42a4d-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="42a4d-113">Encontre o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] nó, selecione e expanda-lo.</span><span class="sxs-lookup"><span data-stu-id="42a4d-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="42a4d-114">Selecione o **componentes de ativação não Http WCF** caixa e salvar a configuração.</span><span class="sxs-lookup"><span data-stu-id="42a4d-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="42a4d-115">Para configurar o WAS para dar suporte à ativação TCP</span><span class="sxs-lookup"><span data-stu-id="42a4d-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="42a4d-116">Para dar suporte à ativação de NET. TCP, o site padrão primeiro deve ser associado a uma porta NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="42a4d-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="42a4d-117">Você pode fazer isso usando Appcmd.exe, que é instalado com o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] conjunto de ferramentas de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="42a4d-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="42a4d-118">Em uma janela de Prompt de comando com nível de administrador, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="42a4d-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="42a4d-119">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="42a4d-119">This command is a single line of text.</span></span> <span data-ttu-id="42a4d-120">Este comando adiciona uma associação de site do NET. TCP para o site padrão escuta na porta TCP 808 com qualquer nome de host.</span><span class="sxs-lookup"><span data-stu-id="42a4d-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="42a4d-121">Embora todos os aplicativos dentro de um site compartilham uma associação comum de NET. TCP, cada aplicativo pode habilitar o suporte do NET. TCP individualmente.</span><span class="sxs-lookup"><span data-stu-id="42a4d-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="42a4d-122">Para habilitar o NET. TCP para o aplicativo, execute o seguinte comando em um prompt de comando com nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="42a4d-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="42a4d-123">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="42a4d-123">This command is a single line of text.</span></span> <span data-ttu-id="42a4d-124">Este comando habilita o /\<*aplicativo WCF*> aplicativo seja acessado usando ambos `http://localhost/<WCF Application>` e `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="42a4d-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>
  
     <span data-ttu-id="42a4d-125">Remova a associação de site do NET. TCP que é adicionado para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="42a4d-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="42a4d-126">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding.cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="42a4d-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="42a4d-127">Remova o NET. TCP da lista de protocolos habilitados, executando o seguinte comando em uma janela de Prompt de comando com nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="42a4d-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="42a4d-128">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="42a4d-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="42a4d-129">Remova a associação do site NET. TCP, executando o seguinte comando em uma janela elevada de Prompt de comando:</span><span class="sxs-lookup"><span data-stu-id="42a4d-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="42a4d-130">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="42a4d-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="42a4d-131">Para remover o NET. TCP da lista de protocolos habilitados</span><span class="sxs-lookup"><span data-stu-id="42a4d-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="42a4d-132">Para remover o NET. TCP da lista de protocolos habilitados, execute o seguinte comando em uma janela de Prompt de comando com nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="42a4d-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="42a4d-133">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="42a4d-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="42a4d-134">Para remover a associação de site do NET. TCP</span><span class="sxs-lookup"><span data-stu-id="42a4d-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="42a4d-135">Para remover o site do NET. TCP associação execute o seguinte comando em uma janela de Prompt de comando com nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="42a4d-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="42a4d-136">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="42a4d-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a4d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42a4d-137">See Also</span></span>  
 [<span data-ttu-id="42a4d-138">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="42a4d-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="42a4d-139">Ativação de MSMQ</span><span class="sxs-lookup"><span data-stu-id="42a4d-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="42a4d-140">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="42a4d-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="42a4d-141">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="42a4d-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
