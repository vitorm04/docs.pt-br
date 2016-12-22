---
title: "Operadores de compara&#231;&#227;o (Visual Basic) | Microsoft Docs"
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
  - "vb.<>"
  - "vb.>="
  - "vb.<="
  - "vb.>"
  - "vb.<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador < [Visual Basic]"
  - "Operador <= [Visual Basic]"
  - "Operador <> [Visual Basic]"
  - "Operador = [Visual Basic]"
  - "Operador > [Visual Basic]"
  - "Operador >= [Visual Basic]"
  - "comparando valores [Visual Basic]"
  - "operadores de comparação, Visual Basicl"
  - "Operador equal [Visual Basic]"
  - "Operador greater than [Visual Basic]"
  - "Operador greater than or equal to [Visual Basic]"
  - "Operador Is [Visual Basic]"
  - "Operador less than [Visual Basic]"
  - "Operador less than or equal to [Visual Basic]"
  - "Operador Like [Visual Basic]"
  - "Operador de comparação not equal to [Visual Basic]"
  - "operadores [Visual Basic], comparação"
  - "operadores [Visual Basic], relacional"
  - "operadores relacionais, sintaxe"
  - "comparação de cadeias de caracteres [Visual Basic]"
  - "símbolos, operadores"
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operadores de compara&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A seguir estão os operadores de comparação definidos em Visual Basic.  
  
 `<`operador  
  
 `<=`operador  
  
 `>`operador  
  
 `>=`operador  
  
 `=`operador  
  
 `<>`operador  
  
 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Operador Like](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 Esses operadores comparam duas expressões para determinar se ou não forem iguais, e se não for, como eles diferem.  `Is`, `IsNot`, e `Like` são discutidas em detalhes em páginas de ajuda separadas.  Os operadores de comparação relacional são discutidos em detalhes nesta página.  
  
## Sintaxe  
  
```  
  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## Partes  
 `result`  
 Obrigatório.  A `Boolean` valor que representa o resultado da comparação.  
  
 `expression`  
 Obrigatório.  Qualquer expressão.  
  
 `comparisonoperator`  
 Obrigatório.  Qualquer operador de comparação relacional.  
  
 `object1`, `object2`  
 Obrigatório.  Qualquer referência a nomes de objeto.  
  
 `string`  
 Obrigatório.  Qualquer expressão `String`.  
  
 `pattern`  
 Obrigatório.  Qualquer `String` expressão ou intervalo de caracteres.  
  
## Comentários  
 A tabela a seguir contém uma lista de operadores de comparação relacional e as condições que determinam se `result` é `True` ou `False`.  
  
|Operador|`True`IF|`False`IF|  
|--------------|--------------|---------------|  
|`<` \(Menor que\)|`expression1`\<  `expression2`|`expression1`\> \=`expression2`|  
|`<=` \(Menor que ou igual a\)|`expression1`\< \=`expression2`|`expression1`\>  `expression2`|  
|`>` \(Maior que\)|`expression1`\>  `expression2`|`expression1`\< \=`expression2`|  
|`>=` \(Maior que ou igual a\)|`expression1`\> \=`expression2`|`expression1`\<  `expression2`|  
|`=`\(Igual a\)|`expression1` \= `expression2`|`expression1`\< \>  `expression2`|  
|`<>`\(Não é igual a\)|`expression1`\< \>  `expression2`|`expression1` \= `expression2`|  
  
> [!NOTE]
>  O [Operador \=](../../../visual-basic/language-reference/operators/assignment-operator.md) também é usado como um operador de atribuição.  
  
 O `Is` operador, o `IsNot` operador e o `Like` o operador tem funcionalidades específicas de comparação diferentes dos operadores na tabela anterior.  
  
## Comparando os números  
 Ao comparar uma expressão do tipo `Single` a um tipo `Double`, o `Single` a expressão é convertida em `Double`.  Esse comportamento é opostos o comportamento encontrado no Visual Basic 6.  
  
 Da mesma forma, se você comparar uma expressão do tipo `Decimal` a uma expressão do tipo `Single` ou `Double`, o `Decimal` a expressão é convertida em `Single` ou `Double`.  Para `Decimal` expressões, qualquer valor fracionário menos de 1E\-28 podem ser perdidas.  Perda de dados valor fracionário pode fazer com que os dois valores sejam comparados como iguais quando não estão.  Por esse motivo, você deve ter cuidado ao usar a igualdade \(`=`\) para comparar duas variáveis de ponto flutuante.  É mais seguro testar se o valor absoluto da diferença entre os dois números é menor do que uma pequena tolerância aceitável.  
  
### Ponto flutuante Imprecision  
 Quando você trabalha com números de ponto flutuante, lembre que eles nem sempre têm uma representação precisa na memória.  Isso pode levar a resultados inesperados de certas operações, como, por exemplo, a comparação de valor e o [Operador Mod](../../../visual-basic/language-reference/operators/mod-operator.md).  Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Comparando Sequências de Caracteres  
 Quando você compara seqüências de caracteres, as expressões de seqüência de caracteres são avaliadas com base em sua ordem de classificação alfabética, que depende do `Option Compare` configuração.  
  
 `Option Compare Binary`comparações de uma ordem de classificação derivada de representações binárias internas dos caracteres da seqüência de bases.  A ordem de classificação é determinada pela página de código.  O exemplo a seguir mostra uma ordem de classificação binária típica.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text`bases de seqüência comparações em uma ordem de classificação de maiúsculas e minúsculas, textual determinadas pela localidade do seu aplicativo.  Ao definir `Option Compare Text` e classificar os caracteres no exemplo anterior, a ordem de classificação de texto seguinte se aplica:  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### Dependência de localidade  
 Ao definir `Option Compare Text`, o resultado de uma comparação de seqüência de caracteres pode depender da localidade na qual o aplicativo é executado.  Dois caracteres podem comparar como igual em uma localidade, mas não em outro.  Se você estiver usando uma comparação de seqüência de caracteres para tomar decisões importantes, como se deseja aceitar uma tentativa de logon, você deve estar alerta a sensibilidade de localidade.  Considere uma das configurações `Option Compare Binary` ou chamando o <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, que considera a localidade.  
  
## Sem especificação de tipo de programação com operadores de comparação relacional  
 O uso de operadores de comparação relacional com `Object` expressões não é permitido em `Option Strict On`.  Quando `Option Strict` é `Off`e `expression1` ou `expression2` é um `Object` a expressão, os tipos de tempo de execução determinam como eles são comparados.  A tabela a seguir mostra como as expressões são comparadas e o resultado da comparação, dependendo do tipo de tempo de execução dos operandos.  
  
|Se operandos forem|Comparação é|  
|------------------------|------------------|  
|Ambos`String`|Classificar com base em características de classificação de seqüência de comparação.|  
|Ambas numéricas|Objetos convertidos em `Double`, comparação numérica.|  
|Um numérico e outro`String`|O `String` é convertido em um `Double` e é feita uma comparação numérica.  Se a `String` não pode ser convertido em `Double`, um <xref:System.InvalidCastException> é lançada.|  
|Um ou ambos são tipos de referência diferente de`String`|Um <xref:System.InvalidCastException> é lançada.|  
  
 Comparações numéricas tratam `Nothing` como 0.  Tratam de comparações de seqüência de caracteres `Nothing` como `""` \(uma seqüência vazia\).  
  
## Sobrecarga  
 Os operadores de comparação relacional \(`<`.  `<=``>`, `>=`, `=`, `<>`\) pode ser  *sobrecarregado*, que significa que uma classe ou estrutura poderá redefinir seu comportamento quando um operando tem o tipo da classe ou estrutura.  Se seu código usa qualquer um destes operadores em uma classe ou estrutura, certifique\-se de que você compreende o comportamento de redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
 Observe que o [Operador \=](../../../visual-basic/language-reference/operators/assignment-operator.md) podem ser sobrecarregados somente como um operador de comparação relacional, e não como um operador de atribuição.  
  
## Exemplo  
 O exemplo a seguir mostra vários usos de operadores de comparação relacional, que você pode usar para comparar expressões.  Operadores de comparação relacional retornam um `Boolean` resultado que representa se ou não avalia a expressão estabelecida `True`.  Quando você aplica a `>` e `<` operadores para seqüências de caracteres, a comparação é feita usando a ordem de classificação alfabética normal das seqüências de caracteres.  Esta ordem pode ser dependente de configuração de localidade.  Se a classificação é diferencia maiúsculas de minúsculas ou não depende do  [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) configuração.  
  
 [!CODE [VbVbalrOperators#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#1)]  
  
 No exemplo anterior, a primeira comparação retorna `False` e as comparações restantes retornam `True`.  
  
## Consulte também  
 <xref:System.InvalidCastException>   
 [Operador \=](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)