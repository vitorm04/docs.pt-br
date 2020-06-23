---
title: Como instalar e configurar componentes de ativação do WCF
description: Saiba como configurar o WAS (serviço de ativação de processos do Windows) no Windows Vista para hospedar serviços WCF que não se comunicam via HTTP.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 84a0dcc4fed28ebd7a536bdabfcdc389be6072d8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246877"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="644b5-103">Como instalar e configurar componentes de ativação do WCF</span><span class="sxs-lookup"><span data-stu-id="644b5-103">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="644b5-104">Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) no Windows Vista para hospedar serviços de Windows Communication Foundation (WCF) que não se comunicam por protocolos de rede HTTP.</span><span class="sxs-lookup"><span data-stu-id="644b5-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="644b5-105">As seções a seguir descrevem as etapas para essa configuração:</span><span class="sxs-lookup"><span data-stu-id="644b5-105">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="644b5-106">Instale (ou confirme a instalação do) dos componentes de ativação do WCF.</span><span class="sxs-lookup"><span data-stu-id="644b5-106">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="644b5-107">Configurar o WAS para dar suporte a um protocolo não HTTP.</span><span class="sxs-lookup"><span data-stu-id="644b5-107">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="644b5-108">O procedimento a seguir configura o Windows Vista para ativação TCP.</span><span class="sxs-lookup"><span data-stu-id="644b5-108">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="644b5-109">Depois de instalar e configurar o WAS, consulte [como hospedar um serviço WCF no was](how-to-host-a-wcf-service-in-was.md) para os procedimentos para criar um serviço WCF que expõe um ponto de extremidade não http que emprega o was.</span><span class="sxs-lookup"><span data-stu-id="644b5-109">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="644b5-110">Para instalar os componentes de ativação não HTTP do WCF</span><span class="sxs-lookup"><span data-stu-id="644b5-110">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="644b5-111">Clique no botão **Iniciar** e clique em **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="644b5-111">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="644b5-112">Clique em **Programas** e clique em **Programas e Recursos**.</span><span class="sxs-lookup"><span data-stu-id="644b5-112">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="644b5-113">No menu **tarefas** , clique em **Ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="644b5-113">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="644b5-114">Localize o nó WinFX, selecione e expanda-o.</span><span class="sxs-lookup"><span data-stu-id="644b5-114">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="644b5-115">Selecione a caixa **componentes de ativação não http do WCF** e salve a configuração.</span><span class="sxs-lookup"><span data-stu-id="644b5-115">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="644b5-116">Para configurar o WAS para dar suporte à ativação de TCP</span><span class="sxs-lookup"><span data-stu-id="644b5-116">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="644b5-117">Para dar suporte à ativação net. TCP, o site padrão deve primeiro ser associado a uma porta Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="644b5-117">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="644b5-118">Você pode fazer isso usando Appcmd.exe, que é instalado com o conjunto de ferramentas de gerenciamento do IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="644b5-118">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="644b5-119">Em uma janela de prompt de comando de nível de administrador, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="644b5-119">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="644b5-120">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="644b5-120">This command is a single line of text.</span></span> <span data-ttu-id="644b5-121">Esse comando adiciona uma associação de site net. TCP ao site padrão escutando na porta TCP 808 com qualquer nome de host.</span><span class="sxs-lookup"><span data-stu-id="644b5-121">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="644b5-122">Embora todos os aplicativos em um site compartilhem uma associação net. TCP comum, cada aplicativo pode habilitar o suporte a net. TCP individualmente.</span><span class="sxs-lookup"><span data-stu-id="644b5-122">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="644b5-123">Para habilitar net. TCP para o aplicativo, execute o comando a seguir em um prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="644b5-123">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="644b5-124">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="644b5-124">This command is a single line of text.</span></span> <span data-ttu-id="644b5-125">Esse comando permite que o/ \<*WCF Application*> aplicativo seja acessado usando o `http://localhost/<WCF Application>` e o `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="644b5-125">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="644b5-126">Remova a associação de site net. TCP que você adicionou para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="644b5-126">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="644b5-127">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding. cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="644b5-127">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="644b5-128">Remova net. TCP da lista de protocolos habilitados executando o comando a seguir em uma janela de prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="644b5-128">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="644b5-129">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="644b5-129">This command is a single line of text.</span></span>

    2. <span data-ttu-id="644b5-130">Remova a associação de site net. TCP executando o seguinte comando em uma janela de prompt de comandos com privilégios elevados:</span><span class="sxs-lookup"><span data-stu-id="644b5-130">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="644b5-131">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="644b5-131">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="644b5-132">Para remover net. TCP da lista de protocolos habilitados</span><span class="sxs-lookup"><span data-stu-id="644b5-132">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="644b5-133">Para remover net. TCP da lista de protocolos habilitados, execute o comando a seguir em uma janela de prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="644b5-133">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="644b5-134">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="644b5-134">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="644b5-135">Para remover a associação do site net. TCP</span><span class="sxs-lookup"><span data-stu-id="644b5-135">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="644b5-136">Para remover a associação de site net. TCP, execute o comando a seguir em uma janela de prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="644b5-136">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="644b5-137">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="644b5-137">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="644b5-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="644b5-138">See also</span></span>

- [<span data-ttu-id="644b5-139">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="644b5-139">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="644b5-140">Ativação de MSMQ</span><span class="sxs-lookup"><span data-stu-id="644b5-140">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="644b5-141">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="644b5-141">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="644b5-142">[Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="644b5-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
