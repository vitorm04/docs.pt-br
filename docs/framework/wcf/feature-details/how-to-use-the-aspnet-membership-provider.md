---
title: "Como utilizar o provedor de associação do ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 74056ae23b08850b9c9a564248d6e276fc518a8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Como utilizar o provedor de associação do ASP.NET
O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permitem aos usuários criar combinações de nome e senha de usuário exclusivo. Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e entre para obter acesso exclusivo para o site e seus serviços. Isso é diferente de segurança do Windows, que exige que os usuários possuem contas em um domínio do Windows. Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome e senha de usuário) pode usar o site e seus serviços.  
  
 Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Para obter informações sobre como usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso do provedor de função, consulte [como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 O recurso de associação requer o uso de um banco de dados do SQL Server para armazenar as informações do usuário. O recurso também inclui métodos para solicitar uma pergunta quaisquer usuários que tenham esquecido suas senhas.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]os desenvolvedores podem aproveitar esses recursos para fins de segurança. Quando integrado a um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, os usuários devem fornecer uma combinação de nome e senha de usuário para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente. Para transferir dados para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, use uma associação que dá suporte a credenciais de nome e senha do usuário, como o <xref:System.ServiceModel.WSHttpBinding> (na configuração, o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e defina a credencial do cliente Digite para `UserName`. Sobre o serviço, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança autentica o usuário com base no nome de usuário e senha e também atribui a função especificada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] função.  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]não fornece métodos para preencher o banco de dados com combinações de nome e senha de usuário ou outras informações do usuário.  
  
### <a name="to-configure-the-membership-provider"></a>Para configurar o provedor de associação  
  
1.  No arquivo Web. config, sob o <`system.web`> elemento, criar uma <`membership`> elemento.  
  
2.  Sob o `<membership>` elemento, crie um `<providers>` elemento.  
  
3.  Como um filho de <`providers`> elemento, adicionar um `<clear />` elemento para liberar a coleção de provedores.  
  
4.  Sob o `<clear />` elemento, criar uma <`add`> elemento com os seguintes atributos definido para os valores apropriados: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, e `passwordFormat`. O `name` atributo será usado posteriormente como um valor no arquivo de configuração. O exemplo a seguir define `SqlMembershipProvider`.  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Para configurar a segurança do serviço para aceitar a combinação de nome e senha do usuário  
  
1.  No arquivo de configuração, sob o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.  
  
2.  Adicionar um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) para a seção de associações. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Criando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação elemento, consulte [como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Defina o atributo `mode` do elemento `<security>` como `Message`.  
  
4.  Definir o `clientCredentialType` atributo do <`message`> elemento `UserName`. Especifica que um par de nome e senha do usuário será usado como a credencial do cliente.  
  
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
  
1.  Como um filho para o `<system.serviceModel>` elemento, adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento  
  
2.  Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.  
  
3.  Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` de atributo para um valor apropriado.  
  
4.  Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o <`behavior`> elemento.  
  
5.  Adicionar um [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) para o `<serviceCredentials>` elemento.  
  
6.  Definir o `userNamePasswordValidationMode` atributo `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Se o `userNamePasswordValidationMode` valor não for definido, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a autenticação do Windows em vez do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação.  
  
7.  Definir o `membershipProviderName` de atributo para o nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico). O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.  
  
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
 O código a seguir mostra a configuração de um serviço que usa o recurso de associação do ASP.  
  
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
 [Como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
