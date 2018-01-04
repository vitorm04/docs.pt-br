---
title: "Como criar um contrato de dados básicos para uma classe ou estrutura"
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
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6241df0fd5a0b6ee532691eee2279f618be25a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Como criar um contrato de dados básicos para uma classe ou estrutura
Este tópico mostra as etapas básicas para criar um contrato de dados usando uma classe ou estrutura. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contratos de dados e como eles são usados, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Para obter um tutorial que percorra as etapas de criação de um basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço e cliente, consulte o [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md). Para um aplicativo de exemplo de trabalho que consiste em um serviço básico e o cliente, consulte [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Para criar um contrato de dados básicos para uma classe ou estrutura  
  
1.  Declare o tipo tem um contrato de dados, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> para a classe de atributo. Observe que todos os tipos públicos, incluindo aqueles sem atributos, são serializáveis. O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo está ausente. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Definir os membros (propriedades, campos ou eventos) que são serializados aplicando o <xref:System.Runtime.Serialization.DataMemberAttribute> a cada membro de atributo. Esses membros são chamados de membros de dados. Por padrão, todos os tipos públicos são serializáveis. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo campos particulares, fazendo com que os dados sejam expostos a outras pessoas. Certifique-se de que o membro não contém dados confidenciais.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um contrato de dados para o `Person` tipo aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para a classe e seus membros.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md)
