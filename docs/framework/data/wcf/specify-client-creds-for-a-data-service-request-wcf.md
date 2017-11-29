---
title: "Como: especificar as credenciais do cliente para uma solicitação de serviço de dados (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88e41101ab9a963ac09610b04afee745aa61c8e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Como: especificar as credenciais do cliente para uma solicitação de serviço de dados (WCF Data Services)
Por padrão, a biblioteca de cliente não fornece credenciais ao enviar uma solicitação para um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] serviço. No entanto, você pode especificar que as credenciais enviadas para autenticar solicitações ao serviço de dados, fornecendo um <xref:System.Net.NetworkCredential> para o <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> propriedade o <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). O exemplo neste tópico mostra como fornecer explicitamente as credenciais que são usadas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente ao solicitar dados do serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Você também pode usar o [serviço de dados de exemplo Northwind](http://go.microsoft.com/fwlink/?LinkId=187426) que é publicado no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site da Web; esses dados de exemplo serviço é somente leitura e tentar salvar alterações retornará um erro. Serviços de dados de exemplo no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site da Web permite a autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é da página de código por trás de um arquivo de linguagem de marcação de aplicativo extensível (XAML) que é a página principal do aplicativo Windows Presentation Framework. Este exemplo exibe um `LoginWindow` instância para coletar a autenticação de credenciais do usuário e, em seguida, usa essas credenciais ao fazer uma solicitação ao serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a página principal do aplicativo do WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é da página de código por trás da janela que é usada para coletar as credenciais de autenticação do usuário antes de fazer uma solicitação ao serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define o logon do aplicativo do WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 As seguintes considerações de segurança se aplicam ao exemplo neste tópico:  
  
-   Para verificar se as credenciais fornecidas neste exemplo de trabalho, o serviço de dados Northwind deve usar um esquema de autenticação diferente de acesso anônimo. Caso contrário, o site que hospeda o serviço de dados não solicitará credenciais.  
  
-   As credenciais do usuário devem ser solicitadas somente durante a execução e não devem ser armazenada em cache. As credenciais sempre devem ser armazenadas com segurança.  
  
-   Os dados enviados com a Autenticação Básica e Digest não são criptografados e, portanto, os dados podem ser vistos por um adversário. Além disso, as credenciais de autenticação básica (nome de usuário e senha) são enviadas em texto não criptografado e podem ser interceptadas.  
  
 Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
