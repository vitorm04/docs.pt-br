---
title: Cadeias de caracteres de formato de enumeração – .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4f2a8fc10d2aad6b2d43bf128697e86aa73c411
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644674"
---
# <a name="enumeration-format-strings"></a>Cadeias de caracteres de formato de enumeração

Você pode usar o método <xref:System.Enum.ToString%2A?displayProperty=nameWithType> para criar um novo objeto de cadeia de caracteres que representa o valor numérico, hexadecimal ou de cadeia de caracteres de um membro da enumeração. Esse método usa uma das cadeias de caracteres de formatação de enumeração para especificar o valor que você deseja que seja retornado.

As seções a seguir listam as cadeias de caracteres de formatação de enumeração e os valores que elas retornam. Esses especificadores de formato não diferenciam maiúsculas de minúsculas.

## <a name="g-or-g"></a>"G" ou "g"

Exibem a entrada de enumeração como um valor de cadeia de caracteres. Caso contrário, é exibido o valor inteiro da instância atual. Se a enumeração for definida com o atributo **Flags** definido, os valores da cadeia de caracteres de cada entrada válida serão concatenados, separados por vírgulas. Se o atributo **Flags** não estiver definido, um valor inválido será exibido como uma entrada numérica. O exemplo a seguir ilustra o especificador de formato G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F ou f

Exibem a entrada de enumeração como um valor de cadeia de caracteres, se possível. Se o valor puder ser exibido totalmente como uma soma das entradas na enumeração (mesmo que o atributo **Flags** não esteja presente), os valores da cadeia de caracteres de cada entrada válida serão concatenados, separados por vírgulas. Se não puder ser determinado completamente pelas entradas de enumeração, o valor será formatado como valor inteiro. O exemplo a seguir ilustra o especificador de formato F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D ou d

Exibem a entrada de enumeração como um valor inteiro na representação mais curta possível. O exemplo a seguir ilustra o especificador de formato D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>"X" ou "x"

Exibe a entrada de enumeração como um valor hexadecimal. O valor é representado com zeros no início, conforme necessário, para garantir tenha no mínimo oito dígitos de comprimento. O exemplo a seguir ilustra o especificador de formato X.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Exemplo

O exemplo a seguir define uma enumeração chamada `Colors`, que consiste em três entradas: `Red`, `Blue` e `Green`.

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Após a enumeração ser definida, uma instância pode ser declarada da seguinte maneira.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

O método `Color.ToString(System.String)` pode, então, ser usado para exibir o valor da enumeração de diferentes maneiras, dependendo do especificador de formato passado para ele.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Consulte também

- [Formatando Tipos](formatting-types.md)
