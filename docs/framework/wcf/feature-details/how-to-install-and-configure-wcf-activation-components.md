---
title: Como instalar e configurar componentes de ativação do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 0a7be97ec157638db3eb2d656fe263b37b8d676c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837409"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="62064-102">Como instalar e configurar componentes de ativação do WCF</span><span class="sxs-lookup"><span data-stu-id="62064-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="62064-103">Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) no Windows Vista para hospedar serviços de Windows Communication Foundation (WCF) que não se comunicam por protocolos de rede HTTP.</span><span class="sxs-lookup"><span data-stu-id="62064-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="62064-104">As seções a seguir descrevem as etapas para essa configuração:</span><span class="sxs-lookup"><span data-stu-id="62064-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="62064-105">Instale (ou confirme a instalação do) dos componentes de ativação do WCF.</span><span class="sxs-lookup"><span data-stu-id="62064-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="62064-106">Configurar o WAS para dar suporte a um protocolo não HTTP.</span><span class="sxs-lookup"><span data-stu-id="62064-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="62064-107">O procedimento a seguir configura o Windows Vista para ativação TCP.</span><span class="sxs-lookup"><span data-stu-id="62064-107">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="62064-108">Depois de instalar e configurar o WAS, consulte [como hospedar um serviço WCF no was](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) para os procedimentos para criar um serviço WCF que expõe um ponto de extremidade não http que emprega o was.</span><span class="sxs-lookup"><span data-stu-id="62064-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="62064-109">Para instalar os componentes de ativação não HTTP do WCF</span><span class="sxs-lookup"><span data-stu-id="62064-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="62064-110">Clique no botão **Iniciar** e em painel de **controle**.</span><span class="sxs-lookup"><span data-stu-id="62064-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="62064-111">Clique em **Programas** e clique em **Programas e Recursos**.</span><span class="sxs-lookup"><span data-stu-id="62064-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="62064-112">No menu **tarefas** , clique em **Ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="62064-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="62064-113">Localize o nó WinFX, selecione e expanda-o.</span><span class="sxs-lookup"><span data-stu-id="62064-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="62064-114">Selecione a caixa **componentes de ativação não http do WCF** e salve a configuração.</span><span class="sxs-lookup"><span data-stu-id="62064-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="62064-115">Para configurar o WAS para dar suporte à ativação de TCP</span><span class="sxs-lookup"><span data-stu-id="62064-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="62064-116">Para dar suporte à ativação net. TCP, o site padrão deve primeiro ser associado a uma porta Net. TCP.</span><span class="sxs-lookup"><span data-stu-id="62064-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="62064-117">Você pode fazer isso usando AppCmd. exe, que é instalado com o conjunto de ferramentas de gerenciamento do IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="62064-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="62064-118">Em uma janela de prompt de comando de nível de administrador, execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="62064-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="62064-119">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="62064-119">This command is a single line of text.</span></span> <span data-ttu-id="62064-120">Esse comando adiciona uma associação de site net. TCP ao site padrão escutando na porta TCP 808 com qualquer nome de host.</span><span class="sxs-lookup"><span data-stu-id="62064-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="62064-121">Embora todos os aplicativos em um site compartilhem uma associação net. TCP comum, cada aplicativo pode habilitar o suporte a net. TCP individualmente.</span><span class="sxs-lookup"><span data-stu-id="62064-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="62064-122">Para habilitar net. TCP para o aplicativo, execute o comando a seguir em um prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="62064-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="62064-123">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="62064-123">This command is a single line of text.</span></span> <span data-ttu-id="62064-124">Esse comando habilita o aplicativo *WCF*de > de\<para ser acessado usando `http://localhost/<WCF Application>` e `net.tcp://localhost/<WCF Application>`.</span><span class="sxs-lookup"><span data-stu-id="62064-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="62064-125">Remova a associação de site net. TCP que você adicionou para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="62064-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="62064-126">Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding. cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="62064-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="62064-127">Remova net. TCP da lista de protocolos habilitados executando o comando a seguir em uma janela de prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="62064-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="62064-128">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="62064-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="62064-129">Remova a associação de site net. TCP executando o seguinte comando em uma janela de prompt de comandos com privilégios elevados:</span><span class="sxs-lookup"><span data-stu-id="62064-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="62064-130">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="62064-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="62064-131">Para remover net. TCP da lista de protocolos habilitados</span><span class="sxs-lookup"><span data-stu-id="62064-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="62064-132">Para remover net. TCP da lista de protocolos habilitados, execute o comando a seguir em uma janela de prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="62064-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="62064-133">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="62064-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="62064-134">Para remover a associação do site net. TCP</span><span class="sxs-lookup"><span data-stu-id="62064-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="62064-135">Para remover a associação de site net. TCP, execute o comando a seguir em uma janela de prompt de comando de nível de administrador.</span><span class="sxs-lookup"><span data-stu-id="62064-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="62064-136">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="62064-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="62064-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62064-137">See also</span></span>

- [<span data-ttu-id="62064-138">Ativação TCP</span><span class="sxs-lookup"><span data-stu-id="62064-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [<span data-ttu-id="62064-139">Ativação de MSMQ</span><span class="sxs-lookup"><span data-stu-id="62064-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [<span data-ttu-id="62064-140">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="62064-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [<span data-ttu-id="62064-141">Recursos de hospedagem do Windows Server app Fabric</span><span class="sxs-lookup"><span data-stu-id="62064-141">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
