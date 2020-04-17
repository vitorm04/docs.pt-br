---
title: 'Como: Instalar e desinstalar serviços do Windows'
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
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607913"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="e5824-102">Como: Instalar e desinstalar serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="e5824-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="e5824-103">Se você estiver desenvolvendo um serviço do Windows com o .NET Framework, você pode instalar rapidamente seu aplicativo de serviço usando o utilitário de linha de comando [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) ou [PowerShell](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="e5824-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="e5824-104">Os desenvolvedores que desejam lançar um serviço Windows que os usuários possam instalar e desinstalar devem usar o InstallShield.</span><span class="sxs-lookup"><span data-stu-id="e5824-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="e5824-105">Para obter mais informações, consulte [Criar um pacote de instalação (desktop Windows)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="e5824-105">For more information, see [Create an installer package (Windows desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

> [!WARNING]
> <span data-ttu-id="e5824-106">Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="e5824-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="e5824-107">Nesse caso, descubra qual pacote de software ou programa instalou o serviço e, em seguida, escolha **Aplicativos** em Configurações para desinstalar o programa.</span><span class="sxs-lookup"><span data-stu-id="e5824-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="e5824-108">Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5824-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="e5824-109">Para seguir as etapas neste artigo, primeiro você precisa adicionar um instalador de serviço no serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="e5824-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="e5824-110">Para obter mais informações, consulte [Passo a Passo: Criando um aplicativo de serviço do Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e5824-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="e5824-111">Não é possível executar projetos de serviço Windows diretamente no ambiente de desenvolvimento do Visual Studio pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="e5824-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="e5824-112">Antes de executar o projeto, você precisa instalar o serviço no projeto.</span><span class="sxs-lookup"><span data-stu-id="e5824-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="e5824-113">Você pode usar o **Gerenciador de Servidores** para verificar se instalou ou desinstalou o serviço.</span><span class="sxs-lookup"><span data-stu-id="e5824-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="e5824-114">Para obter mais informações, confira [Como usar o Gerenciador de Servidores no Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e5824-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="e5824-115">Instale seu serviço manualmente usando o utilitário InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="e5824-115">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="e5824-116">No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>**.</span><span class="sxs-lookup"><span data-stu-id="e5824-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="e5824-117">O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.</span><span class="sxs-lookup"><span data-stu-id="e5824-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="e5824-118">Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.</span><span class="sxs-lookup"><span data-stu-id="e5824-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="e5824-119">Execute *InstallUtil.exe* do prompt de comando com o executável do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="e5824-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="e5824-120">Se você estiver usando o Prompt de Comando do Desenvolvedor para Visual Studio, *InstallUtil.exe* deverá estar no caminho do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5824-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="e5824-121">Caso contrário, você poderá adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo.</span><span class="sxs-lookup"><span data-stu-id="e5824-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="e5824-122">Esta ferramenta está instalada com o .NET Framework em *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span><span class="sxs-lookup"><span data-stu-id="e5824-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="e5824-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5824-123">For example:</span></span>
     - <span data-ttu-id="e5824-124">para a versão de 32 bits do .NET Framework 4 ou 4.5 e posterior, se o diretório de instalação do Windows for *C:\Windows*, o caminho padrão será *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="e5824-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="e5824-125">para a versão de 64 bits do .NET Framework 4 ou 4.5 e posterior, o caminho padrão é *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="e5824-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="e5824-126">Desinstale seu serviço manualmente usando o utilitário InstallUtil.exe</span><span class="sxs-lookup"><span data-stu-id="e5824-126">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="e5824-127">No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>**.</span><span class="sxs-lookup"><span data-stu-id="e5824-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="e5824-128">O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.</span><span class="sxs-lookup"><span data-stu-id="e5824-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="e5824-129">Execute *InstallUtil.exe* no prompt de comando com a saída do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="e5824-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="e5824-130">Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro.</span><span class="sxs-lookup"><span data-stu-id="e5824-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="e5824-131">Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.</span><span class="sxs-lookup"><span data-stu-id="e5824-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="e5824-132">Instale seu serviço manualmente usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5824-132">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="e5824-133">No menu **Iniciar,** selecione o diretório **Windows PowerShell** e selecione **O Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e5824-133">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="e5824-134">Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.</span><span class="sxs-lookup"><span data-stu-id="e5824-134">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="e5824-135">Execute o cmdlet [**do New-Service**](/powershell/module/microsoft.powershell.management/new-service) com a saída do seu projeto e um nome de serviço como parâmetros:</span><span class="sxs-lookup"><span data-stu-id="e5824-135">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="e5824-136">Desinstale seu serviço manualmente usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5824-136">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="e5824-137">No menu **Iniciar,** selecione o diretório **Windows PowerShell** e selecione **O Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e5824-137">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="e5824-138">Execute o cmdlet [**remove-service**](/powershell/module/microsoft.powershell.management/remove-service) com o nome do seu serviço como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="e5824-138">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="e5824-139">Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro.</span><span class="sxs-lookup"><span data-stu-id="e5824-139">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="e5824-140">Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.</span><span class="sxs-lookup"><span data-stu-id="e5824-140">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="e5824-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="e5824-141">See also</span></span>

- [<span data-ttu-id="e5824-142">Introdução aos aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="e5824-142">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="e5824-143">Como: Criar serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="e5824-143">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="e5824-144">Como: Adicionar instaladores ao seu aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="e5824-144">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="e5824-145">Installutil.exe (Ferramenta de Instalação)</span><span class="sxs-lookup"><span data-stu-id="e5824-145">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
