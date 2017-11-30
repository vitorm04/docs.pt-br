---
title: "Tipos de enumeração em contratos de dados"
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
helpviewer_keywords: data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea76ae136695ce2dc9eca0a9c7660e4e1ffe547d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enumeration-types-in-data-contracts"></a>Tipos de enumeração em contratos de dados
Enumerações podem ser expressos no modelo de contrato de dados. Este tópico explica vários exemplos que explicam o modelo de programação.  
  
## <a name="enumeration-basics"></a>Noções básicas de enumeração  
 É uma maneira de usar tipos de enumeração no modelo de contrato de dados aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> para o tipo de atributo. Você deve aplicar o <xref:System.Runtime.Serialization.EnumMemberAttribute> de atributo para cada membro que deve ser incluído no contrato de dados.  
  
 O exemplo a seguir mostra duas classes. O primeiro usa a enumeração e o segundo define a enumeração.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Uma instância do `Car` classe pode ser enviada ou recebida apenas se o `condition` campo é definido como um dos valores `New`, `Used`, ou `Rental`. Se o `condition` é `Broken` ou `Stolen`, um <xref:System.Runtime.Serialization.SerializationException> é gerada.  
  
 Você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute> propriedades (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> e <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) como de costume para contratos de dados de enumeração.  
  
### <a name="enumeration-member-values"></a>Valores de membro de enumeração  
 Geralmente, o contrato de dados inclui nomes de membro de enumeração, não os valores numéricos. No entanto, quando usar os dados de contrato de modelo, se o lado de recebimento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, o esquema exportado preserva os valores numéricos. Observe que isso não é o caso ao usar o [usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 No exemplo anterior, se `condition` é definido como `Used` e os dados são serializados em XML, o XML resultante é `<condition>Used</condition>` e não `<condition>1</condition>`. Portanto, o contrato de dados a seguir é equivalente ao contrato de dados de `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Por exemplo, você pode usar `CarConditionEnum` no lado de envio e `CarConditionWithNumbers` no lado de recepção. Embora o lado de envio usa o valor "1" para `Used` e os usos do lado receptor é o valor "20", a representação XML `<condition>Used</condition>` para ambos os lados.  
  
 Para ser incluído no contrato de dados, você deve aplicar o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], você sempre pode aplicar o valor especial 0 (zero) a uma enumeração, que também é o valor padrão para qualquer enumeração. No entanto, até mesmo esse especial que não pode ser serializado valor igual a zero, a menos que ele está marcado com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.  
  
 Há duas exceções a isso:  
  
-   Enumerações de sinalizador (discutidas posteriormente neste tópico).  
  
-   Membros de dados de enumeração com o <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriedade definida como `false` (nesse caso, a enumeração com o valor zero é omitida dos dados serializados).  
  
### <a name="customizing-enumeration-member-values"></a>Personalizando os valores de membro de enumeração  
 Você pode personalizar o valor do membro de enumeração que faz parte do contrato de dados usando o <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> propriedade o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.  
  
 Por exemplo, o seguinte contrato de dados também é equivalente ao contrato de dados do `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Quando serializado, o valor de `PreviouslyOwned` tem a representação XML `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Enumerações simples  
 Você também pode serializar os tipos de enumeração para os quais o <xref:System.Runtime.Serialization.DataContractAttribute> atributo não foi aplicado. Enumeração tipos são tratados exatamente conforme descrito anteriormente, com exceção de que todos os membros (que não tem o <xref:System.NonSerializedAttribute> atributo aplicado) é tratado como se o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo foi aplicado. Por exemplo, a enumeração seguir implicitamente tem um contrato de dados equivalente ao anterior `CarConditionEnum` exemplo.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Você pode usar enumerações simples quando você não precisa personalizar o nome do contrato de dados da enumeração e namespace e os valores de membro de enumeração.  
  
#### <a name="notes-on-simple-enumerations"></a>Observações sobre enumerações simples  
 Aplicar o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo para enumerações simples não tem nenhum efeito.  
  
 Não faz diferença ou não o <xref:System.SerializableAttribute> atributo é aplicado a enumeração.  
  
 O fato de que o <xref:System.Runtime.Serialization.DataContractSerializer> classe segue o <xref:System.NonSerializedAttribute> atributo aplicado a membros de enumeração é diferente do comportamento do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Ambos esses serializadores ignorar o <xref:System.NonSerializedAttribute> atributo.  
  
## <a name="flag-enumerations"></a>Enumerações de sinalizador  
 Você pode aplicar o <xref:System.FlagsAttribute> de atributo para enumerações. Nesse caso, uma lista de valores de enumeração de zero ou mais pode ser enviada ou recebida simultaneamente.  
  
 Para fazer isso, se aplicam a <xref:System.Runtime.Serialization.DataContractAttribute> de atributos para a enumeração de sinalizador e, em seguida, marcar todos os membros que são potências de dois com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo. Observe que, para usar uma enumeração de sinalizador, o andamento deve ser uma sequência ininterrupta de potências de 2 (por exemplo, 1, 2, 4, 8, 16, 32, 64).  
  
 As etapas a seguir se aplicam ao valor de enumeração do sinalizador de envio:  
  
1.  Tentativa de encontrar um membro de enumeração (com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo aplicado) que mapeia para o valor numérico. Se encontrado, enviar uma lista que contém apenas esse membro.  
  
2.  Tentativa de dividir o valor numérico em uma soma, pois há membros de enumeração (cada um com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo aplicado) que mapeiam para cada parte da soma. Envie a lista de todos esses membros. Observe que o *algoritmo greedy* é usado para localizar a soma, e, portanto, não há nenhuma garantia de que, como a soma é encontrada, mesmo se ele estiver presente. Para evitar esse problema, certifique-se de que os valores numéricos dos membros de enumeração são potências de dois.  
  
3.  Se as duas etapas anteriores falharem e o valor numérico é diferente de zero, gerar um <xref:System.Runtime.Serialization.SerializationException>. Se o valor numérico é zero, envie uma lista vazia.  
  
### <a name="example"></a>Exemplo  
 O seguinte exemplo de enumeração pode ser usado em uma operação de sinalizador.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Os valores de exemplo a seguir são serializados como indicado.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Especificando transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
