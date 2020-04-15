---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389758"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Criando serviços interoperáveis de perfil básico de WS-I 1.1
Para configurar um ponto final de serviço WCF para ser interoperável com ASP.NET clientes de serviço web:  
  
- Use <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> o tipo como o tipo de vinculação para o ponto final do serviço.  
  
- Não use recursos de contrato de chamada e sessão ou comportamentos de transação no ponto final do serviço  
  
Você pode habilitar opcionalmente o suporte para autenticação de cliente HTTPS e nível de transporte na vinculação.  
  
Os seguintes <xref:System.ServiceModel.BasicHttpBinding> recursos da classe exigem funcionalidade além do Perfil Básico WS-I 1.1:  
  
- Codificação de mensagens MTOM (Message Transmission <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> Optimization Mechanism, mecanismo de otimização de transmissão de mensagens) controlada pela propriedade. Deixe esta propriedade em seu <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> valor padrão, que é não usar MTOM.  
  
- A segurança de <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> mensagens controlada pelo valor fornece suporte ao WS-Security compatível com o Perfil básico de segurança 1.0 do WS-I. Deixe esta propriedade em seu <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> valor padrão, que é não usar o WS-Security.  
  
Para disponibilizar os metadados de um serviço WCF para ASP.NET, use as ferramentas de geração de clientes de [serviços web: Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)e o recurso **Add Web Reference** no Visual Studio. Habilite a publicação de metadados. Para obter mais informações, consulte [''Pontos finais de metadados'](publishing-metadata-endpoints.md)de publicação .  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O código de exemplo a seguir demonstra como adicionar um ponto final WCF compatível com ASP.NET clientes de serviço web em código e, alternativamente, em um arquivo de configuração.  
  
### <a name="code"></a>Código  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Confira também

- [Interoperabilidade com serviços Web do ASP.NET](./feature-details/interop-with-aspnet-web-services.md)
