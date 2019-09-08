---
title: Configurando seu aplicativo
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 4e19e4d0ecb6bc90402f99dddd280ee1dbcf7ea0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798157"
---
# <a name="configuring-your-application"></a><span data-ttu-id="0bbf8-102">Configurando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0bbf8-102">Configuring Your Application</span></span>
<span data-ttu-id="0bbf8-103">O Windows Communication Foundation (WCF) usa o sistema de configuração do .NET e permite que você configure serviços no escopo do computador e do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="0bbf8-104">As definições de configuração definidas pelo WCF estão localizadas no grupo de `<system.serviceModel>` seções.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="0bbf8-105">Para obter mais informações sobre como configurar um serviço WCF, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="0bbf8-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="0bbf8-106">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="0bbf8-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [<span data-ttu-id="0bbf8-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0bbf8-107">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="0bbf8-108">As definições de configurações definidas pelo aplicativo são definidas `<appSettings>` no grupo de seções.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="0bbf8-109">Para obter mais informações sobre configurações de aplicativo em arquivos de configuração do .net, consulte [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="0bbf8-109">For more information about application settings in .NET configuration files, see [\<appSettings>](https://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="0bbf8-110">Usando o editor de configuração</span><span class="sxs-lookup"><span data-stu-id="0bbf8-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="0bbf8-111">A [ferramenta Editor de configuração do WCF (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) permite que administradores e desenvolvedores criem e modifiquem definições de configuração para serviços WCF usando uma interface gráfica do usuário.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="0bbf8-112">Com essa ferramenta, você pode gerenciar configurações para associações, comportamentos, serviços e diagnósticos do WCF sem editar diretamente os arquivos de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="0bbf8-113">Editando arquivos de configuração no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0bbf8-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="0bbf8-114">Para editar o arquivo de configuração de um projeto de serviço WCF no Visual Studio, clique com o botão direito do mouse no **Gerenciador de soluções** e escolha o item de menu editar o contexto de **configuração do WCF** .</span><span class="sxs-lookup"><span data-stu-id="0bbf8-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="0bbf8-115">Isso inicia a [ferramenta do editor de configuração (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0bbf8-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bbf8-116">Se você editar o arquivo de configuração de um projeto de serviço Web WCF no Visual Studio, clicando com o botão direito do mouse no **Gerenciador de soluções**, observe que o item de menu Editar contexto de **configuração do WCF** está ausente.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="0bbf8-117">Para solucionar esse problema, clique no menu **ferramentas** e escolha **Editor de configuração do serviço WCF**.</span><span class="sxs-lookup"><span data-stu-id="0bbf8-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="0bbf8-118">Depois disso, você pode clicar com o botão direito do mouse em um arquivo de configuração e usar o item de menu de contexto **Editar configuração do WCF** .</span><span class="sxs-lookup"><span data-stu-id="0bbf8-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbf8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bbf8-119">See also</span></span>

- [<span data-ttu-id="0bbf8-120">Ferramenta Editor de configuração (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="0bbf8-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="0bbf8-121">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="0bbf8-121">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="0bbf8-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0bbf8-122">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
