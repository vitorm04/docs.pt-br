---
title: 'Como: criar um contrato de dados básicos para uma classe ou estrutura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: b46273c468891aa2b18c04adc1ee035c98255ded
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220507"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Como: criar um contrato de dados básicos para uma classe ou estrutura
Este tópico mostra as etapas básicas para criar um contrato de dados usando uma classe ou estrutura. Para obter mais informações sobre contratos de dados e como elas são usadas, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Para obter um tutorial que orienta pelas etapas de criação de um serviço Windows Communication Foundation (WCF) básicas e um cliente, consulte a [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md). Para um aplicativo de exemplo funcional que consiste em um serviço básico e um cliente, consulte [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Para criar um contrato de dados básicos para uma classe ou estrutura  
  
1.  Declare o tipo tem um contrato de dados, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> à classe de atributo. Observe que todos os tipos públicos, incluindo aqueles sem atributos, são serializáveis. O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo estiver ausente. Para obter mais informações, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Definir os membros (propriedades, campos ou eventos) que são serializados, aplicando o <xref:System.Runtime.Serialization.DataMemberAttribute> a cada membro de atributo. Esses membros são chamados de membros de dados. Por padrão, todos os tipos públicos são serializáveis. Para obter mais informações, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> de atributo para campos privados, fazendo com que os dados a ser exposta a outras pessoas. Certifique-se de que o membro não contém dados confidenciais.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um contrato de dados para o `Person` tipo aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para a classe e seus membros.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Guia de introdução ao tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md)
