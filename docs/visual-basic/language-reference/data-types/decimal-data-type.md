---
title: Tipo de dados decimal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a>Tipo de dados decimal (Visual Basic)
Mantém conectado 128 bits (16 bytes) valores que representam números de 96 bits (12 bytes) inteiro dimensionados por uma potência variável de 10. O fator de escala especifica o número de dígitos à direita da vírgula decimal. ele varia de 0 a 28. Com uma escala de 0 (sem casas decimais), o maior valor possível é + /-79.228.162.514.264.337.593.543.950.335 (+ /-7 .9228162514264337593543950335E + 28). Com 28 casas decimais, o maior valor é + /-7.9228162514264337593543950335 e o menor valor diferente de zero é + /-0,0000000000000000000000000001 (+ /-1E-28).  
  
## <a name="remarks"></a>Comentários  
 O `Decimal` tipo de dados fornece o maior número de dígitos significativos para um número. Ele oferece suporte a até 29 dígitos significativos e pode representar valores além 7.9228 x 10 ^ 28. Ele é especialmente adequado para cálculos, como financeiros, que exigem um grande número de dígitos, mas não puder tolerar erros de arredondamento.  
  
 O valor padrão de `Decimal` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Precisão.** `Decimal`não é um tipo de dados de ponto flutuante. O `Decimal` estrutura contém um valor inteiro binário, junto com um bit de sinal e um número inteiro que especifica qual parte do valor é uma fração decimal fator de escala. Por isso, `Decimal` números têm uma representação mais precisa na memória que tipos de ponto flutuantes (`Single` e `Double`).  
  
-   **Desempenho.** O `Decimal` tipo de dados é o mais lento de todos os tipos numéricos. Você deve avaliar a importância da precisão contra o desempenho antes de escolher um tipo de dados.  
  
-   **Ampliação.** O `Decimal` tipo de dados amplia a `Single` ou `Double`. Isso significa que você pode converter `Decimal` para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
-   **Zeros à direita.** Visual Basic não armazena zeros à direita em um `Decimal` literal. No entanto, um `Decimal` variable preserva os zeros à direita adquiridos computacionalmente. O exemplo a seguir ilustra essa situação.  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     A saída de `MsgBox` no exemplo anterior é da seguinte maneira:  
  
     D1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `D` a um literal o força ao tipo de dados `Decimal`. Acrescentar o caractere de tipo identificador `@` a qualquer identificador o força ao tipo `Decimal`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Decimal?displayProperty=nameWithType>.  
  
## <a name="range"></a>Intervalo  
 Talvez seja necessário usar o `D` tipo de caractere para atribuir um valor grande para uma `Decimal` variável ou constante. Esse requisito é porque o compilador interpreta um literal como `Long` , a menos que um caractere de tipo literal literal, como mostra o exemplo a seguir.  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 A declaração `bigDec1` não produz um estouro porque o valor que é atribuído a ela fica dentro do intervalo de `Long`. O `Long` valor pode ser atribuído para o `Decimal` variável.  
  
 A declaração `bigDec2` gera um erro de estouro porque o valor que é atribuído a ele é muito grande para `Long`. Porque o literal numérico primeiro não pode ser interpretado como um `Long`, ele não pode ser atribuído a `Decimal` variável.  
  
 Para `bigDec3`, o caractere de tipo literal `D` resolve o problema, forçando o compilador a interpretar o literal como um `Decimal` em vez de como um `Long`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tipo de Dados Simples](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Tipo de Dados Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
