---
title: "Como instalar e desinstalar serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 1fcbc8e7a84b16d244561e0cd69f8661236e63de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="12619-102">Como instalar e desinstalar serviços</span><span class="sxs-lookup"><span data-stu-id="12619-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="12619-103">Se você estiver desenvolvendo um serviço Windows usando o .NET Framework, você pode rapidamente instalar seu aplicativo de serviço usando um utilitário de linha de comando chamado InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="12619-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="12619-104">Se você for um desenvolvedor que deseja liberar um serviço Windows que os usuários possam instalar e desinstalar, você deve usar o InstallShield.</span><span class="sxs-lookup"><span data-stu-id="12619-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="12619-105">Consulte [implantação do Windows Installer](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span><span class="sxs-lookup"><span data-stu-id="12619-105">See [Windows Installer Deployment](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="12619-106">Se você deseja desinstalar um serviço do seu computador, não execute as etapas neste artigo.</span><span class="sxs-lookup"><span data-stu-id="12619-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="12619-107">Em vez disso, descubra qual pacote de software ou programa instalado o serviço e, em seguida, escolha **adicionar ou remover programas** no painel de controle para desinstalar o programa.</span><span class="sxs-lookup"><span data-stu-id="12619-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="12619-108">Observe que muitos serviços são partes integrais do Windows, se você removê-los, poderá causar instabilidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="12619-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="12619-109">Para usar as etapas neste artigo, primeiro é necessário adicionar um instalador de serviço para o serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="12619-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="12619-110">Consulte [passo a passo: Criando uma janela de aplicativo no Designer de componente de serviço](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="12619-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="12619-111">Projetos de serviço Windows não podem ser executados diretamente do ambiente de desenvolvimento do Visual Studio pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="12619-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="12619-112">Isso ocorre porque o serviço no projeto deve ser instalado antes de executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="12619-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="12619-113">Você pode iniciar **Server Explorer** e verifique se o serviço foi instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="12619-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="12619-114">Para obter mais informações, consulte como: acesso e inicializar o Gerenciador de banco de dados do Gerenciador de servidores.</span><span class="sxs-lookup"><span data-stu-id="12619-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="12619-115">Para instalar o serviço manualmente</span><span class="sxs-lookup"><span data-stu-id="12619-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="12619-116">No Windows **iniciar** menu ou **iniciar** tela, escolha **Visual Studio** , **ferramentas do Visual Studio**, **Developer Prompt de comando**.</span><span class="sxs-lookup"><span data-stu-id="12619-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="12619-117">É exibido um prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12619-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="12619-118">Acesse o diretório onde o arquivo executável compilado do seu projeto está localizado.</span><span class="sxs-lookup"><span data-stu-id="12619-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="12619-119">Execute o InstallUtil.exe no prompt de comando com o executável do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="12619-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="12619-120">Se você estiver usando o prompt de comando do Visual Studio, o InstallUtil.exe deve estar no caminho do sistema.</span><span class="sxs-lookup"><span data-stu-id="12619-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="12619-121">Caso contrário, você pode adicioná-lo ao caminho ou usar o caminho totalmente qualificado para invocá-lo.</span><span class="sxs-lookup"><span data-stu-id="12619-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="12619-122">Essa ferramenta é instalada com o .NET Framework e o caminho é `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span><span class="sxs-lookup"><span data-stu-id="12619-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="12619-123">Por exemplo, para a versão de 32 bits do .NET Framework 4 ou 4.5.\*, se o diretório de instalação do Windows for C:\Windows, o caminho é `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="12619-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="12619-124">Para a versão de 64 bits do .NET Framework 4 ou 4.5. \*, o caminho padrão é `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="12619-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="12619-125">Para desinstalar o serviço manualmente</span><span class="sxs-lookup"><span data-stu-id="12619-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="12619-126">No Windows **iniciar** menu ou **iniciar** tela, escolha **Visual Studio**, **ferramentas do Visual Studio**, **Developer Prompt de comando**.</span><span class="sxs-lookup"><span data-stu-id="12619-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="12619-127">É exibido um prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12619-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="12619-128">Execute o InstallUtil.exe no prompt de comando com a saída do projeto como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="12619-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="12619-129">Às vezes, depois que o executável de um serviço é excluído, o serviço ainda pode estar presente no registro.</span><span class="sxs-lookup"><span data-stu-id="12619-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="12619-130">Nesse caso, use o comando [sc delete](http://technet.microsoft.com/library/cc742045.aspx) para remover a entrada para o serviço de registro.</span><span class="sxs-lookup"><span data-stu-id="12619-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12619-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12619-131">See Also</span></span>  
 [<span data-ttu-id="12619-132">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="12619-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="12619-133">Como criar Serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="12619-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="12619-134">Como adicionar instaladores no seu aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="12619-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="12619-135">Installutil.exe (Ferramenta de Instalação)</span><span class="sxs-lookup"><span data-stu-id="12619-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
