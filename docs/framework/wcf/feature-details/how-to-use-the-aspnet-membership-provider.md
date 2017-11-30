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
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="4b2fa-102">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b2fa-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="4b2fa-103">O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permitem aos usuários criar combinações de nome e senha de usuário exclusivo.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="4b2fa-104">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e entre para obter acesso exclusivo para o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="4b2fa-105">Isso é diferente de segurança do Windows, que exige que os usuários possuem contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="4b2fa-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome e senha de usuário) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="4b2fa-107">Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4b2fa-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="4b2fa-108">Para obter informações sobre como usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso do provedor de função, consulte [como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="4b2fa-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="4b2fa-109">O recurso de associação requer o uso de um banco de dados do SQL Server para armazenar as informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="4b2fa-110">O recurso também inclui métodos para solicitar uma pergunta quaisquer usuários que tenham esquecido suas senhas.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="4b2fa-111">os desenvolvedores podem aproveitar esses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-111"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="4b2fa-112">Quando integrado a um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, os usuários devem fornecer uma combinação de nome e senha de usuário para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-112">When integrated into an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="4b2fa-113">Para transferir dados para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço, use uma associação que dá suporte a credenciais de nome e senha do usuário, como o <xref:System.ServiceModel.WSHttpBinding> (na configuração, o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) e defina a credencial do cliente Digite para `UserName`.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-113">To transfer the data to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="4b2fa-114">Sobre o serviço, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança autentica o usuário com base no nome de usuário e senha e também atribui a função especificada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] função.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-114">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4b2fa-115">não fornece métodos para preencher o banco de dados com combinações de nome e senha de usuário ou outras informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-115"> does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="4b2fa-116">Para configurar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="4b2fa-116">To configure the membership provider</span></span>  
  
1.  <span data-ttu-id="4b2fa-117">No arquivo Web. config, sob o <`system.web`> elemento, criar uma <`membership`> elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2.  <span data-ttu-id="4b2fa-118">Sob o `<membership>` elemento, crie um `<providers>` elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3.  <span data-ttu-id="4b2fa-119">Como um filho de <`providers`> elemento, adicionar um `<clear />` elemento para liberar a coleção de provedores.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4.  <span data-ttu-id="4b2fa-120">Sob o `<clear />` elemento, criar uma <`add`> elemento com os seguintes atributos definido para os valores apropriados: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, e `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="4b2fa-121">O `name` atributo será usado posteriormente como um valor no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="4b2fa-122">O exemplo a seguir define `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="4b2fa-123">O exemplo a seguir mostra a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="4b2fa-124">Para configurar a segurança do serviço para aceitar a combinação de nome e senha do usuário</span><span class="sxs-lookup"><span data-stu-id="4b2fa-124">To configure service security to accept the user name/password combination</span></span>  
  
1.  <span data-ttu-id="4b2fa-125">No arquivo de configuração, sob o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, adicionar um [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2.  <span data-ttu-id="4b2fa-126">Adicionar um [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) para a seção de associações.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4b2fa-127">Criando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação elemento, consulte [como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4b2fa-127"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3.  <span data-ttu-id="4b2fa-128">Defina o atributo `mode` do elemento `<security>` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4.  <span data-ttu-id="4b2fa-129">Definir o `clientCredentialType` atributo do <`message`> elemento `UserName`.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="4b2fa-130">Especifica que um par de nome e senha do usuário será usado como a credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="4b2fa-131">O exemplo a seguir mostra o código de configuração para a associação.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="4b2fa-132">Para configurar um serviço para usar o provedor de associação</span><span class="sxs-lookup"><span data-stu-id="4b2fa-132">To configure a service to use the membership provider</span></span>  
  
1.  <span data-ttu-id="4b2fa-133">Como um filho para o `<system.serviceModel>` elemento, adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento</span><span class="sxs-lookup"><span data-stu-id="4b2fa-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2.  <span data-ttu-id="4b2fa-134">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3.  <span data-ttu-id="4b2fa-135">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="4b2fa-136">Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o <`behavior`> elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5.  <span data-ttu-id="4b2fa-137">Adicionar um [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) para o `<serviceCredentials>` elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6.  <span data-ttu-id="4b2fa-138">Definir o `userNamePasswordValidationMode` atributo `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4b2fa-139">Se o `userNamePasswordValidationMode` valor não for definido, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa a autenticação do Windows em vez do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-139">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7.  <span data-ttu-id="4b2fa-140">Definir o `membershipProviderName` de atributo para o nome do provedor (especificado ao adicionar o provedor no primeiro procedimento neste tópico).</span><span class="sxs-lookup"><span data-stu-id="4b2fa-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="4b2fa-141">O exemplo a seguir mostra o fragmento do `<serviceCredentials>` para este ponto.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4b2fa-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b2fa-142">Example</span></span>  
 <span data-ttu-id="4b2fa-143">O código a seguir mostra a configuração de um serviço que usa o recurso de associação do ASP.</span><span class="sxs-lookup"><span data-stu-id="4b2fa-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b2fa-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b2fa-144">See Also</span></span>  
 [<span data-ttu-id="4b2fa-145">Como: usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="4b2fa-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="4b2fa-146">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="4b2fa-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
