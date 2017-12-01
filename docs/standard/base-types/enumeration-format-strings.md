---
title: "Cadeias de caracteres de formato de enumeração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0992d8591711073f9094c29fad980a8e652e686
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="enumeration-format-strings"></a>Cadeias de caracteres de formato de enumeração
Você pode usar o <xref:System.Enum.ToString%2A?displayProperty=nameWithType> método para criar um novo objeto de cadeia de caracteres que representa o numérico, hexadecimal ou valor de cadeia de caracteres de um membro de enumeração. Esse método usa uma das cadeias de caracteres de formatação de enumeração para especificar o valor que você deseja que seja retornado.  
  
 A tabela a seguir lista a cadeias de caracteres e os valores que elas retornam de formatação de enumeração. Esses especificadores de formato não diferenciam maiúsculas de minúsculas.  
  
| Cadeia de caracteres de formato | Resultado |  
| ------------- | ------ |  
| "G" ou "g" | Exibe a entrada de enumeração como um valor de cadeia de caracteres, se possível e caso contrário, exibe o valor de inteiro da instância atual. Se a enumeração está definida com o **sinalizadores** atributo definido, a cadeia de caracteres de valores de cada entrada válida são concatenados, separados por vírgulas. Se o **sinalizadores** atributo não for definido, um valor inválido é exibido como uma entrada numérica. O exemplo a seguir ilustra o especificador de formato G.<br><br>[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)] |  
| F ou f | Exibe a entrada de enumeração como um valor de cadeia de caracteres, se possível. Se o valor pode ser totalmente exibido como uma soma das entradas na enumeração (mesmo se o **sinalizadores** atributo não estiver presente), os valores de cadeia de caracteres de cada entrada válida são concatenados, separados por vírgulas. Se não puder ser determinado completamente pelas entradas de enumeração, o valor será formatado como valor inteiro. O exemplo a seguir ilustra o especificador de formato F.<br><br>[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)] |  
| D ou d | Exibe a entrada de enumeração como um valor inteiro na representação mais curta possível. O exemplo a seguir ilustra o especificador de formato D.<br><br>[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)] |  
| "X" ou "x" | Exibe a entrada de enumeração como um valor hexadecimal. O valor é representado com zeros no início, conforme necessário, para garantir tenha no mínimo oito dígitos de comprimento. O exemplo a seguir ilustra o especificador de formato X.<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)] |  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma enumeração chamada `Colors`, que consiste em três entradas: `Red`, `Blue` e `Green`.  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 Após a enumeração ser definida, uma instância pode ser declarada da seguinte maneira.  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 O método `Color.ToString(System.String)` pode, então, ser usado para exibir o valor da enumeração de diferentes maneiras, dependendo do especificador de formato passado para ele.  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)
