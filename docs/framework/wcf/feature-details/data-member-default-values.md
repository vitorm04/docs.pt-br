---
title: "Valores padrões de membro de dados"
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
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c7d6aa8d695dd6fc79b23e6cbb69bf523ef680f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="data-member-default-values"></a>Valores padrões de membro de dados
No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], tipos têm um conceito de *valores padrão*. Por exemplo, para qualquer tipo de referência, o valor padrão é `null`, e para um tipo inteiro é zero. É recomendável ocasionalmente para omitir um membro de dados serializados dados quando ele é definido como seu valor padrão. Como o membro tem um valor padrão, um valor real não precisa ser serializado; Isso tem uma vantagem de desempenho.  
  
 Para omitir um membro de dados serializados, defina o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo `false` (o padrão é `true`).  
  
> [!NOTE]
>  Você deve definir o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade `false` se houver uma necessidade específica para fazer isso, por exemplo, para interoperabilidade ou dados redução de tamanho.  
  
## <a name="example"></a>Exemplo  
 O código a seguir tem vários membros com o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> definido como `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Se uma instância dessa classe é serializada, o resultado é o seguinte: `employeeName` e `employeeID` é serializado. O valor nulo para `employeeName` e o valor de zero para `employeeID` explicitamente faz parte dos dados serializados. No entanto, o `position`, `salary`, e `bonus` membros não são serializados. Por fim, `targetSalary` é serializado como de costume, mesmo que o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> está definida como `false`, pois 57800 não coincide com o valor padrão de .NET para um inteiro, que é igual a zero.  
  
### <a name="xml-representation"></a>Representação XML  
 Se o exemplo anterior é serializado como XML, a representação é semelhante ao seguinte.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 O `xsi:nil` é um atributo especial no namespace de instância do esquema de XML do World Wide Web Consortium (W3C) que fornece uma maneira interoperável para representar explicitamente um valor nulo. Observe que não há nenhuma informação no XML sobre membros de dados de posição, salário e comissão. Extremidade de recebimento pode interpretar esses como `null`, zero, e `null`, respectivamente. Não há nenhuma garantia de que um desserializador de terceiros pode tornar a interpretação correta, o motivo pelo qual esse padrão não é recomendado. O <xref:System.Runtime.Serialization.DataContractSerializer> classe sempre seleciona a interpretação correta para valores ausentes.  
  
### <a name="interaction-with-isrequired"></a>Interação com IsRequired  
 Conforme discutido em [controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo tem um <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade (o padrão é `false`). A propriedade indica se um membro de dados fornecido deve ser presente nos dados serializados quando ele está sendo desserializado. Se `IsRequired` é definido como `true`, (que indica que um valor deve estar presente) e <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> é definido como `false` (indicando que o valor não deve estar presente se ele for definido como seu valor padrão), os valores padrão para este membro de dados não podem ser serializado, pois os resultados seriam contraditórios. Se esse tipo de membro de dados é definido como seu valor padrão (geralmente `null` ou zero) e uma tentativa de uma serialização, um <xref:System.Runtime.Serialization.SerializationException> é gerada.  
  
### <a name="schema-representation"></a>Representação de esquema  
 Os detalhes da representação de esquema de linguagem XSD de esquema XML definição de membros de dados quando o `EmitDefaultValue` está definida como `false` são discutidos em [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). No entanto, esta é uma breve visão geral:  
  
-   Quando o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> é definido como `false`, ela é representada como uma anotação específica no esquema [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Não há nenhuma maneira interoperável para representar essas informações. Em particular, o atributo "padrão" no esquema não é usado para essa finalidade, o `minOccurs` atributo será afetado somente pelo <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> configuração e o `nillable` atributo é afetado somente pelo tipo de membro de dados.  
  
-   O valor padrão real para usar não está presente no esquema. É até o ponto de extremidade de recebimento interprete corretamente um elemento ausente.  
  
 Na importação de esquema, o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade é definida automaticamente como `false` sempre que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-anotação específica mencionado anteriormente é detectado. Ele também é definido como `false` para tipos de referência que têm o `nillable` propriedade definida como `false` para dar suporte a cenários específicos de interoperabilidade que normalmente ocorrem quando o consumo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>
