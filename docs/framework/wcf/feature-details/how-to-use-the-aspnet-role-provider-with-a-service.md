---
title: Como utilizar o provedor de função do ASP.NET com um serviço
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184765"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="15695-102">Como utilizar o provedor de função do ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="15695-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="15695-103">O provedor de funções ASP.NET (em conjunto com o provedor de membros ASP.NET) é um recurso que permite que os desenvolvedores ASP.NET criem sites da Web que permitam aos usuários criar uma conta com um site e serem atribuídos funções para fins de autorização.</span><span class="sxs-lookup"><span data-stu-id="15695-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="15695-104">Com esse recurso, qualquer usuário pode estabelecer uma conta no site e fazer login para acesso exclusivo ao site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="15695-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="15695-105">Isso contrasta com a segurança do Windows, que exige que os usuários tenham contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="15695-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="15695-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome de usuário/senha) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="15695-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="15695-107">Para obter um aplicativo de exemplo, consulte [Adesão e Provedor de Função](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="15695-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="15695-108">Para obter mais informações sobre o recurso do provedor de membros ASP.NET, consulte [Como: Usar o provedor de adesão ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="15695-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="15695-109">O recurso provedor de função usa um banco de dados SQL Server para armazenar informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="15695-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="15695-110">Os desenvolvedores da Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="15695-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="15695-111">Quando integrado a um aplicativo WCF, os usuários devem fornecer uma combinação de nome de usuário/senha para o aplicativo cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="15695-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="15695-112">Para permitir que o WCF use o banco <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> de dados, você deve criar uma instância da classe, definir sua <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade para <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, e adicionar a instância à coleção de comportamentos ao <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.</span><span class="sxs-lookup"><span data-stu-id="15695-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="15695-113">Configure o provedor de função</span><span class="sxs-lookup"><span data-stu-id="15695-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="15695-114">No arquivo Web.config, sob `system.web` o elemento <`roleManager`>, adicione `enabled` um `true`elemento> <e defina seu atributo para .</span><span class="sxs-lookup"><span data-stu-id="15695-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="15695-115">Defina `defaultProvider` o `SqlRoleProvider`atributo para .</span><span class="sxs-lookup"><span data-stu-id="15695-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="15695-116">Quando criança, ao `roleManager` elemento <>, adicione um elemento> <. `providers`</span><span class="sxs-lookup"><span data-stu-id="15695-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="15695-117">Quando criança, ao `providers` elemento `add` <>, adicione um elemento <> `name`com `type` `connectionStringName`os seguintes atributos definidos aos valores apropriados: , , e `applicationName`, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="15695-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="15695-118">Configure o serviço para usar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="15695-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="15695-119">No arquivo Web.config, adicione um [ \<elemento system.serviceModel>.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="15695-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="15695-120">Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) um elemento de>`system.ServiceModel` de comportamentos ao elemento <>.</span><span class="sxs-lookup"><span data-stu-id="15695-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="15695-121">Adicione um [ \<serviçoComportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` ao elemento <>.</span><span class="sxs-lookup"><span data-stu-id="15695-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="15695-122">Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) um comportamento>`name` elemento e defina o atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="15695-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="15695-123">Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) um>de `behavior` autorização de serviço ao elemento <>.</span><span class="sxs-lookup"><span data-stu-id="15695-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="15695-124">Defina `principalPermissionMode` o `UseAspNetRoles`atributo para .</span><span class="sxs-lookup"><span data-stu-id="15695-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="15695-125">Defina `roleProviderName` o `SqlRoleProvider`atributo para .</span><span class="sxs-lookup"><span data-stu-id="15695-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="15695-126">O exemplo a seguir mostra um fragmento da configuração.</span><span class="sxs-lookup"><span data-stu-id="15695-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15695-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="15695-127">See also</span></span>

- [<span data-ttu-id="15695-128">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="15695-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="15695-129">Como utilizar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="15695-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
