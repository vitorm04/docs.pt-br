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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb5adec17f834687038b729a475fbcc0e2311c01
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="fb3ad-102">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="fb3ad-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="fb3ad-103">O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função (em conjunto com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação) é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permite que os usuários criem uma conta com um site e para serem atribuídos a funções de autorização finalidades.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="fb3ad-104">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e faça logon para o acesso exclusivo para o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="fb3ad-105">Isso é diferente de segurança do Windows, que exige que os usuários possuem contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="fb3ad-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome e senha de usuário) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="fb3ad-107">Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fb3ad-108">o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de provedor de associação, consulte [como: usar o provedor de associação ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="fb3ad-108"> the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="fb3ad-109">O recurso de provedor de função usa um banco de dados do SQL Server para armazenar informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-109">The role provider feature uses a SQL Server database to store user information.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fb3ad-110">os desenvolvedores podem aproveitar esses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-110"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="fb3ad-111">Quando integrado a um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, os usuários devem fornecer uma combinação de nome e senha de usuário para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-111">When integrated into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="fb3ad-112">Para habilitar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para usar o banco de dados, você deve criar uma instância do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, defina seu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>e adicionar a instância para a coleção de comportamentos para o <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-112">To enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="fb3ad-113">Para configurar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="fb3ad-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="fb3ad-114">No arquivo Web. config, sob o <`system.web`> elemento, adicionar um <`roleManager`> elemento e defina seu `enabled` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="fb3ad-115">Definir o `defaultProvider` atributo `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="fb3ad-116">Como um filho de <`roleManager`> elemento, adicionar um <`providers`> elemento.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="fb3ad-117">Como um filho de <`providers`> elemento, adicionar um <`add`> elemento com os seguintes atributos definido para os valores apropriados: `name`, `type`, `connectionStringName`, e `applicationName`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="fb3ad-118">Para configurar o serviço para usar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="fb3ad-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="fb3ad-119">No arquivo Web. config, adicione um [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="fb3ad-120">Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o <`system.ServiceModel`> elemento.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="fb3ad-121">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="fb3ad-122">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="fb3ad-123">Adicionar um [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para o <`behavior`> elemento.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="fb3ad-124">Definir o `principalPermissionMode` atributo `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="fb3ad-125">Definir o `roleProviderName` atributo `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="fb3ad-126">O exemplo a seguir mostra um fragmento da configuração.</span><span class="sxs-lookup"><span data-stu-id="fb3ad-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb3ad-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb3ad-127">See Also</span></span>  
 [<span data-ttu-id="fb3ad-128">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="fb3ad-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [<span data-ttu-id="fb3ad-129">Como: usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fb3ad-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
