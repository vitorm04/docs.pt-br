---
title: "Contratos de dados compatíveis por encaminhamento"
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
helpviewer_keywords: data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef25e349ca6245ff3247f3a136d9a950d03d81d5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="forward-compatible-data-contracts"></a>Contratos de dados compatíveis por encaminhamento
Um recurso do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sistema de contrato de dados é que os contratos podem evoluir ao longo do tempo maneiras incondicional. Ou seja, um cliente com uma versão mais antiga de um contrato de dados pode se comunicar com um serviço com uma versão mais recente do mesmo contrato de dados, ou um cliente com uma versão mais recente de um contrato de dados pode se comunicar com uma versão mais antiga do mesmo contrato de dados. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Práticas recomendadas: controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Você pode aplicar a maioria dos recursos do controle de versão como necessário quando são criadas novas versões de um contrato de dados existente. No entanto, um recurso de controle de versão, *ciclo*, devem ser criados para o tipo da primeira versão para funcionar adequadamente.  
  
## <a name="round-tripping"></a>Ciclo  
 Ciclo ocorre quando dados passam de uma nova versão para uma versão antiga e voltar para a nova versão de um contrato de dados. Ciclo garante que nenhum dado será perdido. Habilitar o ciclo faz com o tipo que compatíveis por encaminhamento com alterações futuras com suporte pelo modelo de controle de versão do contrato de dados.  
  
 Para habilitar o ciclo de um determinado tipo, o tipo deve implementar o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface. A interface contém uma propriedade, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (retornando o <xref:System.Runtime.Serialization.ExtensionDataObject> tipo). A propriedade armazena todos os dados das versões futuras do contrato de dados é desconhecido para a versão atual.  
  
### <a name="example"></a>Exemplo  
 O contrato de dados a seguir não é compatível com a avanço com alterações futuras.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Para tornar o tipo compatível com as alterações futuras (como adicionar um novo membro de dados denominado "phoneNumber"), implemente o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Quando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura encontra dados que não faz parte do contrato de dados original, os dados são armazenados na propriedade e preservados. Ela não é processada de forma alguma, exceto o armazenamento temporário. Se o objeto é retornado para origem, os dados originais (desconhecidos) também são retornados. Portanto, os dados fez uma viagem de ida e de e para o ponto de extremidade de origem sem perda. No entanto, observe que, se o ponto de extremidade de origem necessário os dados a serem processados, essa expectativa é não atendida, e o ponto de extremidade deve detectar e acomodar a alteração de alguma forma.  
  
 O <xref:System.Runtime.Serialization.ExtensionDataObject> tipo não contém métodos públicos ou propriedades. Portanto, é impossível obter acesso direto aos dados armazenados dentro de <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> propriedade.  
  
 O ciclo recurso pode ser desativado, definindo `ignoreExtensionDataObject` para `true` no <xref:System.Runtime.Serialization.DataContractSerializer> construtor ou definindo o <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> propriedade `true` no <xref:System.ServiceModel.ServiceBehaviorAttribute>. Quando esse recurso está desativado, o desserializador não populará o <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> propriedade e o serializador não emitirá o conteúdo da propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [Controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Best Practices: Data Contract Versioning](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md) 
(Práticas recomendadas: controle de versão de contrato de dados)
