---
title: 'Como: usar o provedor de associação do ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: c2567b6abd42ae725b4786eb111e411f7328154e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939798"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="614e2-102">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="614e2-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="614e2-103">O provedor de associação do ASP.NET é um recurso que permite que os desenvolvedores do ASP.NET criem sites da Web que permitem que os usuários criem combinações exclusivas de nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="614e2-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="614e2-104">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e entrar para ter acesso exclusivo ao site e aos seus serviços.</span><span class="sxs-lookup"><span data-stu-id="614e2-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="614e2-105">Isso é diferente da segurança do Windows, o que exige que os usuários tenham contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="614e2-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="614e2-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação nome de usuário/senha) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="614e2-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="614e2-107">Para um aplicativo de exemplo, consulte [associação e provedor de função](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="614e2-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="614e2-108">Para obter informações sobre como usar o recurso de provedor de [função ASP.net, consulte Como: Use o provedor de função ASP.NET com um](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)serviço.</span><span class="sxs-lookup"><span data-stu-id="614e2-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="614e2-109">O recurso de associação requer o uso de um banco de dados SQL Server para armazenar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="614e2-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="614e2-110">O recurso também inclui métodos para solicitar uma pergunta a qualquer usuário que tenha esquecido sua senha.</span><span class="sxs-lookup"><span data-stu-id="614e2-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="614e2-111">Os desenvolvedores de Windows Communication Foundation (WCF) podem aproveitar esses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="614e2-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="614e2-112">Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="614e2-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="614e2-113">Para transferir os dados para o serviço WCF, use uma associação que ofereça suporte a credenciais de nome de usuário/senha <xref:System.ServiceModel.WSHttpBinding> , como (na configuração, o [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e defina o tipo de `UserName`credencial do cliente como.</span><span class="sxs-lookup"><span data-stu-id="614e2-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="614e2-114">No serviço, a segurança do WCF autentica o usuário com base no nome de usuário e senha e também atribui a função especificada pela função ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="614e2-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="614e2-115">O WCF não fornece métodos para popular o banco de dados com combinações de nome de usuário/senha ou outras informações de usuário.</span><span class="sxs-lookup"><span data-stu-id="614e2-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="614e2-116">Para configurar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="614e2-116">To configure the membership provider</span></span>  
  
1. <span data-ttu-id="614e2-117">No arquivo Web. config, no elemento <`system.web`>, crie um elemento <`membership`>.</span><span class="sxs-lookup"><span data-stu-id="614e2-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2. <span data-ttu-id="614e2-118">No elemento, crie um `<providers>` elemento. `<membership>`</span><span class="sxs-lookup"><span data-stu-id="614e2-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3. <span data-ttu-id="614e2-119">Como um filho para o elemento`providers`< >, adicione um `<clear />` elemento para liberar a coleção de provedores.</span><span class="sxs-lookup"><span data-stu-id="614e2-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4. <span data-ttu-id="614e2-120">Sob o `<clear />` elemento, crie um elemento`add`< > com os seguintes atributos definidos como `applicationName`valores `connectionStringName`apropriados `enablePasswordRetrieval`: `name`, `type` `enablePasswordReset` `requiresQuestionAndAnswer` ,,,,, , `requiresUniqueEmail`e .`passwordFormat`</span><span class="sxs-lookup"><span data-stu-id="614e2-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="614e2-121">O `name` atributo é usado posteriormente como um valor no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="614e2-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="614e2-122">O exemplo a seguir define como `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="614e2-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="614e2-123">O exemplo a seguir mostra a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="614e2-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="614e2-124">Para configurar a segurança do serviço para aceitar a combinação de nome de usuário/senha</span><span class="sxs-lookup"><span data-stu-id="614e2-124">To configure service security to accept the user name/password combination</span></span>  
  
1. <span data-ttu-id="614e2-125">No arquivo de configuração, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<no elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , adicione um elemento bindings >.</span><span class="sxs-lookup"><span data-stu-id="614e2-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2. <span data-ttu-id="614e2-126">Adicione um [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à seção associações.</span><span class="sxs-lookup"><span data-stu-id="614e2-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="614e2-127">Para obter mais informações sobre como criar um elemento de associação [do WCF, consulte Como: Especifique uma associação de serviço na](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.</span><span class="sxs-lookup"><span data-stu-id="614e2-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3. <span data-ttu-id="614e2-128">Defina o atributo `mode` do elemento `<security>` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="614e2-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4. <span data-ttu-id="614e2-129">Defina o `clientCredentialType` atributo do elemento <`message`> como `UserName`.</span><span class="sxs-lookup"><span data-stu-id="614e2-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="614e2-130">Isso especifica que um par de nome de usuário/senha será usado como a credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="614e2-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="614e2-131">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="614e2-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="614e2-132">Para configurar um serviço para usar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="614e2-132">To configure a service to use the membership provider</span></span>  
  
1. <span data-ttu-id="614e2-133">Como um filho para o `<system.serviceModel>` elemento, adicione um elemento de [ \<> de comportamentos](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="614e2-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2. <span data-ttu-id="614e2-134">Adicione um [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) de portais ao elemento <`behaviors`>.</span><span class="sxs-lookup"><span data-stu-id="614e2-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3. <span data-ttu-id="614e2-135">Adicione um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="614e2-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="614e2-136">Adicione um [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ao elemento <`behavior`>.</span><span class="sxs-lookup"><span data-stu-id="614e2-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5. <span data-ttu-id="614e2-137">Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) um`<serviceCredentials>` > userNameAuthentication ao elemento.</span><span class="sxs-lookup"><span data-stu-id="614e2-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6. <span data-ttu-id="614e2-138">Defina o `userNamePasswordValidationMode` atributo como `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="614e2-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="614e2-139">Se o `userNamePasswordValidationMode` valor não for definido, o WCF usará a autenticação do Windows em vez do provedor de associação do ASP.net.</span><span class="sxs-lookup"><span data-stu-id="614e2-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>  
  
7. <span data-ttu-id="614e2-140">Defina o `membershipProviderName` atributo como o nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico).</span><span class="sxs-lookup"><span data-stu-id="614e2-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="614e2-141">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="614e2-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="614e2-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="614e2-142">Example</span></span>  
 <span data-ttu-id="614e2-143">O código a seguir mostra a configuração de um serviço que usa o recurso associação ASP.</span><span class="sxs-lookup"><span data-stu-id="614e2-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="614e2-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="614e2-144">See also</span></span>

- [<span data-ttu-id="614e2-145">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="614e2-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="614e2-146">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="614e2-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
