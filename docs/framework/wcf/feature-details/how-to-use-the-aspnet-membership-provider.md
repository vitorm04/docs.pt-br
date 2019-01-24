---
title: 'Como: Usar o provedor de associação do ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 4653a4b4ae90f391eac559210deb611e2a83d0f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634500"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Como: Usar o provedor de associação do ASP.NET
O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permitem aos usuários criar combinações de nome e senha de usuário exclusivo. Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e entrar para acesso exclusivo para o site e seus serviços. Isso é diferente de segurança do Windows, o que exige que os usuários têm contas em um domínio do Windows. Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome/senha de usuário) pode usar o site e seus serviços.  
  
 Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Para obter informações sobre como usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de provedor de função, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 O recurso de associação requer o uso de um banco de dados do SQL Server para armazenar as informações do usuário. O recurso também inclui métodos para avisar com uma pergunta quaisquer usuários que tenham esquecido sua senha.  
  
 Os desenvolvedores do Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança. Quando integrado a um aplicativo do WCF, os usuários devem fornecer uma combinação de nome/senha de usuário para o aplicativo de cliente do WCF. Para transferir os dados para o serviço WCF, usar uma associação que dá suporte a credenciais de nome/senha do usuário, como o <xref:System.ServiceModel.WSHttpBinding> (na configuração, o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e definir o tipo de credencial para `UserName`. No serviço de segurança do WCF autentica o usuário com base no nome de usuário e senha e também atribui a função especificada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] função.  
  
> [!NOTE]
>  O WCF não fornece métodos para preencher o banco de dados com combinações de nome/senha de usuário ou outras informações do usuário.  
  
### <a name="to-configure-the-membership-provider"></a>Para configurar o provedor de associação  
  
1.  No arquivo Web. config, sob o <`system.web`> elemento, crie um <`membership`> elemento.  
  
2.  Sob o `<membership>` elemento, criar um `<providers>` elemento.  
  
3.  Como um filho para o <`providers`> elemento, adicionar um `<clear />` elemento para a coleção de provedores de liberação.  
  
4.  Sob o `<clear />` elemento, crie um <`add`> elemento com os seguintes atributos definidos com valores apropriados: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, e `passwordFormat`. O `name` atributo é usado posteriormente como um valor no arquivo de configuração. O exemplo a seguir define como `SqlMembershipProvider`.  
  
     O exemplo a seguir mostra a seção de configuração.  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Para configurar a segurança de serviço para aceitar a combinação de nome/senha do usuário  
  
1.  No arquivo de configuração, sob o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.  
  
2.  Adicionar um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à seção de associações. Para obter mais informações sobre a criação de um elemento de associação do WCF, consulte [como: Especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Defina o atributo `mode` do elemento `<security>` como `Message`.  
  
4.  Defina as `clientCredentialType` atributo da <`message`> elemento a ser `UserName`. Isso especifica que um par de nome/senha do usuário será usado como credencial do cliente.  
  
     O exemplo a seguir mostra o código de configuração para a associação.  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Para configurar um serviço para usar o provedor de associação  
  
1.  Como um filho para o `<system.serviceModel>` elemento, adicione uma [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento  
  
2.  Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.  
  
3.  Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` de atributo para um valor apropriado.  
  
4.  Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o <`behavior`> elemento.  
  
5.  Adicionar um [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) para o `<serviceCredentials>` elemento.  
  
6.  Defina as `userNamePasswordValidationMode` atributo `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Se o `userNamePasswordValidationMode` valor não for definido, o WCF usa a autenticação do Windows em vez do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação.  
  
7.  Defina o `membershipProviderName` de atributo para o nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico). O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra a configuração para um serviço que usa o recurso de associação do ASP.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
