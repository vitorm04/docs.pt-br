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
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Como: usar o provedor de função do gerenciador de autorização ASP.NET com um serviço
Quando o ASP.NET hospeda um serviço Web, você pode integrar o Gerenciador de autorização no aplicativo para fornecer autorização para o serviço. O Gerenciador de autorização permite que um desenvolvedor de aplicativos definir as operações específicas, que podem ser agrupadas para tarefas de formulário. Um administrador pode, em seguida, autorizar funções para executar tarefas específicas ou operações individuais. Gerenciador de autorização oferece uma ferramenta de administração como um snap-in do Console de gerenciamento Microsoft (MMC) para gerenciar usuários, tarefas, operações e funções. Os administradores configurar um repositório de políticas do Gerenciador de autorização em um arquivo XML, o Active Directory, ou em um repositório de aplicativo modo ADAM (Active Directory).  
  
 O Gerenciador de autorização é integrado ao aplicativo, configurando o provedor de função do Gerenciador de autorização do ASP.NET para o aplicativo ASP.NET que está hospedando o serviço Web. Como outros provedores de função do ASP.NET, o provedor de função do Gerenciador de autorização do ASP.NET é configurado usando o <`providers`> elemento.  
  
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
  
 Para obter mais informações sobre como integrar um provedor de função ASP.NET com um aplicativo WCF, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Para obter mais informações sobre como usar o Gerenciador de autorização com o ASP.NET, consulte [como: Usar Gerenciador de autorização (AzMan) com o ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Consulte também

- [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
