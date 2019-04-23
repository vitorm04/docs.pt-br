---
title: Valores padrões de membro de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: 2d323566aa211ced9ed76302756ed5dc82c5d2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973714"
---
# <a name="data-member-default-values"></a>Valores padrões de membro de dados
No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], tipos têm um conceito de *valores padrão*. Por exemplo, para qualquer tipo de referência, o valor padrão é `null`, e para um tipo inteiro é zero. É desejável, ocasionalmente, para omitir um membro de dados dos dados serializados quando ela é definida como seu valor padrão. Como o membro tem um valor padrão, um valor real não precisa ser serializado; Isso tem uma vantagem de desempenho.  
  
 Para omitir um membro de dados serializados, defina a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> atributo `false` (o padrão é `true`).  
  
> [!NOTE]
>  Você deve definir a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade para `false` se houver uma necessidade específica para fazer isso, por exemplo, para interoperabilidade ou dados redução de tamanho.  
  
## <a name="example"></a>Exemplo  
 O código a seguir tem vários membros com o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> definido como `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Se uma instância dessa classe é serializada, o resultado é da seguinte maneira: `employeeName` e `employeeID` é serializado. O valor nulo para `employeeName` e o valor zero para `employeeID` explicitamente faz parte dos dados serializados. No entanto, o `position`, `salary`, e `bonus` membros não são serializados. Por fim, `targetSalary` é serializado como de costume, mesmo que o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> estiver definida como `false`, pois 57800 não coincide com o valor de padrão do .NET para um inteiro, que é zero.  
  
### <a name="xml-representation"></a>Representação XML  
 Se o exemplo anterior é serializado para XML, a representação é semelhante ao seguinte.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 O `xsi:nil` é um atributo especial no namespace de instância do esquema de XML do World Wide Web Consortium (W3C) que fornece uma maneira interoperável para representar explicitamente um valor nulo. Observe que não há nenhuma informação em todos os no XML sobre membros de dados de posição, salário e comissão. A extremidade de recebimento pode interpretar como `null`, zero, e `null`, respectivamente. Não há nenhuma garantia de que um desserializador de terceiros pode tornar a interpretação correta, por isso, esse padrão não é recomendado. O <xref:System.Runtime.Serialization.DataContractSerializer> classe sempre seleciona a interpretação correta para valores ausentes.  
  
### <a name="interaction-with-isrequired"></a>Interação com IsRequired  
 Conforme discutido em [controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo tem um <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade (o padrão é `false`). A propriedade indica se um membro de dados fornecido deve ser presente nos dados serializados quando ele está sendo desserializado. Se `IsRequired` é definido como `true`, (que indica que um valor deve estar presente) e <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> é definido como `false` (indicando que o valor não deve estar presente se ele for definido como seu valor padrão), os valores padrão para este membro de dados não podem ser serializado, pois os resultados seriam contraditórios. Se esse membro de dados é definido como seu valor padrão (normalmente `null` ou zero) e uma serialização é tentada, uma <xref:System.Runtime.Serialization.SerializationException> é gerada.  
  
### <a name="schema-representation"></a>Representação de esquema  
 Os detalhes de que a representação de esquema XSD (linguagem) de definição do esquema XML de membros de dados quando o `EmitDefaultValue` estiver definida como `false` são discutidos em [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). No entanto, veja a seguir uma breve visão geral:  
  
-   Quando o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> é definido como `false`, ela é representada no esquema como uma anotação específica para o Windows Communication Foundation (WCF). Não há nenhuma maneira interoperável para representar essas informações. Em particular, o atributo "default" no esquema não é usado para essa finalidade, o `minOccurs` atributo será afetado somente pela <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> definindo e o `nillable` atributo é afetado somente por tipo de membro de dados.  
  
-   O valor padrão real a ser usado não está presente no esquema. É até o ponto de extremidade de recebimento para interpretar corretamente um elemento ausente.  
  
 Na importação de esquema, o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade é definida automaticamente como `false` sempre que a anotação específicas do WCF mencionada anteriormente é detectada. Ele também é definido como `false` para tipos de referência que têm o `nillable` propriedade definida como `false` para dar suporte a cenários específicos de interoperabilidade que costumam ocorrerem durante o consumo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
