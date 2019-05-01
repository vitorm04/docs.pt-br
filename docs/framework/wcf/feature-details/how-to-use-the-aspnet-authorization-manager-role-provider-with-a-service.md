---
title: 'Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: ebdfa8bd7d222c4f9a33b6718b215d327d589c6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047289"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço
Quando [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hospeda um serviço Web, você pode integrar o Gerenciador de autorização no aplicativo para fornecer autorização para o serviço. O Gerenciador de autorização permite que um desenvolvedor de aplicativos definir as operações específicas, que podem ser agrupadas para tarefas de formulário. Um administrador pode, em seguida, autorizar funções para executar tarefas específicas ou operações individuais. Gerenciador de autorização oferece uma ferramenta de administração como um snap-in do Console de gerenciamento Microsoft (MMC) para gerenciar usuários, tarefas, operações e funções. Os administradores configurar um repositório de políticas do Gerenciador de autorização em um arquivo XML, o Active Directory, ou em um repositório de aplicativo modo ADAM (Active Directory).  
  
 O Gerenciador de autorização é integrado ao aplicativo, configurando o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo que está hospedando o serviço Web. Como qualquer outro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedores de função, o Gerenciador de autorização [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função é configurado usando o <`providers`> elemento.  
  
 O exemplo de código a seguir é uma parte de um arquivo de configuração para um serviço Web que é a integração do Gerenciador de autorização no aplicativo.  
  
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
  
 Para obter mais informações sobre como integrar um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função com um aplicativo WCF, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Para obter mais informações sobre como usar o Gerenciador de autorização com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consulte [como: Usar Gerenciador de autorização (AzMan) com o ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Consulte também

- [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
