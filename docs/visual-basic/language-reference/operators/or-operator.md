---
title: "Operador Or (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Or"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador Or"
  - "operadores [Visual Basic], bit a bit"
  - "Operador Or inclusivo"
  - "operadores bit a bit, o operador OR"
  - "Palavra-chave Or"
  - "operadores [Visual Basic], inclusivos ou"
  - "disjunção, de operadores [Visual Basic]"
  - "comparação bit a bit"
  - "disjunção lógica"
  - "Operador de disjunção"
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Or (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa uma disjunção lógica em duas `Boolean` expressões ou uma disjunção bit a bit em duas expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Obrigatório. Qualquer `Boolean` ou expressão numérica. Para `Boolean` comparação, `result` é a disjunção lógica de dois `Boolean` valores. Para operações bit a bit, `result` é um valor numérico representando a disjução bit a bit de dois padrões numéricos de bits.  
  
 `expression1`  
 Obrigatório. Qualquer `Boolean` ou expressão numérica.  
  
 `expression2`  
 Obrigatório. Qualquer `Boolean` ou expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Para `Boolean` comparação, `result` é `False` se e somente se ambos os `expression1` e `expression2` são avaliadas como `False`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Em um `Boolean` comparação, o `Or` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento. O [operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) executa *Short-circuiting*, que significa que, se `expression1` é `True`, em seguida, `expression2` não será avaliado.  
  
 Para operações bit a bit, o `Or` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.  
  
|Se bit no `expression1` é|E o bit na `expression2` é|O bit no `result` é|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Como os operadores lógicos e bit a bit possuem uma precedência menor que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.  
  
## <a name="data-types"></a>Tipos de dados  
 Se o operando consiste em um `Boolean` expressão e uma expressão numérica, o Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.  
  
 Para um `Boolean` comparação, o tipo de dados do resultado é `Boolean`. Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`. Consulte a tabela "Comparações relacionais e bit a bit" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `Or` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica em duas expressões. O resultado é um `Boolean` valor que representa se uma das duas expressões são `True`.  
  
 [!CODE [VbVbalrOperators#35](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#35)]  
  
 O exemplo anterior produz resultados de `True`, `True`, e `False`, respectivamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica inclusiva nos bits individuais de duas expressões numéricas. O bit no padrão resultante é definido se nenhum dos bits correspondentes nos dois operandos é definido como 1.  
  
 [!CODE [VbVbalrOperators#36](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#36)]  
  
 O exemplo anterior produz resultados 10, 14 e 14, respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)