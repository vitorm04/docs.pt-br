---
title: 'Como: usar o provedor de associação do ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 8011b026e857dd6e5815ef7da00c1c33db8b5b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310350"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="497a9-102">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="497a9-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="497a9-103">O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permitem aos usuários criar combinações de nome e senha de usuário exclusivo.</span><span class="sxs-lookup"><span data-stu-id="497a9-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="497a9-104">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e entrar para acesso exclusivo para o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="497a9-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="497a9-105">Isso é diferente de segurança do Windows, o que exige que os usuários têm contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="497a9-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="497a9-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome/senha de usuário) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="497a9-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="497a9-107">Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="497a9-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="497a9-108">Para obter informações sobre como usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de provedor de função, consulte [como: Usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="497a9-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="497a9-109">O recurso de associação requer o uso de um banco de dados do SQL Server para armazenar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="497a9-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="497a9-110">O recurso também inclui métodos para avisar com uma pergunta quaisquer usuários que tenham esquecido sua senha.</span><span class="sxs-lookup"><span data-stu-id="497a9-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="497a9-111">Os desenvolvedores do Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="497a9-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="497a9-112">Quando integrado a um aplicativo do WCF, os usuários devem fornecer uma combinação de nome/senha de usuário para o aplicativo de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="497a9-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="497a9-113">Para transferir os dados para o serviço WCF, usar uma associação que dá suporte a credenciais de nome/senha do usuário, como o <xref:System.ServiceModel.WSHttpBinding> (na configuração, o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e definir o tipo de credencial para `UserName`.</span><span class="sxs-lookup"><span data-stu-id="497a9-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="497a9-114">No serviço de segurança do WCF autentica o usuário com base no nome de usuário e senha e também atribui a função especificada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] função.</span><span class="sxs-lookup"><span data-stu-id="497a9-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="497a9-115">O WCF não fornece métodos para preencher o banco de dados com combinações de nome/senha de usuário ou outras informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="497a9-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="497a9-116">Para configurar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="497a9-116">To configure the membership provider</span></span>  
  
1. <span data-ttu-id="497a9-117">No arquivo Web. config, sob o <`system.web`> elemento, crie um <`membership`> elemento.</span><span class="sxs-lookup"><span data-stu-id="497a9-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2. <span data-ttu-id="497a9-118">Sob o `<membership>` elemento, criar um `<providers>` elemento.</span><span class="sxs-lookup"><span data-stu-id="497a9-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3. <span data-ttu-id="497a9-119">Como um filho para o <`providers`> elemento, adicionar um `<clear />` elemento para a coleção de provedores de liberação.</span><span class="sxs-lookup"><span data-stu-id="497a9-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4. <span data-ttu-id="497a9-120">Sob o `<clear />` elemento, crie um <`add`> elemento com os seguintes atributos definidos com valores apropriados: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, e `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="497a9-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="497a9-121">O `name` atributo é usado posteriormente como um valor no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="497a9-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="497a9-122">O exemplo a seguir define como `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="497a9-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="497a9-123">O exemplo a seguir mostra a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="497a9-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="497a9-124">Para configurar a segurança de serviço para aceitar a combinação de nome/senha do usuário</span><span class="sxs-lookup"><span data-stu-id="497a9-124">To configure service security to accept the user name/password combination</span></span>  
  
1. <span data-ttu-id="497a9-125">No arquivo de configuração, sob o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="497a9-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2. <span data-ttu-id="497a9-126">Adicionar um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à seção de associações.</span><span class="sxs-lookup"><span data-stu-id="497a9-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="497a9-127">Para obter mais informações sobre a criação de um elemento de associação do WCF, consulte [como: Especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="497a9-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3. <span data-ttu-id="497a9-128">Defina o atributo `mode` do elemento `<security>` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="497a9-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4. <span data-ttu-id="497a9-129">Defina as `clientCredentialType` atributo da <`message`> elemento a ser `UserName`.</span><span class="sxs-lookup"><span data-stu-id="497a9-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="497a9-130">Isso especifica que um par de nome/senha do usuário será usado como credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="497a9-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="497a9-131">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="497a9-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="497a9-132">Para configurar um serviço para usar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="497a9-132">To configure a service to use the membership provider</span></span>  
  
1. <span data-ttu-id="497a9-133">Como um filho para o `<system.serviceModel>` elemento, adicione uma [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento</span><span class="sxs-lookup"><span data-stu-id="497a9-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2. <span data-ttu-id="497a9-134">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.</span><span class="sxs-lookup"><span data-stu-id="497a9-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3. <span data-ttu-id="497a9-135">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="497a9-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="497a9-136">Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o <`behavior`> elemento.</span><span class="sxs-lookup"><span data-stu-id="497a9-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5. <span data-ttu-id="497a9-137">Adicionar um [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) para o `<serviceCredentials>` elemento.</span><span class="sxs-lookup"><span data-stu-id="497a9-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6. <span data-ttu-id="497a9-138">Defina as `userNamePasswordValidationMode` atributo `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="497a9-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="497a9-139">Se o `userNamePasswordValidationMode` valor não for definido, o WCF usa a autenticação do Windows em vez do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação.</span><span class="sxs-lookup"><span data-stu-id="497a9-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7. <span data-ttu-id="497a9-140">Defina o `membershipProviderName` de atributo para o nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico).</span><span class="sxs-lookup"><span data-stu-id="497a9-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="497a9-141">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="497a9-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="497a9-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="497a9-142">Example</span></span>  
 <span data-ttu-id="497a9-143">O código a seguir mostra a configuração para um serviço que usa o recurso de associação do ASP.</span><span class="sxs-lookup"><span data-stu-id="497a9-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="497a9-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="497a9-144">See also</span></span>

- [<span data-ttu-id="497a9-145">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="497a9-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="497a9-146">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="497a9-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
