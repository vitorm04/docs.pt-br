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
ms.openlocfilehash: 38fc0172b5f97561d69fe495237e95597d7b9727
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003129"
---
# <a name="how-to-install-and-uninstall-windows-services"></a><span data-ttu-id="f0695-102">Como: instalar e desinstalar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="f0695-102">How to: Install and uninstall Windows services</span></span>

<span data-ttu-id="f0695-103">Se você estiver desenvolvendo um serviço do Windows com o .NET Framework, poderá instalar rapidamente seu aplicativo de serviço usando o utilitário de linha de comando [*InstallUtil. exe*](../tools/installutil-exe-installer-tool.md) ou o [PowerShell](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="f0695-103">If you’re developing a Windows service with the .NET Framework, you can quickly install your service app by using the [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) command-line utility or [PowerShell](/powershell/scripting/overview).</span></span> <span data-ttu-id="f0695-104">Os desenvolvedores que desejam lançar um serviço Windows que os usuários possam instalar e desinstalar devem usar o InstallShield.</span><span class="sxs-lookup"><span data-stu-id="f0695-104">Developers who want to release a Windows service that users can install and uninstall should use InstallShield.</span></span> <span data-ttu-id="f0695-105">Para obter mais informações, confira [Criar um pacote do instalador (cliente Windows)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span><span class="sxs-lookup"><span data-stu-id="f0695-105">For more information, see [Create an installer package (Windows client)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

> [!WARNING]
> <span data-ttu-id="f0695-106">Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="f0695-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="f0695-107">Nesse caso, descubra qual pacote de software ou programa instalou o serviço e, em seguida, escolha **Aplicativos** em Configurações para desinstalar o programa.</span><span class="sxs-lookup"><span data-stu-id="f0695-107">Instead, find out which program or software package installed the service, and then choose **Apps** in Settings to uninstall that program.</span></span> <span data-ttu-id="f0695-108">Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="f0695-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>

<span data-ttu-id="f0695-109">Para seguir as etapas neste artigo, primeiro você precisa adicionar um instalador de serviço no serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="f0695-109">To use the steps in this article, you first need to add a service installer to your Windows service.</span></span> <span data-ttu-id="f0695-110">Para obter mais informações, confira [Passo a passo: criando um aplicativo de serviço Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f0695-110">For more information, see [Walkthrough: Creating a Windows service app](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>

<span data-ttu-id="f0695-111">Não é possível executar projetos de serviço Windows diretamente no ambiente de desenvolvimento do Visual Studio pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="f0695-111">You can't run Windows service projects directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="f0695-112">Antes de executar o projeto, você precisa instalar o serviço no projeto.</span><span class="sxs-lookup"><span data-stu-id="f0695-112">Before you can run the project, you must install the service in the project.</span></span>

> [!TIP]
> <span data-ttu-id="f0695-113">Você pode usar o **Gerenciador de Servidores** para verificar se instalou ou desinstalou o serviço.</span><span class="sxs-lookup"><span data-stu-id="f0695-113">You can use **Server Explorer** to verify that you've installed or uninstalled your service.</span></span> <span data-ttu-id="f0695-114">Para obter mais informações, confira [Como usar o Gerenciador de Servidores no Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f0695-114">For more information, see [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).</span></span>

### <a name="install-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="f0695-115">Instale o serviço manualmente usando o utilitário InstallUtil. exe</span><span class="sxs-lookup"><span data-stu-id="f0695-115">Install your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="f0695-116">No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>** .</span><span class="sxs-lookup"><span data-stu-id="f0695-116">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="f0695-117">O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.</span><span class="sxs-lookup"><span data-stu-id="f0695-117">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="f0695-118">Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.</span><span class="sxs-lookup"><span data-stu-id="f0695-118">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="f0695-119">Execute *InstallUtil.exe* do prompt de comando com o executável do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="f0695-119">Run *InstallUtil.exe* from the command prompt with your project's executable as a parameter:</span></span>

    ```console
    installutil <yourproject>.exe
    ```

     <span data-ttu-id="f0695-120">Se você estiver usando o Prompt de Comando do Desenvolvedor para Visual Studio, *InstallUtil.exe* deverá estar no caminho do sistema.</span><span class="sxs-lookup"><span data-stu-id="f0695-120">If you’re using the Developer Command Prompt for Visual Studio, *InstallUtil.exe* should be on the system path.</span></span> <span data-ttu-id="f0695-121">Caso contrário, você poderá adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo.</span><span class="sxs-lookup"><span data-stu-id="f0695-121">Otherwise, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="f0695-122">Essa ferramenta é instalada com o .NET Framework em *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>* .</span><span class="sxs-lookup"><span data-stu-id="f0695-122">This tool is installed with the .NET Framework in *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.</span></span>

     <span data-ttu-id="f0695-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f0695-123">For example:</span></span>
     - <span data-ttu-id="f0695-124">para a versão de 32 bits do .NET Framework 4 ou 4.5 e posterior, se o diretório de instalação do Windows for *C:\Windows*, o caminho padrão será *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="f0695-124">For the 32-bit version of the .NET Framework 4 or 4.5 and later, if your Windows installation directory is *C:\Windows*, the default path is *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>
     - <span data-ttu-id="f0695-125">para a versão de 64 bits do .NET Framework 4 ou 4.5 e posterior, o caminho padrão é *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="f0695-125">For the 64-bit version of the .NET Framework 4 or 4.5 and later, the default path is *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a><span data-ttu-id="f0695-126">Desinstalar o serviço manualmente usando o utilitário InstallUtil. exe</span><span class="sxs-lookup"><span data-stu-id="f0695-126">Uninstall your service manually using InstallUtil.exe utility</span></span>

1. <span data-ttu-id="f0695-127">No menu **Iniciar**, selecione o diretório **Visual Studio \<*versão*>** e, em seguida, selecione o **Prompt de Comando do Desenvolvedor para VS \<*versão*>** .</span><span class="sxs-lookup"><span data-stu-id="f0695-127">From the **Start** menu, select the **Visual Studio \<*version*>** directory, then select **Developer Command Prompt for VS \<*version*>**.</span></span>

     <span data-ttu-id="f0695-128">O Prompt de Comando do Desenvolvedor para Visual Studio é exibido.</span><span class="sxs-lookup"><span data-stu-id="f0695-128">The Developer Command Prompt for Visual Studio appears.</span></span>

2. <span data-ttu-id="f0695-129">Execute *InstallUtil.exe* no prompt de comando com a saída do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="f0695-129">Run *InstallUtil.exe* from the command prompt with your project's output as a parameter:</span></span>

    ```console
    installutil /u <yourproject>.exe
    ```

3. <span data-ttu-id="f0695-130">Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro.</span><span class="sxs-lookup"><span data-stu-id="f0695-130">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="f0695-131">Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.</span><span class="sxs-lookup"><span data-stu-id="f0695-131">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

### <a name="install-your-service-manually-using-powershell"></a><span data-ttu-id="f0695-132">Instalar o serviço manualmente usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0695-132">Install your service manually using PowerShell</span></span>

1. <span data-ttu-id="f0695-133">No menu **Iniciar** , selecione o diretório do **Windows PowerShell** e, em seguida, selecione **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f0695-133">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="f0695-134">Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.</span><span class="sxs-lookup"><span data-stu-id="f0695-134">Access the directory where your project's compiled executable file is located.</span></span>

3. <span data-ttu-id="f0695-135">Execute o cmdlet [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) com o com a saída do seu projeto e um nome de serviço como parâmetros:</span><span class="sxs-lookup"><span data-stu-id="f0695-135">Run the [**New-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet with the with your project's output and a service name as parameters:</span></span>

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a><span data-ttu-id="f0695-136">Desinstalar o serviço manualmente usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0695-136">Uninstall your service manually using PowerShell</span></span>

1. <span data-ttu-id="f0695-137">No menu **Iniciar** , selecione o diretório do **Windows PowerShell** e, em seguida, selecione **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f0695-137">From the **Start** menu, select the **Windows PowerShell** directory, then select **Windows PowerShell**.</span></span>

2. <span data-ttu-id="f0695-138">Execute o cmdlet [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) com o nome do seu serviço como parâmetro:</span><span class="sxs-lookup"><span data-stu-id="f0695-138">Run the [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet with the name of your service as parameter:</span></span>

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. <span data-ttu-id="f0695-139">Depois que o executável de um serviço for excluído, o serviço ainda poderá estar presente no Registro.</span><span class="sxs-lookup"><span data-stu-id="f0695-139">After the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="f0695-140">Nesse caso, use o comando [sc delete](/windows-server/administration/windows-commands/sc-delete) para remover a entrada do serviço do Registro.</span><span class="sxs-lookup"><span data-stu-id="f0695-140">If that's the case, use the command [sc delete](/windows-server/administration/windows-commands/sc-delete) to remove the entry for the service from the registry.</span></span>

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a><span data-ttu-id="f0695-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0695-141">See also</span></span>

- [<span data-ttu-id="f0695-142">Introdução aos aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="f0695-142">Introduction to Windows service applications</span></span>](../windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="f0695-143">Como: criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="f0695-143">How to: Create Windows services</span></span>](../windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="f0695-144">Como: adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="f0695-144">How to: Add installers to your service application</span></span>](../windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="f0695-145">Installutil.exe (ferramenta de instalação)</span><span class="sxs-lookup"><span data-stu-id="f0695-145">Installutil.exe (Installer tool)</span></span>](../tools/installutil-exe-installer-tool.md)
