---
title: Nomes de contrato de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: cd878452f3ec99627507334a26873a004e5b5314
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072515"
---
# <a name="data-contract-names"></a>Nomes de contrato de dados

Às vezes, um cliente e um serviço não compartilham os mesmos tipos. Eles ainda podem passar dados entre si, desde que os contratos de dados são equivalentes em ambos os lados. [Equivalência de contrato de dados](data-contract-equivalence.md) é baseado no contrato de dados e nomes de membro de dados, e, portanto, um mecanismo é fornecido para mapear tipos e membros para esses nomes. Este tópico explica as regras de nomenclatura de contratos de dados, bem como o comportamento padrão da infraestrutura do Windows Communication Foundation (WCF) durante a criação de nomes.

## <a name="basic-rules"></a>Regras básicas
Regras básicas em relação à nomenclatura dados contratos incluem:

- Um nome de contrato de dados totalmente qualificado consiste em um namespace e um nome.

- Membros de dados tem apenas nomes, mas nenhum namespace.

- Durante o processamento de contratos de dados, a infraestrutura do WCF é diferencia maiusculas de minúsculas para os namespaces e os nomes dos contratos de dados e os membros de dados.

## <a name="data-contract-namespaces"></a>Namespaces de contrato de dados
Um namespace de contrato de dados assume a forma de um identificador de URI (Uniform Resource). O URI pode ser absoluto ou relativo. Por padrão, os contratos de dados para um tipo específico são atribuídos a um namespace que o namespace do common language runtime (CLR) desse tipo é proveniente.

Por padrão, qualquer dado namespace CLR (no formato *Clr.Namespace*) é mapeado para o namespace `http://schemas.datacontract.org/2004/07/Clr.Namespace`. Para substituir esse padrão, aplique o <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atributo ao assembly ou módulo inteiro. Como alternativa, para controlar o namespace de contrato de dados para cada tipo, defina as <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> propriedade do <xref:System.Runtime.Serialization.DataContractAttribute>.

> [!NOTE]
> O `http://schemas.microsoft.com/2003/10/Serialization` namespace é reservado e não pode ser usado como um namespace de contrato de dados.

> [!NOTE]
> Você não pode substituir o namespace padrão em tipos de contrato de dados que contêm `delegate` declarações.

## <a name="data-contract-names"></a>Nomes de contrato de dados
O nome padrão de um contrato de dados para um determinado tipo é o nome desse tipo. Para substituir o padrão, defina as <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade do <xref:System.Runtime.Serialization.DataContractAttribute> para um nome alternativo. Regras especiais para tipos genéricos são descritas em "Dados de contrato de nomes para tipos genéricos" neste tópico.

## <a name="data-member-names"></a>Nomes de membro de dados
O nome padrão de um membro de dados para um determinado campo ou propriedade é o nome desse campo ou propriedade. Para substituir o padrão, defina as <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> para um valor alternativo.

### <a name="examples"></a>Exemplos
O exemplo a seguir mostra como você pode substituir o comportamento de contratos de dados e os membros de dados de nomenclatura padrão.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Nomes de contrato de dados para tipos genéricos
Existem regras especiais para determinar os nomes de contrato de dados para tipos genéricos. Essas regras ajudam a evitar conflitos de nome de contrato de dados entre dois genéricos fechados do mesmo tipo genérico.

Por padrão, nome do contrato de dados para um tipo genérico é o nome do tipo, seguido pela cadeia de caracteres "De", seguido pelos nomes de contrato de dados dos parâmetros genéricos, seguidos por um *hash* calculada usando os namespaces de contrato de dados do os parâmetros genéricos. Um hash é o resultado de uma função matemática que atua como uma "impressão digital" que identifica exclusivamente uma parte dos dados. Quando todos os parâmetros genéricos forem tipos primitivos, o hash é omitido.

Por exemplo, consulte os tipos no exemplo a seguir.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

Neste exemplo, o tipo `Drawing<Square,RegularRedBrush>` tem o nome do contrato de dados "DrawingOfSquareRedBrush5HWGAU6h", onde "5HWGAU6h" é um hash de namespaces "urn: formas" e "urn: default". O tipo `Drawing<Square,SpecialRedBrush>` tem o nome do contrato de dados "DrawingOfSquareRedBrushjpB5LgQ_S", onde "jpB5LgQ_S" é um hash de "urn: formas" e os namespaces "urn: especial". Observe que se o hash não for usado, os dois nomes são idênticos e, portanto, uma colisão de nome ocorre.

## <a name="customizing-data-contract-names-for-generic-types"></a>Personalizando nomes de contrato de dados para tipos genéricos

Às vezes, os nomes de contrato de dados gerados para tipos genéricos, como descrito anteriormente, são inaceitáveis. Por exemplo, você pode saber com antecedência que você não será executado em colisões de nome e talvez queira remover o hash. Nesse caso, você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade do `DataContractAttribute` atributo para especificar o outra maneira de gerar nomes. Você pode usar números entre chaves dentro do `Name` propriedade para se referir aos dados e nomes de contrato de parâmetros genéricos. (0 se refere ao primeiro parâmetro, 1 refere-se ao segundo e assim por diante). Você pode usar uma cerquilha (#) dentro das chaves para se referir ao hash. Você pode usar cada uma dessas referências várias vezes ou não de forma alguma.

Por exemplo, anterior genérico `Drawing` tipo poderia ter sido declarado como mostrado no exemplo a seguir.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

Nesse caso, o tipo `Drawing<Square,RegularRedBrush>` tem o nome do contrato de dados "Drawing_using_RedBrush_brush_and_Square_shape". Observe que, como há um "{#}" no <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade, o hash não é uma parte do nome e, portanto, o tipo é suscetível a nomenclatura colisões; por exemplo, o tipo `Drawing<Square,SpecialRedBrush>` teria exatamente o mesmo nome de contrato de dados.

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Usando contratos de dados](using-data-contracts.md)
- [Equivalência de contrato de dados](data-contract-equivalence.md)
- [Nomes de contrato de dados](data-contract-names.md)
- [Controle de versão de contrato de dados](data-contract-versioning.md)