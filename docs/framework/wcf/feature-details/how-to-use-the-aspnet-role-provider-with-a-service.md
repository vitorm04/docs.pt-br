---
title: 'Como: Usar o provedor de função ASP.NET com um serviço'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 0ad581a6967c759095d85d946a8557b47a075355
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658228"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="992f0-102">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="992f0-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="992f0-103">O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função (em conjunto com o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação) é um recurso que permite [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aos desenvolvedores criar sites da Web que permitem aos usuários criar uma conta com um site e a serem atribuídos a funções para autorização finalidades.</span><span class="sxs-lookup"><span data-stu-id="992f0-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="992f0-104">Com esse recurso, qualquer usuário pode estabelecer uma conta com o site e faça logon no acesso exclusivo para o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="992f0-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="992f0-105">Isso é diferente de segurança do Windows, o que exige que os usuários têm contas em um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="992f0-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="992f0-106">Em vez disso, qualquer usuário que forneça suas credenciais (a combinação de nome/senha de usuário) pode usar o site e seus serviços.</span><span class="sxs-lookup"><span data-stu-id="992f0-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="992f0-107">Para um aplicativo de exemplo, consulte [provedor de função e associação](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="992f0-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="992f0-108">Para obter mais informações sobre o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] recurso de provedor de associação, consulte [como: Usar o provedor de associação ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="992f0-108">For more information about the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="992f0-109">O recurso de provedor de função usa um banco de dados do SQL Server para armazenar informações do usuário.</span><span class="sxs-lookup"><span data-stu-id="992f0-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="992f0-110">Os desenvolvedores do Windows Communication Foundation (WCF) podem tirar proveito desses recursos para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="992f0-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="992f0-111">Quando integrado em um aplicativo WCF, os usuários devem fornecer uma combinação de nome/senha de usuário para o aplicativo de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="992f0-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="992f0-112">Para habilitar o WCF para usar o banco de dados, você deve criar uma instância da <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe, defina sua <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> propriedade a ser <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>e adicione a instância para a coleção de comportamentos para o <xref:System.ServiceModel.ServiceHost> que está hospedando o serviço.</span><span class="sxs-lookup"><span data-stu-id="992f0-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="992f0-113">Para configurar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="992f0-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="992f0-114">No arquivo Web. config, sob o <`system.web`> elemento, adicionar um <`roleManager`> elemento e defina seu `enabled` de atributo para `true`.</span><span class="sxs-lookup"><span data-stu-id="992f0-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="992f0-115">Defina as `defaultProvider` atributo `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="992f0-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="992f0-116">Como um filho para o <`roleManager`> elemento, adicione um <`providers`> elemento.</span><span class="sxs-lookup"><span data-stu-id="992f0-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="992f0-117">Como um filho para o <`providers`> elemento, adicione um <`add`> elemento com os seguintes atributos definidos com valores apropriados: `name`, `type`, `connectionStringName`, e `applicationName`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="992f0-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="992f0-118">Para configurar o serviço para usar o provedor de função</span><span class="sxs-lookup"><span data-stu-id="992f0-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="992f0-119">No arquivo Web. config, adicione uma [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="992f0-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="992f0-120">Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o <`system.ServiceModel`> elemento.</span><span class="sxs-lookup"><span data-stu-id="992f0-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="992f0-121">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o <`behaviors`> elemento.</span><span class="sxs-lookup"><span data-stu-id="992f0-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="992f0-122">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="992f0-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="992f0-123">Adicionar um [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para o <`behavior`> elemento.</span><span class="sxs-lookup"><span data-stu-id="992f0-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="992f0-124">Defina as `principalPermissionMode` atributo `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="992f0-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="992f0-125">Defina as `roleProviderName` atributo `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="992f0-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="992f0-126">O exemplo a seguir mostra um fragmento da configuração.</span><span class="sxs-lookup"><span data-stu-id="992f0-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="992f0-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="992f0-127">See also</span></span>
- [<span data-ttu-id="992f0-128">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="992f0-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="992f0-129">Como: Usar o provedor de associação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="992f0-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
