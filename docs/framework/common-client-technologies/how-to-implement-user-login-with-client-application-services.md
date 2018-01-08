---
title: "Como implementar login de usuário com serviços de aplicativo cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bf073b6db0a69cfda0c69ae34df0396f5dea35c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Como implementar login de usuário com serviços de aplicativo cliente
Você pode usar serviços de aplicativos cliente para validar usuários por meio de um serviço de perfil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] existente. Para obter informações sobre como configurar o serviço de perfil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consulte [Usando formulários de autenticação com Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 Os procedimentos a seguir descrevem como validar os usuários através do serviço de autenticação quando seu aplicativo está configurado para usar um dos provedores de serviço de autenticação de cliente. Para obter mais informações, consulte [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Normalmente você executará todas as validações por meio do método `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType>. Este método gerencia a interação com o serviço de autenticação por meio do provedor de autenticação configurado. Para obter mais informações, consulte [Visão geral dos serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Os procedimentos de autenticação de formulários requerem o acesso a um serviço de autenticação [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] em execução. Para obter orientações sobre testes de ponta a ponta dos recursos de serviços de aplicativos cliente, consulte [Instruções passo a passo: usando serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>Para autenticar um usuário com a autenticação de formulários usando um provedor de credenciais de associação  
  
1.  Implementar a interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>. O exemplo de código a seguir mostra uma implementação <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> para uma classe de caixa de diálogo de logon de <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. Essa caixa de diálogo tem caixas de texto para o nome de usuário e senha e uma caixa de seleção “Lembrar de mim”. Quando o provedor de autenticação do cliente chama o método <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>, o formulário é exibido. Quando o usuário preenche as informações na caixa de diálogo de logon e clica em OK, os valores especificados são retornados em um novo objeto <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Chame o método `static` e <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> e passe cadeias de caracteres vazias como os valores de parâmetro. Quando você especifica cadeias de caracteres vazias, este método chama internamente o método <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> para o provedor de credenciais configurado para seu aplicativo. O exemplo de código a seguir chama esse método para restringir o acesso a um aplicativo do Windows Forms inteiro. Você pode adicionar esse código a um manipulador <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>Para autenticar um usuário com a autenticação de formulários sem usar um provedor de credenciais de associação  
  
-   Chame o método `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> e passe e os valores de nome de usuário e senha recuperados do usuário.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>Para autenticar um usuário com a autenticação do Windows  
  
-   Chame o método `static` e <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> e passe cadeias de caracteres vazias para os parâmetros. Esta chamada de método sempre retornará `true` e adicionará um cookie ao cache de cookies do usuário que contém a identidade do Windows.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Programação robusta  
 O código de exemplo neste tópico demonstra os usos mais simples de autenticação em um aplicativo cliente Windows. Quando você chama o método `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> com a autenticação de formulários e serviços de aplicativos cliente, no entanto, seu código pode gerar um <xref:System.Net.WebException>. Isso indica que o serviço de autenticação está indisponível. Para obter um exemplo de como tratar essa exceção, consulte [Instruções passo a passo: usando serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Visão geral dos serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Como configurar serviços de aplicativo cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Instruções passo a passo: usando serviços de aplicativos cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Usando formulários de autenticação com Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
