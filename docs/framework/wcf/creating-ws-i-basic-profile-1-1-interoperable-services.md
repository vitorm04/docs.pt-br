---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: eb1cd12c45a276d5c3cb14f89205fff618121abc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320138"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Criando serviços interoperáveis de perfil básico de WS-I 1.1
Para configurar um ponto de extremidade de serviço WCF para ser interoperável com clientes do serviço Web ASP.NET:  
  
- Use o tipo <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> como o tipo de associação para o ponto de extremidade de serviço.  
  
- Não usar recursos de retorno de chamada e de contrato de sessão ou comportamentos de transação em seu ponto de extremidade de serviço  
  
 Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação.  
  
 Os seguintes recursos da classe <xref:System.ServiceModel.BasicHttpBinding> exigem funcionalidade além do WS-I Basic Profile 1,1:  
  
- Codificação de mensagem MTOM (mecanismo de otimização de transmissão de mensagens) controlada pela propriedade <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>. Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> para não usar MTOM.  
  
- A segurança de mensagem controlada pelo valor de <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> fornece suporte ao WS-Security com o WS-I Basic Security Profile 1,0. Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> para não usar o WS-Security.  
  
 Para disponibilizar os metadados para um serviço WCF para ASP.NET, use a ferramenta de geração de cliente do serviço Web: [ferramenta de linguagem de descrição de serviços Web (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (disco. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)e o recurso `Add Web Reference` no Visual Studio; Você deve habilitar a publicação de metadados. Para obter mais informações, consulte [publicando pontos de extremidade de metadados](publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir demonstra como adicionar um ponto de extremidade WCF compatível com clientes de serviço Web ASP.NET em código e, como alternativa, em um arquivo de configuração.  
  
### <a name="code"></a>Código  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Consulte também

- [Interoperabilidade com serviços Web do ASP.NET](./feature-details/interop-with-aspnet-web-services.md)
