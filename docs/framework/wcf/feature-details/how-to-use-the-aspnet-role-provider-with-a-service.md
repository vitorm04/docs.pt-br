---
title: "Como utilizar o provedor de função do ASP.NET com um serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bdddbd39a528e6abd6a0268db310b6173849f19b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Como utilizar o provedor de função do ASP.NET com um serviço
O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função (em conjunto com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação) é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permite que os usuários criem uma conta com um site e para serem atribuídos a funções de autorização finalidades. Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e faça logon para o acesso exclusivo para o site e seus serviços. Isso é diferente de segurança do Windows, que exige que os usuários possuem contas em um domínio do Windows. Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome e senha de usuário) pode usar o site e seus serviços.  
  
 Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de provedor de associação, consulte [como: usar o provedor de associação ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 O recurso de provedor de função usa um banco de dados do SQL Server para armazenar informações do usuário. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]os desenvolvedores podem aproveitar esses recursos para fins de segurança. Quando integrado a um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, os usuários devem fornecer uma combinação de nome e senha de usuário para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente. Para habilitar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para usar o banco de dados, você deve criar uma instância do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, defina seu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>e adicionar a instância para a coleção de comportamentos para o <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.  
  
### <a name="to-configure-the-role-provider"></a>Para configurar o provedor de função  
  
1.  No arquivo Web. config, sob o <`system.web`> elemento, adicionar um <`roleManager`> elemento e defina seu `enabled` atributo `true`.  
  
2.  Definir o `defaultProvider` atributo `SqlRoleProvider`.  
  
3.  Como um filho de <`roleManager`> elemento, adicionar um <`providers`> elemento.  
  
4.  Como um filho de <`providers`> elemento, adicionar um <`add`> elemento com os seguintes atributos definido para os valores apropriados: `name`, `type`, `connectionStringName`, e `applicationName`, conforme mostrado no exemplo a seguir.  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>Para configurar o serviço para usar o provedor de função  
  
1.  No arquivo Web. config, adicione um [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento.  
  
2.  Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o <`system.ServiceModel`> elemento.  
  
3.  Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.  
  
4.  Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento e defina o `name` de atributo para um valor apropriado.  
  
5.  Adicionar um [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para o <`behavior`> elemento.  
  
6.  Definir o `principalPermissionMode` atributo `UseAspNetRoles`.  
  
7.  Definir o `roleProviderName` atributo `SqlRoleProvider`. O exemplo a seguir mostra um fragmento da configuração.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [Como: usar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
