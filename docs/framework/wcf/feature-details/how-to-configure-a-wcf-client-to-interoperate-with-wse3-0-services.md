---
title: "Como configurar um cliente do WCF para interoperar com serviços WSE3.0"
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
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea71737e1e214aa1a035739901bf79f8ef4a9c7a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>Como configurar um cliente do WCF para interoperar com serviços WSE3.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]os clientes são compatíveis com o nível de transmissão com Web Services aprimoramentos 3.0 para Microsoft .NET (WSE) de serviços quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os clientes são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>Para configurar um cliente WCF para interoperar com um serviço Web do WSE 3.0  
  
1.  Execute o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente para o serviço Web do WSE 3.0.  
  
     Para um serviço Web de WSE, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente é criada.  
  
     Para obter detalhes sobre como criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, consulte o [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Crie uma classe que representa uma associação que pode se comunicar com serviços WSE 3.0 Web.  
  
     A seguinte classe faz parte do [interoperar com WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemplo.  
  
    1.  Crie uma classe que derive da classe <xref:System.ServiceModel.Channels.Binding>.  
  
         O exemplo de código a seguir cria uma classe denominada `WseHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding> classe.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  Adicione propriedades à classe que especificam a declaração completa de WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem.  
  
         O exemplo de código a seguir define `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` propriedades que especificam a declaração completa de WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se confirmações de assinatura são necessárias e as configurações de proteção de mensagem respectivamente.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  Substituir o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método para definir as propriedades de associação.  
  
         O exemplo de código a seguir especifica o transporte, a codificação de mensagem e as configurações de proteção de mensagem, fazendo com que os valores da `SecurityAssertion` e `MessageProtectionOrder` propriedades.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  No código do aplicativo cliente, adicione código para definir as propriedades de associação.  
  
     O exemplo de código a seguir especifica que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente deve usar a autenticação e proteção de mensagem conforme definido pelo WSE 3.0 `AnonymousForCertificate` asserção de segurança completa. Além disso, sessões seguras e chaves derivadas são necessárias.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define uma associação personalizada que expõe propriedades que correspondem às propriedades de uma asserção de segurança completa de WSE 3.0. A associação personalizada, que é chamada de `WseHttpBinding`, é usado para especificar as propriedades de associação para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 [Interoperando com WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
