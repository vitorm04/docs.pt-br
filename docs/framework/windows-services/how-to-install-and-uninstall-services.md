---
title: 'Como: instalar e desinstalar serviços Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 4f6e25467e713263ab5cdecc08078153098fdede
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690685"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="cfe0d-102">Como: instalar e desinstalar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="cfe0d-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="cfe0d-103">Se você estiver desenvolvendo um serviço Windows usando o .NET Framework, instale rapidamente o aplicativo de serviço usando o utilitário de linha de comando [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cfe0d-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility.</span></span> <span data-ttu-id="cfe0d-104">Os desenvolvedores que desejam lançar um serviço Windows que os usuários possam instalar e desinstalar devem usar o InstallShield.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="cfe0d-105">Para obter mais informações, confira [Criar um pacote do instalador (cliente Windows)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="cfe0d-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

> [!WARNING]
> <span data-ttu-id="cfe0d-106">Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="cfe0d-107">Nesse caso, descubra qual pacote de software ou programa instalou o serviço e, em seguida, escolha **Aplicativos** em Configurações para desinstalar o programa.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="cfe0d-108">Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="cfe0d-109">Para seguir as etapas neste artigo, primeiro você precisa adicionar um instalador de serviço no serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="cfe0d-110">Para obter mais informações, confira [Passo a passo: criando um aplicativo de serviço Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="cfe0d-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="cfe0d-111">Não é possível executar projetos de serviço Windows diretamente no ambiente de desenvolvimento do Visual Studio pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="cfe0d-112">Antes de executar o projeto, você precisa instalar o serviço no projeto.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="cfe0d-113">Você pode usar o **Gerenciador de Servidores** para verificar se instalou ou desinstalou o serviço.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="cfe0d-114">Para obter mais informações, confira [Como usar o Gerenciador de Servidores no Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cfe0d-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually"></a><span data-ttu-id="cfe0d-115">Instalar o serviço manualmente</span><span class="sxs-lookup"><span data-stu-id="cfe0d-115">Install your service manually</span></span>

1. <span data-ttu-id="cfe0d-116">No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>** .</span><span class="sxs-lookup"><span data-stu-id="cfe0d-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="cfe0d-117">O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="cfe0d-118">Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="cfe0d-119">Execute *InstallUtil.exe* do prompt de comando com o executável do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="cfe0d-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="cfe0d-120">Se você estiver usando o Prompt de Comando do Desenvolvedor para Visual Studio, *InstallUtil.exe* deverá estar no caminho do sistema.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="cfe0d-121">Caso contrário, você poderá adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="cfe0d-122">Essa ferramenta é instalada com o .NET Framework em *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>* .</span><span class="sxs-lookup"><span data-stu-id="cfe0d-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="cfe0d-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cfe0d-123">For example:</span></span>
     - <span data-ttu-id="cfe0d-124">para a versão de 32 bits do .NET Framework 4 ou 4.5 e posterior, se o diretório de instalação do Windows for *C:\Windows*, o caminho padrão será *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="cfe0d-125">para a versão de 64 bits do .NET Framework 4 ou 4.5 e posterior, o caminho padrão é *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually"></a><span data-ttu-id="cfe0d-126">Desinstalar o serviço manualmente</span><span class="sxs-lookup"><span data-stu-id="cfe0d-126">Uninstall your service manually</span></span>

1. <span data-ttu-id="cfe0d-127">No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>** .</span><span class="sxs-lookup"><span data-stu-id="cfe0d-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="cfe0d-128">O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="cfe0d-129">Execute *InstallUtil.exe* no prompt de comando com a saída do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="cfe0d-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="cfe0d-130">Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="cfe0d-131">Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.</span><span class="sxs-lookup"><span data-stu-id="cfe0d-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfe0d-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfe0d-132">See also</span></span>

- [<span data-ttu-id="cfe0d-133">Introdução aos aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="cfe0d-133">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="cfe0d-134">Como: criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="cfe0d-134">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="cfe0d-135">Como: adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="cfe0d-135">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="cfe0d-136">Installutil.exe (ferramenta de instalação)</span><span class="sxs-lookup"><span data-stu-id="cfe0d-136">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
