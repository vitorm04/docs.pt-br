---
title: "Serviços de aplicativo cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31738e205d0b2b88cbb049607eeb027db873db3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="client-application-services"></a>Serviços de aplicativo cliente
Os serviços de aplicativos cliente facilitam a criação de aplicativos baseados em Windows que usam os serviços de aplicativo de perfil, funções e logon [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] incluídos nas Extensões AJAX do Microsoft ASP.NET 2.0. Esses serviços permitem que vários aplicativos Web e baseados no Windows compartilhem informações do usuário e a funcionalidade de gerenciamento de usuários de um único servidor. Por exemplo, você pode usar esses serviços para executar as seguintes tarefas:  
  
-   Autenticar um usuário. Você pode usar o serviço de autenticação para verificar a identidade de um usuário.  
  
-   Determinar as funções de um usuário autenticado. Você pode usar o serviço de funções para alterar a interface do usuário do seu aplicativo dependendo da função do usuário. Por exemplo, você pode fornecer recursos adicionais para os usuários que estão em uma função de administrador.  
  
-   Armazenar e acessar configurações de aplicativo por usuário localizadas no servidor. Você pode usar o serviço de configurações da Web (também conhecido como o serviço de perfil) para compartilhar as configurações entre vários aplicativos e locais.  
  
 Os serviços de aplicativos cliente aproveitam o modelo de extensibilidade de serviços Web por meio de provedores de serviço cliente que você pode especificar nos arquivos de configuração de aplicativo. Esses provedores de serviço incluem a funcionalidade offline que usa um cache local para autenticação, funções e dados de configurações quando uma conexão de rede está indisponível.  
  
 Para obter mais informações sobre os serviços de aplicativos [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consulte [Visão geral sobre Serviços de Aplicativos ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral dos serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Descreve os recursos disponíveis por meio de provedores de serviço de aplicativos cliente.  
  
 [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Descreve como usar o designer de projeto [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] para habilitar e configurar serviços de aplicativo. Também descreve as alterações correspondentes no arquivo App.config.  
  
 [Como implementar login de usuário com serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Descreve como validar um usuário quando seu aplicativo está configurado para usar um provedor de serviços de autenticação de cliente.  
  
 [Instruções passo a passo: usando serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Descreve como combinar todos os recursos de serviços de aplicativos cliente em um único aplicativo. Este passo a passo fornece orientação de ponta a ponta. Por exemplo, ele inclui instruções sobre como criar um aplicativo de serviço Web ASP.NET que você pode usar para testar os serviços de aplicativos cliente.  
  
## <a name="reference"></a>Referência  
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
  
## <a name="see-also"></a>Consulte também  
 [Visão geral dos serviços de aplicativo do ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Usando formulários de autenticação com Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Usando funções de informações com o Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Usando informações de perfil com o Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Autenticação do ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Gerenciando autorização usando funções](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Visão Geral das Configurações do Aplicativo](../../../docs/framework/winforms/advanced/application-settings-overview.md)
