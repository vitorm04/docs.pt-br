---
title: Como utilizar o provedor de função do ASP.NET com um serviço
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595291"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="fa401-102">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="fa401-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="fa401-103">O provedor de função ASP.NET (em conjunto com o provedor de associação ASP.NET) é um recurso que permite aos desenvolvedores de ASP.NET criar sites da Web que permitem aos usuários criar uma conta com um site e receber funções para fins de autorização.</span><span class="sxs-lookup"><span data-stu-id="fa401-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="fa401-104">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e fazer logon para ter acesso exclusivo ao site e aos seus serviços.</span><span class="sxs-lookup"><span data-stu-id="fa401-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="fa401-105">Isso é diferente da segurança do Windows, o que exige que os usuários tenham contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa401-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="fa401-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação nome de usuário/senha) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="fa401-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="fa401-107">Para um aplicativo de exemplo, consulte [associação e provedor de função](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="fa401-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="fa401-108">Para obter mais informações sobre o recurso de provedor de associação do ASP.NET, consulte [como: usar o provedor de associação do ASP.net](how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="fa401-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="fa401-109">O recurso de provedor de função usa um banco de dados SQL Server para armazenar informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="fa401-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="fa401-110">Os desenvolvedores de Windows Communication Foundation (WCF) podem aproveitar esses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="fa401-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="fa401-111">Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="fa401-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="fa401-112">Para habilitar o WCF a usar o banco de dados, você deve criar uma instância da <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, definir sua <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade como <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> e adicionar a instância à coleção de comportamentos para o <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.</span><span class="sxs-lookup"><span data-stu-id="fa401-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="fa401-113">Configurar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="fa401-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="fa401-114">No arquivo Web. config, no `system.web` elemento < >, adicione um `roleManager` elemento < > e defina seu `enabled` atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="fa401-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="fa401-115">Defina o `defaultProvider` atributo como `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="fa401-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="fa401-116">Como um filho para o `roleManager` elemento <>, adicione um `providers` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="fa401-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="fa401-117">Como um filho para o `providers` elemento <>, adicione um `add` elemento <> com os seguintes atributos definidos para os valores apropriados: `name` ,, `type` `connectionStringName` e `applicationName` , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fa401-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="fa401-118">Configurar o serviço para usar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="fa401-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="fa401-119">No arquivo Web. config, adicione um [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="fa401-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="fa401-120">Adicione um [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elemento ao elemento <`system.ServiceModel`>.</span><span class="sxs-lookup"><span data-stu-id="fa401-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="fa401-121">Adicione um [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) ao elemento <`behaviors`>.</span><span class="sxs-lookup"><span data-stu-id="fa401-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="fa401-122">Adicione um [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento e defina o `name` atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="fa401-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="fa401-123">Adicione um [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) ao elemento <`behavior`>.</span><span class="sxs-lookup"><span data-stu-id="fa401-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="fa401-124">Defina o `principalPermissionMode` atributo como `UseAspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="fa401-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="fa401-125">Defina o `roleProviderName` atributo como `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="fa401-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="fa401-126">O exemplo a seguir mostra um fragmento da configuração.</span><span class="sxs-lookup"><span data-stu-id="fa401-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa401-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa401-127">See also</span></span>

- [<span data-ttu-id="fa401-128">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="fa401-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="fa401-129">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fa401-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
