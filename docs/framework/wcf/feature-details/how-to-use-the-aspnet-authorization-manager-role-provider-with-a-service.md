---
title: "Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88fc7658af3d82a21931b697e3a66a15b32be16b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="e6eab-102">Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="e6eab-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="e6eab-103">Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um serviço Web, você pode integrar o Gerenciador de autorização do aplicativo para fornecer autorização para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e6eab-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="e6eab-104">Gerenciador de autorização permite que um desenvolvedor de aplicativos definir as operações individuais, que podem ser agrupadas para tarefas de formulário.</span><span class="sxs-lookup"><span data-stu-id="e6eab-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="e6eab-105">Um administrador pode, então, autorizar funções para executar tarefas específicas ou operações individuais.</span><span class="sxs-lookup"><span data-stu-id="e6eab-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="e6eab-106">Gerenciador de autorização oferece uma ferramenta de administração como um snap-in do Console de gerenciamento Microsoft (MMC) para gerenciar usuários, tarefas, operações e funções.</span><span class="sxs-lookup"><span data-stu-id="e6eab-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="e6eab-107">Os administradores configurar um repositório de política do Gerenciador de autorização em um arquivo XML, o Active Directory, ou em um armazenamento de modo de aplicativo do Active Directory (ADAM).</span><span class="sxs-lookup"><span data-stu-id="e6eab-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="e6eab-108">O Gerenciador de autorização é integrado no aplicativo configurando o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função para a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo que está hospedando o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="e6eab-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="e6eab-109">Assim como outros [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedores de função, o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função é configurado usando o <`providers`> elemento.</span><span class="sxs-lookup"><span data-stu-id="e6eab-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="e6eab-110">O exemplo de código a seguir é uma parte de um arquivo de configuração para um serviço Web que integra o Gerenciador de autorização para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6eab-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e6eab-111">Integrando um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, consulte [como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="e6eab-111"> integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e6eab-112">usando o Gerenciador de autorização com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [como: Use o Gerenciador de autorização (AzMan) com o ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="e6eab-112"> using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6eab-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6eab-113">See Also</span></span>  
 [<span data-ttu-id="e6eab-114">Como: usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="e6eab-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
