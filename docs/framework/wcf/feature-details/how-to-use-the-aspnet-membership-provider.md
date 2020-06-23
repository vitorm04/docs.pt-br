---
title: Como utilizar o provedor de associação do ASP.NET
description: Saiba como o provedor de associação do ASP.NET dá suporte a sites que permitem que os usuários criem um nome de usuário e senha para acesso sem ter uma conta de domínio do Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246721"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="d5a2c-103">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d5a2c-103">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="d5a2c-104">O provedor de associação do ASP.NET é um recurso que permite que os desenvolvedores do ASP.NET criem sites da Web que permitem que os usuários criem combinações exclusivas de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-104">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="d5a2c-105">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e entrar para ter acesso exclusivo ao site e aos seus serviços.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-105">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="d5a2c-106">Isso é diferente da segurança do Windows, o que exige que os usuários tenham contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="d5a2c-107">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação nome de usuário/senha) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-107">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="d5a2c-108">Para um aplicativo de exemplo, consulte [associação e provedor de função](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d5a2c-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="d5a2c-109">Para obter informações sobre como usar o recurso de provedor de função ASP.NET, consulte [como: usar o provedor de função ASP.NET com um serviço](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="d5a2c-109">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="d5a2c-110">O recurso de associação requer o uso de um banco de dados SQL Server para armazenar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-110">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="d5a2c-111">O recurso também inclui métodos para solicitar uma pergunta a qualquer usuário que tenha esquecido sua senha.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-111">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="d5a2c-112">Os desenvolvedores de Windows Communication Foundation (WCF) podem aproveitar esses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-112">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="d5a2c-113">Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-113">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="d5a2c-114">Para transferir os dados para o serviço WCF, use uma associação que ofereça suporte a credenciais de nome de usuário/senha, como <xref:System.ServiceModel.WSHttpBinding> (em configuração, o [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ) e defina o tipo de credencial do cliente como `UserName` .</span><span class="sxs-lookup"><span data-stu-id="d5a2c-114">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="d5a2c-115">No serviço, a segurança do WCF autentica o usuário com base no nome de usuário e senha e também atribui a função especificada pela função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-115">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="d5a2c-116">O WCF não fornece métodos para popular o banco de dados com combinações de nome de usuário/senha ou outras informações de usuário.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-116">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="d5a2c-117">Para configurar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="d5a2c-117">To configure the membership provider</span></span>

1. <span data-ttu-id="d5a2c-118">No arquivo Web.config, no `system.web` elemento <>, crie um `membership` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-118">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="d5a2c-119">No `<membership>` elemento, crie um `<providers>` elemento.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-119">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="d5a2c-120">Como um filho para o `providers` elemento <>, adicione um `<clear />` elemento para liberar a coleção de provedores.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-120">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="d5a2c-121">No `<clear />` elemento, crie um elemento <`add`> com os seguintes atributos definidos como valores apropriados:,,,,,, `name` `type` `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `requiresUniqueEmail` e `passwordFormat` .</span><span class="sxs-lookup"><span data-stu-id="d5a2c-121">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="d5a2c-122">O `name` atributo é usado posteriormente como um valor no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-122">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="d5a2c-123">O exemplo a seguir define como `SqlMembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="d5a2c-123">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="d5a2c-124">O exemplo a seguir mostra a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-124">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="d5a2c-125">Para configurar a segurança do serviço para aceitar a combinação de nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="d5a2c-125">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="d5a2c-126">No arquivo de configuração, no [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicione um [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-126">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="d5a2c-127">Adicione um [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) à seção de associações.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-127">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="d5a2c-128">Para obter mais informações sobre como criar um elemento de associação do WCF, consulte [como especificar uma associação de serviço na configuração](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d5a2c-128">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="d5a2c-129">Defina o atributo `mode` do elemento `<security>` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-129">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="d5a2c-130">Defina o `clientCredentialType` atributo do elemento <`message`> como `UserName` .</span><span class="sxs-lookup"><span data-stu-id="d5a2c-130">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="d5a2c-131">Isso especifica que um par de nome de usuário/senha será usado como a credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-131">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="d5a2c-132">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-132">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="d5a2c-133">Para configurar um serviço para usar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="d5a2c-133">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="d5a2c-134">Como um filho para o `<system.serviceModel>` elemento, adicione um [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elemento</span><span class="sxs-lookup"><span data-stu-id="d5a2c-134">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="d5a2c-135">Adicione um [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) ao elemento <`behaviors`>.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-135">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="d5a2c-136">Adicione um [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-136">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="d5a2c-137">Adicione um [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) ao elemento <`behavior`>.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-137">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="d5a2c-138">Adicione um [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) ao `<serviceCredentials>` elemento.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-138">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="d5a2c-139">Defina o `userNamePasswordValidationMode` atributo como `MembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="d5a2c-139">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d5a2c-140">Se o `userNamePasswordValidationMode` valor não for definido, o WCF usará a autenticação do Windows em vez do provedor de associação do ASP.net.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-140">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="d5a2c-141">Defina o `membershipProviderName` atributo como o nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico).</span><span class="sxs-lookup"><span data-stu-id="d5a2c-141">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="d5a2c-142">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-142">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="d5a2c-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5a2c-143">Example</span></span>

<span data-ttu-id="d5a2c-144">O código a seguir mostra a configuração de um serviço que usa o recurso associação ASP.</span><span class="sxs-lookup"><span data-stu-id="d5a2c-144">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d5a2c-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="d5a2c-145">See also</span></span>

- [<span data-ttu-id="d5a2c-146">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="d5a2c-146">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="d5a2c-147">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="d5a2c-147">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
