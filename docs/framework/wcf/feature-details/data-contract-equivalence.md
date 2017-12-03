---
title: "Equivalência de contrato de dados"
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
helpviewer_keywords: data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7367cabecc18f32860e0a391ce5cf48d54503dc6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-equivalence"></a>Equivalência de contrato de dados
Para um cliente enviar dados de um determinado tipo com êxito a um serviço ou um serviço para enviar dados com êxito a um cliente, o tipo de envio não necessariamente precisa existir na extremidade de recebimento. O único requisito é que os contratos de ambos os tipos de dados ser equivalentes. (Às vezes, equivalência estrita não é necessária, conforme discutido em [controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Para contratos de dados sejam equivalentes, eles devem ter o mesmo namespace e nome. Além disso, cada membro de dados em um lado deve ter um membro de dados equivalentes no outro lado.  
  
 Para membros de dados sejam equivalentes, eles devem ter o mesmo nome. Além disso, eles devem representar o mesmo tipo de dados. Isto é, seus contratos de dados devem ser equivalentes.  
  
> [!NOTE]
>  Observação de contrato de dados nomes e namespaces, bem como nomes de membros de dados diferenciam maiusculas de minúsculas.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]namespaces e nomes de contrato de dados, bem como os nomes de membros de dados, consulte [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Se existem dois tipos no mesmo lado (remetente ou destinatário) e seus contratos de dados não são equivalentes (por exemplo, eles têm membros de dados diferente), você deve não lhes o mesmo nome e namespace. Isso pode causar exceções sejam geradas.  
  
 Os contratos para os seguintes tipos de dados são equivalentes:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Equivalência de contrato de dados e de ordem de membro de dados  
 Usando o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> classe pode afetar a equivalência de contrato de dados. Os contratos de dados devem ter membros que aparecem na mesma ordem como equivalente. A ordem padrão é alfabética. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Por exemplo, o código a seguir resulta em contratos de dados equivalentes.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 No entanto, o seguinte não resulta em um contrato de dados equivalente.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Equivalência de contrato de dados, Interfaces e herança  
 Ao determinar a equivalência, um contrato de dados que herda de outro contrato de dados é tratado como se fosse um contrato de dados que inclui todos os membros de dados do tipo base. Tenha em mente que a ordem dos membros de dados deve corresponder e precedem por membros do tipo base derivadas membros de tipo na ordem. Além disso, se, como no exemplo de código a seguir, os membros de dados têm o mesmo valor de ordem, a ordenação para os membros de dados está em ordem alfabética. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 No exemplo a seguir, o contrato de dados para o tipo `Employee` é equivalente ao contrato de dados para o tipo de `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Ao passar parâmetros e valores de retorno entre um cliente e um serviço, um contrato de dados de uma classe base não será enviado quando o ponto de extremidade receptor espera um contrato de dados de uma classe derivada. Isso está de acordo com princípios de programação orientada a objeto. No exemplo anterior, um objeto do tipo `Person` não pode ser enviada quando um `Employee` é esperado.  
  
 Um contrato de dados de uma classe derivada pode ser enviado quando um contrato de dados de uma classe base é esperado, mas somente se o ponto de extremidade de recebimento "sabe" do tipo derivado usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). No exemplo anterior, um objeto do tipo `Employee` podem ser enviadas quando um `Person` é esperado, mas somente se o código receptor emprega o <xref:System.Runtime.Serialization.KnownTypeAttribute> para incluí-lo na lista de tipos conhecidos.  
  
 Ao passar parâmetros e valores de retorno entre aplicativos, se o tipo esperado é uma interface, é equivalente para o tipo esperado sendo do tipo <xref:System.Object>. Como cada tipo, por fim, deriva de <xref:System.Object>, cada contrato de dados, por fim, deriva de contrato de dados para <xref:System.Object>. Portanto, qualquer tipo de contrato de dados pode ser passado quando uma interface é esperada. São necessárias etapas adicionais para trabalhar com êxito com interfaces; Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
