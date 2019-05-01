---
title: 'Como: usar o provedor de função do ASP.NET com um serviço'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 8f3fadc60645ef81d2683c63fda0ddd5bf24c982
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047237"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Como: usar o provedor de função do ASP.NET com um serviço
O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função (em conjunto com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação) é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permitem aos usuários criar uma conta com um site e a serem atribuídos a funções para autorização finalidades. Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e faça logon no acesso exclusivo para o site e seus serviços. Isso é diferente de segurança do Windows, o que exige que os usuários têm contas em um domínio do Windows. Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome/senha de usuário) pode usar o site e seus serviços.  
  
 Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Para obter mais informações sobre o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de provedor de associação, consulte [como: Usar o provedor de associação ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 O recurso de provedor de função usa um banco de dados do SQL Server para armazenar informações do usuário. Os desenvolvedores do Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança. Quando integrado em um aplicativo WCF, os usuários devem fornecer uma combinação de nome/senha de usuário para o aplicativo de cliente do WCF. Para habilitar o WCF para usar o banco de dados, você deve criar uma instância da <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, defina sua <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade a ser <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>e adicione a instância para a coleção de comportamentos para o <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.  
  
### <a name="to-configure-the-role-provider"></a>Para configurar o provedor de função  
  
1. No arquivo Web. config, sob o <`system.web`> elemento, adicionar um <`roleManager`> elemento e defina seu `enabled` de atributo para `true`.  
  
2. Defina as `defaultProvider` atributo `SqlRoleProvider`.  
  
3. Como um filho para o <`roleManager`> elemento, adicione um <`providers`> elemento.  
  
4. Como um filho para o <`providers`> elemento, adicione um <`add`> elemento com os seguintes atributos definidos com valores apropriados: `name`, `type`, `connectionStringName`, e `applicationName`, conforme mostrado no exemplo a seguir.  
  
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
  
1. No arquivo Web. config, adicione uma [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento.  
  
2. Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o <`system.ServiceModel`> elemento.  
  
3. Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.  
  
4. Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento e defina o `name` de atributo para um valor apropriado.  
  
5. Adicionar um [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para o <`behavior`> elemento.  
  
6. Defina as `principalPermissionMode` atributo `UseAspNetRoles`.  
  
7. Defina as `roleProviderName` atributo `SqlRoleProvider`. O exemplo a seguir mostra um fragmento da configuração.  
  
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

- [Provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Como: Usar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
