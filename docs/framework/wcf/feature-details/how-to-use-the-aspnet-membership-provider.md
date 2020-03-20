---
title: Como utilizar o provedor de associação do ASP.NET
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184789"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Como utilizar o provedor de associação do ASP.NET

O provedor de assinatura ASP.NET é um recurso que permite que ASP.NET desenvolvedores criem sites da Web que permitem que os usuários criem combinações exclusivas de nome de usuário e senha. Com esta facilidade, qualquer usuário pode estabelecer uma conta no site, e fazer login para acesso exclusivo ao site e seus serviços. Isso contrasta com a segurança do Windows, que exige que os usuários tenham contas em um domínio do Windows. Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome de usuário/senha) pode usar o site e seus serviços.

Para obter um aplicativo de exemplo, consulte [Adesão e Provedor de Função](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Para obter informações sobre como usar o recurso do provedor de ASP.NET função, consulte [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).

O recurso de associação requer o uso de um banco de dados do SQL Server para armazenar as informações do usuário. O recurso também inclui métodos para solicitar com uma pergunta qualquer usuário que tenha esquecido sua senha.

Os desenvolvedores da Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança. Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente WCF. Para transferir os dados para o serviço WCF, use uma vinculação <xref:System.ServiceModel.WSHttpBinding> que suporte credenciais de nome de usuário/senha, como `UserName`o (na configuração, o [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e defina o tipo de credencial do cliente para . No serviço, a segurança do WCF autentica o usuário com base no nome de usuário e senha, e também atribui a função especificada pela função ASP.NET.

> [!NOTE]
> O WCF não fornece métodos para preencher o banco de dados com combinações de nome de usuário/senha ou outras informações do usuário.

### <a name="to-configure-the-membership-provider"></a>Para configurar o provedor de membros

1. No arquivo Web.config, sob `system.web` o elemento <`membership`>, crie um elemento> <.

2. `<membership>` o elemento, `<providers>` crie um elemento.

3. Quando criança, para `providers` o <`<clear />`> elemento, adicione um elemento para lavar a coleção de provedores.

4. `<clear />` o elemento, `add` crie um elemento <> com `name`os `type` `connectionStringName`seguintes atributos `passwordFormat`definidos para valores apropriados:,, , `applicationName` `enablePasswordRetrieval`, `enablePasswordReset`, , `requiresQuestionAndAnswer`, e `requiresUniqueEmail`. O `name` atributo é usado mais tarde como um valor no arquivo de configuração. O exemplo a `SqlMembershipProvider`seguir define-o para .

    O exemplo a seguir mostra a seção configuração.

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Para configurar a segurança do serviço para aceitar a combinação de nome de usuário/senha

1. No arquivo de configuração, o [ \<elemento system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) adicione um [ \<elemento de>de vinculações.](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. Adicione um [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à seção de vinculações. Para obter mais informações sobre a criação de um elemento de vinculação do WCF, consulte [Como: Especificar uma vinculação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

3. Defina o atributo `mode` do elemento `<security>` como `Message`.

4. Defina `clientCredentialType` o atributo do elemento> <`message` para `UserName`. Isso especifica que um par de nome de usuário/senha será usado como credencial do cliente.

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Para configurar um serviço para usar o provedor de membros

1. Como uma criança `<system.serviceModel>` para o elemento, adicionar um [ \<comportamento>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento

2. Adicione um [ \<serviçoComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` ao elemento <>.

3. Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) um comportamento>`name` e defina o atributo como um valor apropriado.

4. Adicione um [ \<>serviceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ao elemento> <. `behavior`

5. Adicione um [ \<>de autenticação de nome](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) de usuário ao `<serviceCredentials>` elemento.

6. Defina `userNamePasswordValidationMode` o `MembershipProvider`atributo para .

    > [!IMPORTANT]
    > Se `userNamePasswordValidationMode` o valor não estiver definido, o WCF usará a autenticação do Windows em vez do provedor de membros ASP.NET.

7. Defina `membershipProviderName` o atributo ao nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico). O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.

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

O código a seguir mostra a configuração de um serviço que usa o recurso de associação ASP.

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

## <a name="see-also"></a>Confira também

- [Como utilizar o provedor de função do ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
