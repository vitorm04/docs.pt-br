---
title: Configurando seu aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a><span data-ttu-id="b16db-102">Configurando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="b16db-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="b16db-103">usa o sistema de configuração do .NET e permite que você configure serviços no escopo máquina e do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b16db-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="b16db-104">Configurações definidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] estão localizados no `<system.serviceModel>` grupo da seção.</span><span class="sxs-lookup"><span data-stu-id="b16db-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b16db-105">como configurar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="b16db-105"> how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   <span data-ttu-id="b16db-106">[Configuring Services](../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)</span><span class="sxs-lookup"><span data-stu-id="b16db-106">[Configuring Services](../../../../docs/framework/wcf/configuring-services.md)</span></span>  
  
-   [<span data-ttu-id="b16db-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b16db-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="b16db-108">As definições de configuração definido pelo aplicativo estão definidas no `<appSettings>` grupo da seção.</span><span class="sxs-lookup"><span data-stu-id="b16db-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b16db-109">configurações do aplicativo em arquivos de configuração do .NET, consulte [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="b16db-109"> application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="b16db-110">Usando o Editor de configuração</span><span class="sxs-lookup"><span data-stu-id="b16db-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="b16db-111">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) permite que os administradores e desenvolvedores criar e modificar definições de configuração para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços usando a interface gráfica do usuário.</span><span class="sxs-lookup"><span data-stu-id="b16db-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="b16db-112">Com essa ferramenta, você pode gerenciar configurações para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações, comportamentos, serviços e diagnósticos sem editar diretamente os arquivos de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="b16db-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="b16db-113">Editando arquivos de configuração no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b16db-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="b16db-114">Para editar o arquivo de configuração de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de serviço no [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], clique com botão direito no **Solution Explorer** e escolha o **Editar configuração do WCF** item de menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="b16db-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="b16db-115">Isso inicia o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b16db-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b16db-116">Se você editar o arquivo de configuração de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projeto de serviço da Web em [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] clicando no **Solution Explorer**, observe que o **Editar configuração do WCF** item de menu de contexto está ausente .</span><span class="sxs-lookup"><span data-stu-id="b16db-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="b16db-117">Para solucionar esse problema, clique no **ferramentas** menu e escolha **Editor de configuração de serviço do WCF**.</span><span class="sxs-lookup"><span data-stu-id="b16db-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="b16db-118">Depois disso, selecione o arquivo de configuração e use o **Editar configuração do WCF** item de menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="b16db-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16db-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b16db-119">See Also</span></span>  
 <span data-ttu-id="b16db-120">[Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) (Ferramenta Editor de configuração (SvcConfigEditor.exe))</span><span class="sxs-lookup"><span data-stu-id="b16db-120">[Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)</span></span>  
 <span data-ttu-id="b16db-121">[Configuring Services](../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)</span><span class="sxs-lookup"><span data-stu-id="b16db-121">[Configuring Services](../../../../docs/framework/wcf/configuring-services.md)</span></span>  
 [<span data-ttu-id="b16db-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b16db-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
