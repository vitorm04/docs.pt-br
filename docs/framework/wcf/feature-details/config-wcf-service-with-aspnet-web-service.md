---
title: Como configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: ddd7e8c95701532010b54e5136a33d37d139f6a4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739226"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>Como configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET

Para configurar um ponto final de serviço da Windows Communication Foundation (WCF) <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> para ser interoperável com ASP.NET clientes de serviço web, use o tipo como o tipo de vinculação para o ponto final do serviço.  
  
 Você pode habilitar opcionalmente o suporte para autenticação de cliente HTTPS e nível de transporte na vinculação. ASP.NET clientes de serviçoweb não suportam codificação de mensagens MTOM, então a <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade deve ser deixada como seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>. ASP.NET clientes do Web Service não suportam <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> ws-security, portanto, o deve ser definido como <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
 Para disponibilizar os metadados de um serviço WCF para ASP.NET ferramentas de geração de proxy de serviços web (ou seja, [Ferramenta de Linguagem de Descrição de Serviços Web (Wsdl.exe),](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100))Ferramenta de Descoberta de [Serviços Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))e o recurso **Adicionar referência web** no Visual Studio), você deve expor um ponto final de metadados HTTP/GET.  
  
## <a name="add-an-endpoint-in-code"></a>Adicione um ponto final no código  
  
1. Criar uma <xref:System.ServiceModel.BasicHttpBinding> nova instância  
  
2. Opcionalmente, habilite a segurança do transporte para a <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>vinculação deste ponto final de serviço, definindo o modo de segurança para a vinculação a . Para obter detalhes, consulte [Segurança de Transporte](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Adicione um novo ponto final de aplicativo ao seu host de serviço usando a instância de vinculação que você acabou de criar. Para obter detalhes sobre como adicionar um ponto final de serviço no código, consulte [como: Criar um ponto final de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
4. Habilite um ponto final de metadados HTTP/GET para o seu serviço. Para obter [detalhes, consulte Como publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>Adicione um ponto final em um arquivo de configuração  
  
1. Crie uma <xref:System.ServiceModel.BasicHttpBinding> nova configuração de vinculação. Para obter detalhes, consulte [como: Especificar uma vinculação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
2. Opcionalmente, habilite a segurança do transporte para esta configuração de vinculação de ponto final de serviço, definindo o modo de segurança para a vinculação a <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>. Para obter detalhes, consulte [Segurança de Transporte](../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
3. Configure um novo ponto final de aplicativo para o seu serviço usando a configuração de vinculação que você acabou de criar. Para obter detalhes sobre como adicionar um ponto final de serviço em um arquivo de configuração, consulte [como: Criar um ponto final de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
4. Habilite um ponto final de metadados HTTP/GET para o seu serviço. Para obter detalhes, consulte [Como publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
## <a name="example"></a>Exemplo  
 O código de exemplo a seguir demonstra como adicionar um ponto final WCF compatível com ASP.NET clientes de serviço web em código e, alternativamente, em arquivos de configuração.  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>Confira também

- [Como criar um ponto de extremidade de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [Como publicar metadados utilizando código para um serviço](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [Como especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Como criar um ponto de extremidade de serviço em configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Como publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Utilizando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
