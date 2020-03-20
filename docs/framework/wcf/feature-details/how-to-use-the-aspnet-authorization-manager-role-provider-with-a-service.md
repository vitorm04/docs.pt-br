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
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Como usar o provedor de função do gerenciador de autorização ASP.NET com um serviço
Quando ASP.NET hospeda um serviço Web, você pode integrar o Authorization Manager ao aplicativo para fornecer autorização ao serviço. O Authorization Manager permite que um desenvolvedor de aplicativos defina operações individuais, que podem ser agrupadas para formar tarefas. Um administrador pode então autorizar funções para executar tarefas específicas ou operações individuais. O Authorization Manager fornece uma ferramenta de administração como um snap-in do Microsoft Management Console (MMC) para gerenciar funções, tarefas, operações e usuários. Os administradores configuram uma loja de diretiva do Gerenciador de Autorização em um arquivo XML, Active Directory ou em uma loja ADAM (Active Directory Application Mode, modo de aplicação do diretório ativo).  
  
 O Gerenciador de Autorização é integrado ao aplicativo configurando o Gerenciador de ASP.NET papel do provedor de ASP.NET que está hospedando o serviço Web. Como outros provedores de ASP.NET, o provedor de `providers` ASP.NET de ASP.NET de autorização é configurado usando o elemento> <.  
  
 O exemplo de código a seguir é uma parte de um arquivo de configuração de um serviço Web que está integrando o Authorization Manager ao aplicativo.  
  
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
  
 Para obter mais informações sobre como integrar um provedor de função ASP.NET com um aplicativo WCF, consulte [Como: Usar o provedor de função ASP.NET com um serviço.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md) Para obter mais informações sobre como usar o Authorization Manager com ASP.NET, consulte [Como: Gerente de Autorização de Uso (AzMan) com ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Confira também

- [Como utilizar o provedor de função do ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
