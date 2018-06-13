---
title: Nomes de contrato de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 18ba9aa1f7af3733acd60924d0aa24ceb1b5126c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494264"
---
# <a name="data-contract-names"></a>Nomes de contrato de dados
Às vezes, um cliente e um serviço não compartilham os mesmos tipos. Eles ainda podem passar dados entre si como os contratos de dados são equivalentes em ambos os lados. [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md) é baseado no contrato de dados e nomes de membros de dados, e, portanto, um mecanismo é fornecido para mapear tipos e membros para esses nomes. Este tópico explica as regras de nomeação de contratos de dados, bem como o comportamento padrão da infraestrutura do Windows Communication Foundation (WCF) ao criar nomes.  
  
## <a name="basic-rules"></a>Regras básicas  
 Regras básicas sobre os dados de nomenclatura contratos incluem:  
  
-   Um nome de contrato de dados completo consiste em um namespace e um nome.  
  
-   Membros de dados têm apenas nomes, mas nenhum namespace.  
  
-   Durante o processamento de contratos de dados, a infraestrutura WCF diferencia maiusculas de minúsculas para os namespaces e os nomes dos contratos de dados e os membros de dados.  
  
## <a name="data-contract-namespaces"></a>Namespaces de contrato de dados  
 Um namespace de contrato de dados assume a forma de um URI Uniform Resource Identifier (). O URI pode ser absoluta ou relativa. Por padrão, os contratos de dados para um tipo específico são atribuídos a um namespace que vem do namespace de runtime (CLR) de linguagem comum desse tipo.  
  
 Por padrão, qualquer dado namespace CLR (no formato *Clr.Namespace*) é mapeado para o namespace "http://schemas.datacontract.org/2004/07/Clr.Namespace". Para substituir esse padrão, se aplicam a <xref:System.Runtime.Serialization.ContractNamespaceAttribute> de atributo para o assembly ou módulo inteiro. Como alternativa, para controlar o namespace de contrato de dados para cada tipo, defina o <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> propriedade o <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
> [!NOTE]
>  O "http://schemas.microsoft.com/2003/10/Serialization"namespace é reservado e não pode ser usado como um namespace de contrato de dados.  
  
> [!NOTE]
>  Você não pode substituir o namespace padrão em tipos de contrato de dados que contêm `delegate` declarações.  
  
## <a name="data-contract-names"></a>Nomes de contrato de dados  
 O nome padrão de um contrato de dados para um determinado tipo é o nome desse tipo. Para substituir o padrão, defina o <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade o <xref:System.Runtime.Serialization.DataContractAttribute> para um nome alternativo. Regras especiais para tipos genéricos são descritas em "Dados contrato nomes para tipos genéricos" neste tópico.  
  
## <a name="data-member-names"></a>Nomes de membros de dados  
 O nome padrão de um membro de dados para um determinado campo ou propriedade é o nome desse campo ou propriedade. Para substituir o padrão, defina o <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> propriedade o <xref:System.Runtime.Serialization.DataMemberAttribute> para um valor alternativo.  
  
### <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra como você pode substituir o comportamento de contratos de dados e os membros de dados de nomenclatura padrão.  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## <a name="data-contract-names-for-generic-types"></a>Nomes de contrato de dados para tipos genéricos  
 Existem regras especiais para determinar os nomes de contrato de dados para tipos genéricos. Essas regras ajudam a evitar conflitos de nome de contrato de dados entre dois genéricos fechados do mesmo tipo genérico.  
  
 Por padrão, nome do contrato de dados para um tipo genérico é o nome do tipo, seguido pela cadeia de caracteres "De", seguido pelos nomes de contrato de dados dos parâmetros genéricos, seguidos por um *hash* calculado usando os namespaces de contrato de dados do os parâmetros genéricos. Um hash é o resultado de uma função matemática que atua como uma "impressão digital" que identifica exclusivamente uma parte dos dados. Quando todos os parâmetros genéricos forem tipos primitivos, o hash é omitido.  
  
 Por exemplo, consulte os tipos no exemplo a seguir.  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 Neste exemplo, o tipo `Drawing<Square,RegularRedBrush>` tem o nome do contrato de dados "DrawingOfSquareRedBrush5HWGAU6h", onde "5HWGAU6h" é um hash de namespaces "urn: formas" e "urn: padrão". O tipo `Drawing<Square,SpecialRedBrush>` tem o nome do contrato de dados "DrawingOfSquareRedBrushjpB5LgQ_S", onde "jpB5LgQ_S" é um hash de "urn: formas" e os namespaces "urn: especial". Observe que se o hash não é usado, os dois nomes são idênticos e, portanto, ocorre a uma colisão de nomes.  
  
## <a name="customizing-data-contract-names-for-generic-types"></a>Personalizando nomes de contrato de dados para tipos genéricos  
 Às vezes, os nomes de contrato de dados gerados para tipos genéricos, como descrito anteriormente, são inaceitáveis. Por exemplo, você pode saber com antecedência que você não será executada em conflitos de nome e remova o hash. Nesse caso, você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade o `DataContractAttribute` atributo para especificar um modo diferente para gerar nomes. Você pode usar números entre chaves dentro do `Name` propriedade para fazer referência a dados e nomes de parâmetros genéricos. (0 refere-se ao primeiro parâmetro, 1 refere-se a segunda e assim por diante). Você pode usar um sinal de número (#) entre chaves para se referir ao hash. Você pode usar cada uma dessas referências várias vezes ou não.  
  
 Por exemplo, o anterior genérico `Drawing` tipo poderia ter sido declarado como mostrado no exemplo a seguir.  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 Nesse caso, o tipo `Drawing<Square,RegularRedBrush>` tem o nome de contrato de dados "Drawing_using_RedBrush_brush_and_Square_shape". Observe que, como há um "{#}" no <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> propriedade, o hash não é uma parte do nome e, portanto, o tipo é suscetível a nomenclatura colisões; por exemplo, o tipo `Drawing<Square,SpecialRedBrush>` tem exatamente o mesmo nome de contrato de dados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
