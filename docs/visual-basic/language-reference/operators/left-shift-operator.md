---
title: "Operador &lt;&lt; (Visual Basic) | Microsoft Docs"
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
  - "vb.<<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador << [Visual Basic]"
  - "operadores bit shift"
  - "Operador <<, Operador left shift do Visual Basic"
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &lt;&lt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa um deslocamento aritmético à esquerda em um padrão de bits.  
  
## Sintaxe  
  
```  
  
result = pattern << amount  
```  
  
## Partes  
 `result`  
 Obrigatório.  Valor numérico integral.  O resultado do deslocamento do padrão de bits.  O tipo de dados é o mesmo de `pattern`.  
  
 `pattern`  
 Obrigatório.  Expressão numérica integral.  O padrão de bits para ser deslocado.  O tipo de dados deve ser um tipo integral \(`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`\).  
  
 `amount`  
 Obrigatório.  Expressão numérica.  O número de bits para deslocar o padrão de bits.  O tipo de dados deve ser `Integer` ou ampliável para `Integer`.  
  
## Comentários  
 Shifts aritméticos são não circulares, que significa que os bits deslocados de uma extremidade do resultado não são reintroduzidos na outra extremidade.  Em um deslocamento aritmético à esquerda, os bits deslocados fora do intervalo de tipo de dados o resultado são descartados, e as posições vagas de bits no lado direito estão definidas como zero.  
  
 Para evitar que uma mudança de bits mais do que o resultado pode comportar, o Visual Basic mascara o valor de `amount` com uma máscara de tamanho que corresponde ao tipo de dados do `pattern`.  O binário AND desses valores é usado para a quantidade de deslocamentos.  As máscaras de tamanho são:  
  
|Tipo de dados do `pattern`|Máscara de tamanho \(decimal\)|Máscara de tamanho \(hexadecimal\)|  
|--------------------------------|------------------------------------|----------------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 Se `amount` for zero, o valor de `result` é idêntico ao valor de `pattern`.  Se `amount` for negativo, ele é interpretado como um valor não assinado e mascarado com a máscara de tamanho apropriada.  
  
 Deslocamentos aritméticos nunca geram exceções de overflow \(estouro\).  
  
> [!NOTE]
>  O operador `<<` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se o seu código utiliza este operador em uma classe ou estrutura, certifique\-se de que você compreenda seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa a `<<` operador para executar cálculos aritméticos deixado turnos nos valores integrais.  O resultado sempre tem o mesmo tipo de dados que a expressão que está sendo deslocada.  
  
 [!CODE [VbVbalrOperators#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#12)]  
  
 Os resultados do exemplo anterior são os seguintes:  
  
-   `result1` é 192 \(0000 0000 1100 0000\).  
  
-   `result2` é 3072 \(0000 1100 0000 0000\).  
  
-   `result3` é \-32768 \(1000 0000 0000 0000\).  
  
-   `result4` é 384 \(0000 0001 1000 0000\).  
  
-   `result5`é 0 \(deslocadas 15 casas à esquerda\).  
  
 O valor de deslocamento para `result4` é calculado como 17 AND 15, que é igual a 1.  
  
## Consulte também  
 [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Operador \<\<\=](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)