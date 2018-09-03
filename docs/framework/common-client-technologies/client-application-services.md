---
title: Serviços de aplicativo cliente
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d58510240593f73ff761aa669035f28598006c10
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401577"
---
# <a name="client-application-services"></a><span data-ttu-id="f3921-102">Serviços de aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="f3921-102">Client Application Services</span></span>
<span data-ttu-id="f3921-103">Os serviços de aplicativos cliente facilitam a criação de aplicativos baseados em Windows que usam os serviços de aplicativo de perfil, funções e logon [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] incluídos nas Extensões AJAX do Microsoft ASP.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="f3921-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="f3921-104">Esses serviços permitem que vários aplicativos Web e baseados no Windows compartilhem informações do usuário e a funcionalidade de gerenciamento de usuários de um único servidor.</span><span class="sxs-lookup"><span data-stu-id="f3921-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="f3921-105">Por exemplo, você pode usar esses serviços para executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="f3921-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f3921-106">Autenticar um usuário.</span><span class="sxs-lookup"><span data-stu-id="f3921-106">Authenticate a user.</span></span> <span data-ttu-id="f3921-107">Você pode usar o serviço de autenticação para verificar a identidade de um usuário.</span><span class="sxs-lookup"><span data-stu-id="f3921-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="f3921-108">Determinar as funções de um usuário autenticado.</span><span class="sxs-lookup"><span data-stu-id="f3921-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="f3921-109">Você pode usar o serviço de funções para alterar a interface do usuário do seu aplicativo dependendo da função do usuário.</span><span class="sxs-lookup"><span data-stu-id="f3921-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="f3921-110">Por exemplo, você pode fornecer recursos adicionais para os usuários que estão em uma função de administrador.</span><span class="sxs-lookup"><span data-stu-id="f3921-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="f3921-111">Armazenar e acessar configurações de aplicativo por usuário localizadas no servidor.</span><span class="sxs-lookup"><span data-stu-id="f3921-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="f3921-112">Você pode usar o serviço de configurações da Web (também conhecido como o serviço de perfil) para compartilhar as configurações entre vários aplicativos e locais.</span><span class="sxs-lookup"><span data-stu-id="f3921-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="f3921-113">Os serviços de aplicativos cliente aproveitam o modelo de extensibilidade de serviços Web por meio de provedores de serviço cliente que você pode especificar nos arquivos de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3921-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="f3921-114">Esses provedores de serviço incluem a funcionalidade offline que usa um cache local para autenticação, funções e dados de configurações quando uma conexão de rede está indisponível.</span><span class="sxs-lookup"><span data-stu-id="f3921-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="f3921-115">Para obter mais informações sobre os serviços de aplicativos [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consulte [Visão geral sobre Serviços de Aplicativos ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span><span class="sxs-lookup"><span data-stu-id="f3921-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3921-116">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f3921-116">In This Section</span></span>  
 [<span data-ttu-id="f3921-117">Visão geral dos serviços de aplicativos cliente</span><span class="sxs-lookup"><span data-stu-id="f3921-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="f3921-118">Descreve os recursos disponíveis por meio de provedores de serviço de aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="f3921-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="f3921-119">Como configurar serviços de aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="f3921-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="f3921-120">Descreve como usar o designer de projeto do Visual Studio para habilitar e configurar serviços de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3921-120">Describes how to use the Visual Studio project designer to enable and configuration application services.</span></span> <span data-ttu-id="f3921-121">Também descreve as alterações correspondentes no arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="f3921-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="f3921-122">Como implementar login de usuário com serviços de aplicativos cliente</span><span class="sxs-lookup"><span data-stu-id="f3921-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="f3921-123">Descreve como validar um usuário quando seu aplicativo está configurado para usar um provedor de serviços de autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="f3921-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="f3921-124">Instruções passo a passo: usando serviços de aplicativos cliente</span><span class="sxs-lookup"><span data-stu-id="f3921-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="f3921-125">Descreve como combinar todos os recursos de serviços de aplicativos cliente em um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3921-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="f3921-126">Este passo a passo fornece orientação de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="f3921-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="f3921-127">Por exemplo, ele inclui instruções sobre como criar um aplicativo de serviço Web ASP.NET que você pode usar para testar os serviços de aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="f3921-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f3921-128">Referência</span><span class="sxs-lookup"><span data-stu-id="f3921-128">Reference</span></span>  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a><span data-ttu-id="f3921-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3921-129">See Also</span></span>  
 [<span data-ttu-id="f3921-130">Visão geral dos Serviços de Aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f3921-130">ASP.NET Application Services Overview</span></span>](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="f3921-131">Usando formulários de autenticação com Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="f3921-131">Using Forms Authentication with Microsoft Ajax</span></span>](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="f3921-132">Usando informações de funções com o Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="f3921-132">Using Roles Information with Microsoft Ajax</span></span>](https://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="f3921-133">Usando informações de perfis com o Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="f3921-133">Using Profile Information with Microsoft Ajax</span></span>](https://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="f3921-134">Autenticação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f3921-134">ASP.NET Authentication</span></span>](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="f3921-135">[Gerenciando autorização usando funções](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="f3921-135">[Managing Authorization Using Roles](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="f3921-136">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="f3921-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)
