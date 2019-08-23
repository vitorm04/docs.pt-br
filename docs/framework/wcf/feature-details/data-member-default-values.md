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
ms.openlocfilehash: 17e73ab2aa777ae53f31596fa364a4feac297842
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962923"
---
# <a name="data-member-default-values"></a>Valores padrões de membro de dados
No .NET Framework, os tipos têm um conceito de *valores padrão*. Por exemplo, para qualquer tipo de referência, o valor `null`padrão é e para um tipo inteiro, ele é zero. Ocasionalmente, é desejável omitir um membro de dados de dados serializados quando ele é definido como seu valor padrão. Como o membro tem um valor padrão, um valor real não precisa ser serializado; Isso tem uma vantagem de desempenho.  
  
 Para omitir um membro de dados serializados, <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> defina a propriedade <xref:System.Runtime.Serialization.DataMemberAttribute> do atributo `false` como (o padrão `true`é).  
  
> [!NOTE]
> Você deve definir a <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> Propriedade como `false` se houver uma necessidade específica para fazer isso, como para interoperabilidade ou redução de tamanho de dados.  
  
## <a name="example"></a>Exemplo  
 O código a seguir tem vários membros com <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> o conjunto `false`para.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Se uma instância dessa classe for serializada, o resultado será o seguinte: `employeeName` e `employeeID` será serializado. O valor nulo para `employeeName` e o valor zero para `employeeID` o é explicitamente parte dos dados serializados. No entanto `position`, `salary`os membros `bonus` , e não são serializados. Por fim `targetSalary` , é serializado como de costume, embora <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a propriedade esteja definida `false`como, porque 57800 não corresponde ao valor padrão do .net para um inteiro, que é zero.  
  
### <a name="xml-representation"></a>Representação XML  
 Se o exemplo anterior for serializado em XML, a representação será semelhante à seguinte.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 O `xsi:nil` atributo é um atributo especial no namespace de instância de esquema XML World Wide Web Consortium (W3C) que fornece uma maneira interoperável para representar explicitamente um valor nulo. Observe que não há nenhuma informação no XML sobre a posição, o salário e os membros dos dados de bônus. A extremidade de recebimento pode interpretá `null`-los como, `null`zero e, respectivamente. Não há nenhuma garantia de que um desserializador de terceiros possa fazer a interpretação correta, motivo pelo qual esse padrão não é recomendado. A <xref:System.Runtime.Serialization.DataContractSerializer> classe sempre seleciona a interpretação correta para valores ausentes.  
  
### <a name="interaction-with-isrequired"></a>Interação com IsRequired  
 Conforme discutido no [controle de versão de contrato](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)de <xref:System.Runtime.Serialization.DataMemberAttribute> dados, o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> atributo tem uma propriedade ( `false`o padrão é). A propriedade indica se um determinado membro de dados deve estar presente nos dados serializados quando estiver desserializado. Se `IsRequired` é definido como `true`, (que indica que um valor deve estar presente) e <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> é definido como `false` (indicando que o valor não deve estar presente se for definido como seu valor padrão), os valores padrão para esse membro de dados não podem ser serializado porque os resultados seriam contraditórios. Se esse membro de dados for definido como seu valor padrão (geralmente `null` ou zero) e uma serialização for tentada, um <xref:System.Runtime.Serialization.SerializationException> será gerado.  
  
### <a name="schema-representation"></a>Representação de esquema  
 Os detalhes da representação de esquema XSD (linguagem de definição de esquema XML) de membros de `EmitDefaultValue` dados quando a propriedade `false` é definida como são discutidas na [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). No entanto, veja a seguir uma breve visão geral:  
  
- Quando o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> é definido como `false`, ele é representado no esquema como uma anotação específica para Windows Communication Foundation (WCF). Não há uma maneira interoperável de representar essas informações. Em particular, o atributo "default" no esquema não é usado para essa finalidade, o `minOccurs` atributo é afetado somente <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> pela configuração e o `nillable` atributo é afetado somente pelo tipo do membro de dados.  
  
- O valor padrão real a ser usado não está presente no esquema. Cabe ao ponto de extremidade de recebimento interpretar adequadamente um elemento ausente.  
  
 Na importação de esquema, <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a propriedade é definida automaticamente `false` como sempre que a anotação específica do WCF mencionada anteriormente é detectada. Ele também é definido como `false` para os tipos de referência que `nillable` têm a propriedade `false` definida como para dar suporte a cenários de interoperabilidade específicos que normalmente ocorrem ao consumir serviços Web ASP.net.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
