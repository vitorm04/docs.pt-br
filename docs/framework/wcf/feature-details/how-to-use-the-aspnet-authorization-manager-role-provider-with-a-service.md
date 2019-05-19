---
title: 'Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880196"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="7ea14-102">Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="7ea14-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="7ea14-103">Quando o ASP.NET hospeda um serviço Web, você pode integrar o Gerenciador de autorização no aplicativo para fornecer autorização para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7ea14-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="7ea14-104">O Gerenciador de autorização permite que um desenvolvedor de aplicativos definir as operações específicas, que podem ser agrupadas para tarefas de formulário.</span><span class="sxs-lookup"><span data-stu-id="7ea14-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="7ea14-105">Um administrador pode, em seguida, autorizar funções para executar tarefas específicas ou operações individuais.</span><span class="sxs-lookup"><span data-stu-id="7ea14-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="7ea14-106">Gerenciador de autorização oferece uma ferramenta de administração como um snap-in do Console de gerenciamento Microsoft (MMC) para gerenciar usuários, tarefas, operações e funções.</span><span class="sxs-lookup"><span data-stu-id="7ea14-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="7ea14-107">Os administradores configurar um repositório de políticas do Gerenciador de autorização em um arquivo XML, o Active Directory, ou em um repositório de aplicativo modo ADAM (Active Directory).</span><span class="sxs-lookup"><span data-stu-id="7ea14-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="7ea14-108">O Gerenciador de autorização é integrado ao aplicativo, configurando o provedor de função do Gerenciador de autorização do ASP.NET para o aplicativo ASP.NET que está hospedando o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="7ea14-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="7ea14-109">Como outros provedores de função do ASP.NET, o provedor de função do Gerenciador de autorização do ASP.NET é configurado usando o <`providers`> elemento.</span><span class="sxs-lookup"><span data-stu-id="7ea14-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="7ea14-110">O exemplo de código a seguir é uma parte de um arquivo de configuração para um serviço Web que é a integração do Gerenciador de autorização no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ea14-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="7ea14-111">Para obter mais informações sobre como integrar um provedor de função ASP.NET com um aplicativo WCF, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="7ea14-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="7ea14-112">Para obter mais informações sobre como usar o Gerenciador de autorização com o ASP.NET, consulte [como: Usar Gerenciador de autorização (AzMan) com o ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="7ea14-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea14-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ea14-113">See also</span></span>

- [<span data-ttu-id="7ea14-114">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="7ea14-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
