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
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="64377-102">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="64377-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="64377-103">O provedor de assinatura ASP.NET é um recurso que permite que ASP.NET desenvolvedores criem sites da Web que permitem que os usuários criem combinações exclusivas de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="64377-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="64377-104">Com esta facilidade, qualquer usuário pode estabelecer uma conta no site, e fazer login para acesso exclusivo ao site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="64377-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="64377-105">Isso contrasta com a segurança do Windows, que exige que os usuários tenham contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="64377-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="64377-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome de usuário/senha) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="64377-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="64377-107">Para obter um aplicativo de exemplo, consulte [Adesão e Provedor de Função](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="64377-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="64377-108">Para obter informações sobre como usar o recurso do provedor de ASP.NET função, consulte [Como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="64377-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="64377-109">O recurso de associação requer o uso de um banco de dados do SQL Server para armazenar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="64377-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="64377-110">O recurso também inclui métodos para solicitar com uma pergunta qualquer usuário que tenha esquecido sua senha.</span><span class="sxs-lookup"><span data-stu-id="64377-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="64377-111">Os desenvolvedores da Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="64377-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="64377-112">Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="64377-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="64377-113">Para transferir os dados para o serviço WCF, use uma vinculação <xref:System.ServiceModel.WSHttpBinding> que suporte credenciais de nome de usuário/senha, como `UserName`o (na configuração, o [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e defina o tipo de credencial do cliente para .</span><span class="sxs-lookup"><span data-stu-id="64377-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="64377-114">No serviço, a segurança do WCF autentica o usuário com base no nome de usuário e senha, e também atribui a função especificada pela função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="64377-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="64377-115">O WCF não fornece métodos para preencher o banco de dados com combinações de nome de usuário/senha ou outras informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="64377-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="64377-116">Para configurar o provedor de membros</span><span class="sxs-lookup"><span data-stu-id="64377-116">To configure the membership provider</span></span>

1. <span data-ttu-id="64377-117">No arquivo Web.config, sob `system.web` o elemento <`membership`>, crie um elemento> <.</span><span class="sxs-lookup"><span data-stu-id="64377-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="64377-118">`<membership>` o elemento, `<providers>` crie um elemento.</span><span class="sxs-lookup"><span data-stu-id="64377-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="64377-119">Quando criança, para `providers` o <`<clear />`> elemento, adicione um elemento para lavar a coleção de provedores.</span><span class="sxs-lookup"><span data-stu-id="64377-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="64377-120">`<clear />` o elemento, `add` crie um elemento <> com `name`os `type` `connectionStringName`seguintes atributos `passwordFormat`definidos para valores apropriados:,, , `applicationName` `enablePasswordRetrieval`, `enablePasswordReset`, , `requiresQuestionAndAnswer`, e `requiresUniqueEmail`.</span><span class="sxs-lookup"><span data-stu-id="64377-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="64377-121">O `name` atributo é usado mais tarde como um valor no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="64377-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="64377-122">O exemplo a `SqlMembershipProvider`seguir define-o para .</span><span class="sxs-lookup"><span data-stu-id="64377-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="64377-123">O exemplo a seguir mostra a seção configuração.</span><span class="sxs-lookup"><span data-stu-id="64377-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="64377-124">Para configurar a segurança do serviço para aceitar a combinação de nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="64377-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="64377-125">No arquivo de configuração, o [ \<elemento system.serviceModel>,](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) adicione um [ \<elemento de>de vinculações.](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="64377-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="64377-126">Adicione um [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à seção de vinculações.</span><span class="sxs-lookup"><span data-stu-id="64377-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="64377-127">Para obter mais informações sobre a criação de um elemento de vinculação do WCF, consulte [Como: Especificar uma vinculação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="64377-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="64377-128">Defina o atributo `mode` do elemento `<security>` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="64377-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="64377-129">Defina `clientCredentialType` o atributo do elemento> <`message` para `UserName`.</span><span class="sxs-lookup"><span data-stu-id="64377-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="64377-130">Isso especifica que um par de nome de usuário/senha será usado como credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="64377-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="64377-131">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="64377-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="64377-132">Para configurar um serviço para usar o provedor de membros</span><span class="sxs-lookup"><span data-stu-id="64377-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="64377-133">Como uma criança `<system.serviceModel>` para o elemento, adicionar um [ \<comportamento>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento</span><span class="sxs-lookup"><span data-stu-id="64377-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="64377-134">Adicione um [ \<serviçoComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` ao elemento <>.</span><span class="sxs-lookup"><span data-stu-id="64377-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="64377-135">Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) um comportamento>`name` e defina o atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="64377-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="64377-136">Adicione um [ \<>serviceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ao elemento> <. `behavior`</span><span class="sxs-lookup"><span data-stu-id="64377-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="64377-137">Adicione um [ \<>de autenticação de nome](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) de usuário ao `<serviceCredentials>` elemento.</span><span class="sxs-lookup"><span data-stu-id="64377-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="64377-138">Defina `userNamePasswordValidationMode` o `MembershipProvider`atributo para .</span><span class="sxs-lookup"><span data-stu-id="64377-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="64377-139">Se `userNamePasswordValidationMode` o valor não estiver definido, o WCF usará a autenticação do Windows em vez do provedor de membros ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="64377-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="64377-140">Defina `membershipProviderName` o atributo ao nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico).</span><span class="sxs-lookup"><span data-stu-id="64377-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="64377-141">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="64377-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="64377-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64377-142">Example</span></span>

<span data-ttu-id="64377-143">O código a seguir mostra a configuração de um serviço que usa o recurso de associação ASP.</span><span class="sxs-lookup"><span data-stu-id="64377-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="64377-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="64377-144">See also</span></span>

- [<span data-ttu-id="64377-145">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="64377-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="64377-146">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="64377-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
