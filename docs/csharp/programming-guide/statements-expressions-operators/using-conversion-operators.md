---
title: Usando operadores de conversão – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 888339661ba1cb2e0b702f284d9f27b3217e74c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973152"
---
# <a name="using-conversion-operators-c-programming-guide"></a>Usando operadores de conversão (Guia de Programação em C#)
É possível usar operadores de conversão `implicit`, que são mais fáceis de usar ou operadores de conversão `explicit`, que indicam claramente para alguém que lê o código que você está convertendo um tipo. Este tópico demonstra os dois os tipos de operador de conversão.  
  
> [!NOTE]
>  Para obter informações sobre conversões de tipo simples, confira [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md) ou <xref:System.Convert>.  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de um operador de conversão explícita. Este operador converte do tipo <xref:System.Byte> em um tipo de valor denominado `Digit`. Como nem todos os bytes podem ser convertidos em um dígito, a conversão é explícita, o que significa que uma conversão deve ser usada, conforme mostrado no método `Main`.  
  
 [!code-csharp[csProgGuideStatements#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#11)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo demonstra um operador de conversão implícita definindo um operador de conversão que desfaz o que o exemplo anterior fez: converte de uma classe de valor chamada `Digit` no tipo <xref:System.Byte> integral. Como qualquer dígito pode ser convertido em um <xref:System.Byte>, não há necessidade de forçar os usuários a serem explícitos com relação à conversão.  
  
 [!code-csharp[csProgGuideStatements#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#12)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
- [is](../../../csharp/language-reference/keywords/is.md)
