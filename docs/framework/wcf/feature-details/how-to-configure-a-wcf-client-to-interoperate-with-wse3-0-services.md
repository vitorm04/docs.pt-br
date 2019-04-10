---
title: 'Como: configurar um cliente do WCF para interoperar com serviços WSE3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 62642651516274a27c44abfc19e94dc529690ea9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304539"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Como: configurar um cliente do WCF para interoperar com serviços WSE3.0
Os clientes do Windows Communication Foundation (WCF) são compatíveis com o nível de transmissão com Web Services aprimoramentos 3.0 para serviços do Microsoft .NET (WSE) quando os clientes do WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Para configurar um cliente WCF para interoperar com um serviço Web do WSE 3.0  
  
1. Execute o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um cliente WCF para o serviço Web do WSE 3.0.  
  
     Para um serviço Web do WSE, uma classe de cliente do WCF é criada.  
  
     Para obter detalhes sobre a criação de um cliente do WCF, consulte o [como: Criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2. Crie uma classe que representa uma associação que pode se comunicar com os serviços Web do WSE 3.0.  
  
     A classe a seguir faz parte dos [interoperação com WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) exemplo.  
  
    1.  Crie uma classe que derive da classe <xref:System.ServiceModel.Channels.Binding>.  
  
         O exemplo de código a seguir cria uma classe chamada `WseHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding> classe.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Adicione propriedades à classe que especificam a asserção pronta para uso do WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem.  
  
         O exemplo de código a seguir define o `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, e `MessageProtectionOrder` propriedades. Eles especificam a asserção pronta para uso do WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem, respectivamente.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Substituir o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método para definir as propriedades de associação.  
  
         O exemplo de código a seguir especifica o transporte, codificação de mensagem e as configurações de proteção de mensagem obtendo os valores de `SecurityAssertion` e `MessageProtectionOrder` propriedades.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. No código do aplicativo cliente, adicione código para definir as propriedades de associação.  
  
     O exemplo de código a seguir especifica que o cliente do WCF deve usar autenticação e proteção de mensagem, conforme definido pelo WSE 3.0 `AnonymousForCertificate` asserção de segurança pronta para uso. Além disso, sessões seguras e as chaves derivadas são necessárias.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define uma associação personalizada que expõe propriedades que correspondem às propriedades de uma asserção de segurança pronta para uso do WSE 3.0. A associação personalizada, que é chamada `WseHttpBinding`, em seguida, é usado para especificar as propriedades de associação para um cliente WCF.  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.Binding>
- [Interoperação com WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
