---
title: Contratos de dados compatíveis por encaminhamento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 732c47b03c2769a6147c3c812ddd6e81dab11a55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695641"
---
# <a name="forward-compatible-data-contracts"></a>Contratos de dados compatíveis por encaminhamento
Um recurso do Windows Communication Foundation (WCF) é o sistema de contrato de dados que contratos pode evoluir ao longo do tempo de maneiras não separáveis. Ou seja, um cliente com uma versão mais antiga de um contrato de dados pode se comunicar com um serviço com uma versão mais recente do mesmo contrato de dados ou um cliente com uma versão mais recente de um contrato de dados pode se comunicar com uma versão anterior do mesmo contrato de dados. Para obter mais informações, consulte [práticas recomendadas: Controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Você pode aplicar a maioria dos recursos de controle de versão em uma base conforme necessário quando novas versões de um contrato de dados existente são criadas. No entanto, um recurso de controle de versão, *ciclo completo*, devem ser compilados no tipo da primeira versão para funcionar corretamente.  
  
## <a name="round-tripping"></a>O ciclo completo  
 Ciclo ocorre quando dados passam de uma nova versão para uma versão antiga e de volta para a nova versão de um contrato de dados. O ciclo completo garante que nenhum dado será perdido. Habilitar o ciclo completo torna ao tipo em compatíveis por encaminhamento com alterações futuras, com suporte pelo modelo de controle de versão do contrato de dados.  
  
 Para habilitar o ciclo completo de um determinado tipo, o tipo deve implementar o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. A interface contém uma propriedade, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (retornando o <xref:System.Runtime.Serialization.ExtensionDataObject> tipo). A propriedade armazena todos os dados das versões futuras do contrato de dados é desconhecido para a versão atual.  
  
### <a name="example"></a>Exemplo  
 O seguinte contrato de dados não é compatíveis por encaminhamento com alterações futuras.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Para tornar o tipo compatível com as alterações futuras (como adicionar um novo membro de dados denominado "phoneNumber"), implemente o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Quando a infraestrutura do WCF encontra dados que não fazem parte do contrato de dados original, os dados são armazenados na propriedade e preservados. Ela não é processada de qualquer outra forma, exceto para armazenamento temporário. Se o objeto é retornado para origem, os dados originais (desconhecidos) também são retornados. Portanto, os dados fez uma viagem de ida e para o ponto de extremidade de origem sem perda. No entanto, observe que, se o ponto de extremidade de origem necessário os dados a serem processados, a expectativa de que é não atendida, e o ponto de extremidade deve detectar e acomodar a alteração de alguma forma.  
  
 O <xref:System.Runtime.Serialization.ExtensionDataObject> tipo não contém métodos públicos ou propriedades. Portanto, é impossível obter acesso direto aos dados armazenados dentro de <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> propriedade.  
  
 O recurso de ciclo completo pode ser desativado, definindo `ignoreExtensionDataObject` para `true` na <xref:System.Runtime.Serialization.DataContractSerializer> construtor ou definindo o <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> propriedade a ser `true` no <xref:System.ServiceModel.ServiceBehaviorAttribute>. Quando esse recurso está desativado, o desserializador não populará o <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> propriedade e o serializador não emitirá o conteúdo da propriedade.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Práticas recomendadas: Controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
