---
title: "Como personalizar uma associação fornecida pelo sistema"
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
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9b048b5c57d174ac921793ee8677622b88a0595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-system-provided-binding"></a>Como personalizar uma associação fornecida pelo sistema
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]inclui várias associações fornecidas pelo sistema que permitem configurar algumas das propriedades dos elementos de associação subjacente, mas não todas as propriedades. Este tópico demonstra como definir propriedades nos elementos de associação para criar uma associação personalizada.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como criar diretamente e configurar os elementos de associação sem usar as associações fornecidas pelo sistema, consulte [personalizado associações](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Criando e estendendo associações personalizadas, consulte [estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] todas as associações são compostas de *elementos de associação*. Cada elemento de associação derivado de <xref:System.ServiceModel.Channels.BindingElement> classe. Associações fornecidas pelo sistema, como <xref:System.ServiceModel.BasicHttpBinding> criar e configurar seus próprios elementos de associação. Este tópico mostra como acessar e alterar as propriedades desses elementos de associação, que não são diretamente expostos na associação; Especificamente, o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Os elementos de associação individuais estão contidos em uma coleção representada pelo <xref:System.ServiceModel.Channels.BindingElementCollection> de classe e são adicionados nesta ordem: fluxo de transações, sessão confiável, segurança, Duplex compostos, unidirecional, segurança de fluxo, codificação de mensagem e transporte. Observe que nem todos os elementos de associação listados são necessários em cada associação. Elementos de associação definida pelo usuário também podem ser exibido nesta coleção de elemento de associação e devem aparecer na mesma ordem conforme descrito anteriormente. Por exemplo, um transporte definido pelo usuário deve ser o último elemento da coleção de elementos de associação.  
  
 O <xref:System.ServiceModel.BasicHttpBinding> classe contém três elementos de associação:  
  
1.  Um elemento de associação ou opcional de segurança de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> classe usada com o transporte HTTP (segurança em nível de mensagem) ou o <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> classe, que é usado quando a camada de transporte fornece segurança, no caso do transporte HTTPS é usado.  
  
2.  Um codificador de mensagem necessário ou elemento de associação <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ou <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Um transporte necessário ou elemento de associação <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 Neste exemplo, podemos criar uma instância da associação, gerar um *associação personalizada* , examine os elementos de associação na associação personalizada e, ao encontrar o elemento de associação HTTP, vamos definir seu `KeepAliveEnabled` propriedade `false`. O `KeepAliveEnabled` propriedade não é exposta diretamente no `BasicHttpBinding`, portanto, é necessário criar uma associação personalizada para navegar até o elemento de associação e defina essa propriedade.  
  
### <a name="to-modify-a-system-provided-binding"></a>Para modificar uma associação fornecida pelo sistema  
  
1.  Criar uma instância do <xref:System.ServiceModel.BasicHttpBinding> de classe e defina o modo de segurança em nível de mensagem.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Criar uma associação personalizada de associação e criar um <xref:System.ServiceModel.Channels.BindingElementCollection> classe a partir de uma das propriedades da associação personalizada.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Percorra a <xref:System.ServiceModel.Channels.BindingElementCollection> classe, e quando você encontrar o <xref:System.ServiceModel.Channels.HttpTransportBindingElement> classe, defina seu <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> propriedade `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)
