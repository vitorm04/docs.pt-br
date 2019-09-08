---
title: 'Como: Especificar credenciais de cliente para uma solicitação de serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: 4177b7f5138bd3e3ddd63e4a0d8d4bcb2be01fbb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790329"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Como: Especificar credenciais de cliente para uma solicitação de serviço de dados (WCF Data Services)
Por padrão, a biblioteca de cliente não fornece credenciais ao enviar uma solicitação para um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] serviço. No entanto, você pode especificar que as credenciais sejam enviadas para autenticar solicitações para o serviço de <xref:System.Net.NetworkCredential> dados fornecendo <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> um para a <xref:System.Data.Services.Client.DataServiceContext>Propriedade do. Para obter mais informações, consulte [securing WCF Data Services](securing-wcf-data-services.md). O exemplo neste tópico mostra como fornecer explicitamente as credenciais que são usadas pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente ao solicitar dados do serviço de dados.  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md). Você também pode usar o [serviço de dados de exemplo Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) publicado no [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] site; esse serviço de dados de exemplo é somente leitura e a tentativa de salvar alterações retorna um erro. Os serviços de dados de exemplo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] no site permitem autenticação anônima.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é da página code-behind para um arquivo de Extensible Application Markup Language (XAML) que é a página principal do aplicativo Windows Presentation Framework. Este exemplo exibe uma `LoginWindow` instância para coletar credenciais de autenticação do usuário e, em seguida, usa essas credenciais ao fazer uma solicitação para o serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a página principal do aplicativo WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é da página code-behind da janela que é usada para coletar as credenciais de autenticação do usuário antes de fazer uma solicitação para o serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define o logon do aplicativo do WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 As seguintes considerações de segurança se aplicam ao exemplo neste tópico:  
  
- Para verificar se as credenciais fornecidas neste exemplo funcionam, o serviço de dados Northwind deve usar um esquema de autenticação diferente do acesso anônimo. Caso contrário, o site que hospeda o serviço de dados não solicitará credenciais.  
  
- As credenciais de usuário só devem ser solicitadas durante a execução e não devem ser armazenadas em cache. As credenciais sempre devem ser armazenadas com segurança.  
  
- Os dados enviados com a Autenticação Básica e Digest não são criptografados e, portanto, os dados podem ser vistos por um adversário. Além disso, as credenciais de autenticação básica (nome de usuário e senha) são enviadas em texto não criptografado e podem ser interceptadas.  
  
 Para obter mais informações, consulte [securing WCF Data Services](securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Protegendo o WCF Data Services](securing-wcf-data-services.md)
- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
