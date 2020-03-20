---
title: Como utilizar o provedor de função do ASP.NET com um serviço
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184765"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Como utilizar o provedor de função do ASP.NET com um serviço

O provedor de funções ASP.NET (em conjunto com o provedor de membros ASP.NET) é um recurso que permite que os desenvolvedores ASP.NET criem sites da Web que permitam aos usuários criar uma conta com um site e serem atribuídos funções para fins de autorização. Com esse recurso, qualquer usuário pode estabelecer uma conta no site e fazer login para acesso exclusivo ao site e seus serviços. Isso contrasta com a segurança do Windows, que exige que os usuários tenham contas em um domínio do Windows. Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome de usuário/senha) pode usar o site e seus serviços.  
  
Para obter um aplicativo de exemplo, consulte [Adesão e Provedor de Função](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Para obter mais informações sobre o recurso do provedor de membros ASP.NET, consulte [Como: Usar o provedor de adesão ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
O recurso provedor de função usa um banco de dados SQL Server para armazenar informações do usuário. Os desenvolvedores da Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança. Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente WCF. Para permitir que o WCF use o banco <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> de dados, você deve criar uma instância da classe, definir sua <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade para <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, e adicionar a instância à coleção de comportamentos ao <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.  
  
## <a name="configure-the-role-provider"></a>Configure o provedor de função  
  
1. No arquivo Web.config, sob `system.web` o elemento <`roleManager`>, adicione `enabled` um `true`elemento> <e defina seu atributo para .  
  
2. Defina `defaultProvider` o `SqlRoleProvider`atributo para .  
  
3. Quando criança, ao `roleManager` elemento <>, adicione um elemento> <. `providers`  
  
4. Quando criança, ao `providers` elemento `add` <>, adicione um elemento <> `name`com `type` `connectionStringName`os seguintes atributos definidos aos valores apropriados: , , e `applicationName`, como mostrado no exemplo a seguir.  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Configure o serviço para usar o provedor de função  
  
1. No arquivo Web.config, adicione um [ \<elemento system.serviceModel>.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) um elemento de>`system.ServiceModel` de comportamentos ao elemento <>.  
  
3. Adicione um [ \<serviçoComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` ao elemento <>.  
  
4. Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) um comportamento>`name` elemento e defina o atributo como um valor apropriado.  
  
5. Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) um>de `behavior` autorização de serviço ao elemento <>.  
  
6. Defina `principalPermissionMode` o `UseAspNetRoles`atributo para .  
  
7. Defina `roleProviderName` o `SqlRoleProvider`atributo para . O exemplo a seguir mostra um fragmento da configuração.  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a>Confira também

- [Provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Como utilizar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
