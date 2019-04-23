---
title: 'Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: ebdfa8bd7d222c4f9a33b6718b215d327d589c6d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073566"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="dd0bb-102">Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="dd0bb-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="dd0bb-103">Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um serviço Web, você pode integrar o Gerenciador de autorização no aplicativo para fornecer autorização para o serviço.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="dd0bb-104">O Gerenciador de autorização permite que um desenvolvedor de aplicativos definir as operações específicas, que podem ser agrupadas para tarefas de formulário.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="dd0bb-105">Um administrador pode, em seguida, autorizar funções para executar tarefas específicas ou operações individuais.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="dd0bb-106">Gerenciador de autorização oferece uma ferramenta de administração como um snap-in do Console de gerenciamento Microsoft (MMC) para gerenciar usuários, tarefas, operações e funções.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="dd0bb-107">Os administradores configurar um repositório de políticas do Gerenciador de autorização em um arquivo XML, o Active Directory, ou em um repositório de aplicativo modo ADAM (Active Directory).</span><span class="sxs-lookup"><span data-stu-id="dd0bb-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="dd0bb-108">O Gerenciador de autorização é integrado ao aplicativo, configurando o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo que está hospedando o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="dd0bb-109">Como qualquer outro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedores de função, o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função é configurado usando o <`providers`> elemento.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="dd0bb-110">O exemplo de código a seguir é uma parte de um arquivo de configuração para um serviço Web que é a integração do Gerenciador de autorização no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd0bb-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="dd0bb-111">Para obter mais informações sobre como integrar um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função com um aplicativo WCF, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="dd0bb-111">For more information about integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="dd0bb-112">Para obter mais informações sobre como usar o Gerenciador de autorização com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [como: Usar Gerenciador de autorização (AzMan) com o ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="dd0bb-112">For more information about using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0bb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd0bb-113">See also</span></span>

- [<span data-ttu-id="dd0bb-114">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="dd0bb-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
