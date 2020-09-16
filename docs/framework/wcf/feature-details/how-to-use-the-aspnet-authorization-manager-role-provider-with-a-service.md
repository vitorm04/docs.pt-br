---
title: 'Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 4a92c9db000b703f4fdab7c34e5359de74b0228d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545598"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="cfd24-102">Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="cfd24-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="cfd24-103">Quando o ASP.NET hospeda um serviço Web, você pode integrar o Gerenciador de autorização ao aplicativo para fornecer autorização ao serviço.</span><span class="sxs-lookup"><span data-stu-id="cfd24-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="cfd24-104">O Gerenciador de autorização permite que um desenvolvedor de aplicativo defina operações individuais, que podem ser agrupadas para tarefas de formulário.</span><span class="sxs-lookup"><span data-stu-id="cfd24-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="cfd24-105">Um administrador pode então autorizar funções para executar tarefas específicas ou operações individuais.</span><span class="sxs-lookup"><span data-stu-id="cfd24-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="cfd24-106">O Gerenciador de autorização fornece uma ferramenta de administração como um snap-in do MMC (console de gerenciamento Microsoft) para gerenciar funções, tarefas, operações e usuários.</span><span class="sxs-lookup"><span data-stu-id="cfd24-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="cfd24-107">Os administradores configuram um repositório de políticas do Gerenciador de autorização em um arquivo XML, Active Directory ou em um repositório do ADAM (Active Directory Application Mode).</span><span class="sxs-lookup"><span data-stu-id="cfd24-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="cfd24-108">O Gerenciador de autorização é integrado ao aplicativo Configurando o provedor de função ASP.NET do Gerenciador de autorização para o aplicativo ASP.NET que está hospedando o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="cfd24-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="cfd24-109">Assim como outros provedores de função ASP.NET, o provedor de função ASP.NET do Gerenciador de autorização é configurado usando o `providers` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="cfd24-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="cfd24-110">O exemplo de código a seguir é uma parte de um arquivo de configuração para um serviço Web que está integrando o Gerenciador de autorização no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd24-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="cfd24-111">Para obter mais informações sobre como integrar um provedor de função ASP.NET a um aplicativo WCF, consulte [como: usar o provedor de função ASP.NET com um serviço](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="cfd24-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="cfd24-112">Para obter mais informações sobre como usar o Gerenciador de autorização com ASP.NET, consulte [como: usar o Gerenciador de autorização (AzMan) com o ASP.NET 2,0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="cfd24-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd24-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfd24-113">See also</span></span>

- [<span data-ttu-id="cfd24-114">Como: usar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="cfd24-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
