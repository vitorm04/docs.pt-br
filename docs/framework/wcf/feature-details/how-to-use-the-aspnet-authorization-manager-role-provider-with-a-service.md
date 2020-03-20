---
title: Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184805"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="c3df5-102">Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="c3df5-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="c3df5-103">Quando ASP.NET hospeda um serviço Web, você pode integrar o Authorization Manager ao aplicativo para fornecer autorização ao serviço.</span><span class="sxs-lookup"><span data-stu-id="c3df5-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="c3df5-104">O Authorization Manager permite que um desenvolvedor de aplicativos defina operações individuais, que podem ser agrupadas para formar tarefas.</span><span class="sxs-lookup"><span data-stu-id="c3df5-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="c3df5-105">Um administrador pode então autorizar funções para executar tarefas específicas ou operações individuais.</span><span class="sxs-lookup"><span data-stu-id="c3df5-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="c3df5-106">O Authorization Manager fornece uma ferramenta de administração como um snap-in do Microsoft Management Console (MMC) para gerenciar funções, tarefas, operações e usuários.</span><span class="sxs-lookup"><span data-stu-id="c3df5-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="c3df5-107">Os administradores configuram uma loja de diretiva do Gerenciador de Autorização em um arquivo XML, Active Directory ou em uma loja ADAM (Active Directory Application Mode, modo de aplicação do diretório ativo).</span><span class="sxs-lookup"><span data-stu-id="c3df5-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="c3df5-108">O Gerenciador de Autorização é integrado ao aplicativo configurando o Gerenciador de ASP.NET papel do provedor de ASP.NET que está hospedando o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="c3df5-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="c3df5-109">Como outros provedores de ASP.NET, o provedor de `providers` ASP.NET de ASP.NET de autorização é configurado usando o elemento> <.</span><span class="sxs-lookup"><span data-stu-id="c3df5-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="c3df5-110">O exemplo de código a seguir é uma parte de um arquivo de configuração de um serviço Web que está integrando o Authorization Manager ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3df5-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="c3df5-111">Para obter mais informações sobre como integrar um provedor de função ASP.NET com um aplicativo WCF, consulte [Como: Usar o provedor de função ASP.NET com um serviço.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)</span><span class="sxs-lookup"><span data-stu-id="c3df5-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="c3df5-112">Para obter mais informações sobre como usar o Authorization Manager com ASP.NET, consulte [Como: Gerente de Autorização de Uso (AzMan) com ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="c3df5-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3df5-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3df5-113">See also</span></span>

- [<span data-ttu-id="c3df5-114">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="c3df5-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
