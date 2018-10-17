---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 80c61f11f82a13fe5aedb9d21ae2555f86fd4aff
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371206"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Criando serviços interoperáveis de perfil básico de WS-I 1.1
Para configurar um ponto de extremidade de serviço do WCF para interoperabilidade com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] clientes de serviço Web:  
  
-   Use o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tipo como o tipo de associação para o ponto de extremidade de serviço.  
  
-   Não use o retorno de chamada e recursos de contrato de sessão ou comportamentos de transação em seu ponto de extremidade de serviço  
  
 Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação.  
  
 Os seguintes recursos do <xref:System.ServiceModel.BasicHttpBinding> classe precisar de funcionalidade além do WS-I Basic Profile 1.1:  
  
-   Codificação de mensagem (MTOM Transmission Optimization Mechanism) mensagem controlada pela <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade. Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> para não usar o MTOM.  
  
-   Controlado por segurança da mensagem o <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> valor fornece suporte a WS-Security em conformidade com WS-I Basic Security Profile 1.0. Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> para não usar WS-Security.  
  
 Para disponibilizar para os metadados para um serviço WCF [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use as ferramentas de geração de cliente de serviço Web: [ferramenta do Web Services Description Language (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [ferramenta de descoberta de serviços da Web (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)e o `Add Web Reference` recurso no Visual Studio; você deve habilitar a publicação de metadados. Para obter mais informações, consulte [publicando pontos de extremidade de metadados](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir demonstra como adicionar um ponto de extremidade do WCF que é compatível com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] clientes de serviço em código e, como alternativa, em um arquivo de configuração da Web.  
  
### <a name="code"></a>Código  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade com serviços Web do ASP.NET](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
