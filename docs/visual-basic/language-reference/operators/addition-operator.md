---
title: "Operador + (Visual Basic) | Microsoft Docs"
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
  - "vb.+"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador +"
  - "Operadores aritméticos, adição"
  - "operadores de concatenação, sintaxe"
  - "cadeias de caracteres {Visual Basic], concatenação"
  - "Operador de soma"
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador + (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Adiciona dois números ou retorna o valor positivo de um expressão numérica.  Também pode ser usado para concatenar duas expressões de string.  
  
## Sintaxe  
  
```  
  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`expression1`|Obrigatório.  Qualquer expressão numérica ou string.|  
|`expression2`|Necessária a menos que o operador `+` esteja calculando um valor negativo.  Qualquer expressão numérica ou string.|  
  
## Resultado  
 Se `expression1` e `expression2` forem numéricos, o resultado é sua soma aritmética.  
  
 Se `expression2` estiver ausente, o operador `+` é o operador de identidade *unário* para o valor inalterado de uma expressão.  Nesse sentido, a operação consiste em manter o sinal de `expression1`,portanto, o resultado é negativo se `expression1` for negativo.  
  
 Se `expression1` e `expression2` são ambas strings, o resultado é a concatenação de seus valores.  
  
 Se `expression1` e `expression2` são de tipos mistos, a ação tomada depende seus tipos, seu conteúdo e a configuração de [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  Para obter mais informações, consulte as tabelas em "Comentários".  
  
## Os tipos suportados  
 Todos os tipos numéricos, incluindo os tipos unsigned e ponto\-flutuante e `Decimal` e `String`.  
  
## Comentários  
 Em geral, `+` executa adição aritmética quando possível e concatena somente quando as duas expressões são strings.  
  
 Se nenhuma expressão for um `Object`, Visual Basic toma as seguintes medidas.  
  
|||  
|-|-|  
|Tipos de dados de expressões|Ação pelo compilador|  
|As duas expressões são tipos de dados numéricos \(`SByte`, `Byte`,`Short`, `UShort`,`Integer`,`UInteger`,`Long`,`ULong`, `Decimal`,`Single`,ou `Double`\)|Somar  O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.  Veja as tabelas de "Aritmética de Inteiros" em [Tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)|  
|As duas expressões são do tipo `String`|Concatenar.|  
|Uma expressão é um tipo de dados numéricos e a outra é uma string.|Se `Option Strict` estiver `On`, então é gerado um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, então implicitamente converta o `String` `Double` e adicione.<br /><br /> Se a `String` não pode ser convertida para `Double`, lance uma exceção <xref:System.InvalidCastException>.|  
|Uma expressão é um tipo de dados numérico e a outra é uma string.[nada](../../../visual-basic/language-reference/nothing.md)|Adicionar, com `Nothing` valorado como zero.|  
|Uma expressão é uma sequência de caracteres, e a outra é `Nothing`|Concatene, com `Nothing` valorado como " ".|  
  
 Se uma expressão for uma expressão `Object`, o Visual Basic toma as seguintes medidas.  
  
|||  
|-|-|  
|Tipos de dados de expressões|Ação pelo compilador|  
|A expressão `Object` contém um valor numérico e a outra é uma tipo de dados numérico|Se `Option Strict` estiver `On`, então é gerado um erro do compilador.<br /><br /> Se `Option Strict` estiver `Off`, adicione.|  
|`Object`expressão contém um valor numérico e a outra é do tipo`String`|Se `Option Strict` estiver `On`, então é gerado um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, então implicitamente converta o `String` `Double` e adicione.<br /><br /> Se a `String` não pode ser convertida para `Double`, lance uma exceção <xref:System.InvalidCastException>.|  
|A expressão `Object` contém uma string e a outra é um tipo de dados numérico|Se `Option Strict` estiver `On`, então é gerado um erro do compilador.<br /><br /> Se `Option Strict` estiver `Off`, então implicitamente converta a string `Object` `Double` e adicione.<br /><br /> Se a string `Object` não pode ser convertida para `Double`, lance uma exceção <xref:System.InvalidCastException>.|  
|`Object`expressão contém uma seqüência de caracteres e a outra é do tipo`String`|Se `Option Strict` estiver `On`, então é gerado um erro do compilador.<br /><br /> Se `Option Strict` é `Off`, então implicitamente converta `Object` para `String` e adicione.|  
  
 Se as duas expressões forem expressões `Object`, o Visual Basic toma as seguintes medidas \(somente `Option Strict Off`\).  
  
|||  
|-|-|  
|Tipos de dados de expressões|Ação pelo compilador|  
|As duas expressões `Object` contém valores numéricos|Somar|  
|Ambas expressões `Object` são do tipo `String`.|Concatenar.|  
|Uma expressão `Object` contém uma string e a outra é um tipo de dados numérico|Implicitamente converta a sequência de caracteres `Object` para `Double` e adicione.<br /><br /> Se a sequência de caracteres `Object` não pode ser convertida para um valor numérico, em seguida, lance uma exceção <xref:System.InvalidCastException>.|  
  
 Se qualquer um das expressões `Object`for avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, o operador `+` vai tratá\-la como uma `String` de valor " ".  
  
> [!NOTE]
>  Quando você usa o operador `+`, talvez não seja possível determinar se a adição ou concatenação de sequência de caracteres ocorrerá.  Use o operador `&` de concatenação para eliminar ambiguidade e fornecer código autodocumentável.  
  
## Sobrecarga  
 O operador `+` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 O exemplo a seguir usa o operador `+` para somar números.  Se os operandos forem ambos numéricos,o Visual Basic calcula o resultado aritmético.  O resultado aritmético representa a soma de dois operandos.  
  
 [!CODE [VbVbalrOperators#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#6)]  
  
 Você também pode usar o operador `+` para concatenar as sequências de caracteres.  Se os operandos forem ambos sequências de caracteres, o Visual Basic os concatena.  O resultado da concatenação representa uma única sequência de caracteres consistindo no conteúdo de dois operandos um após o outro.  
  
 Se os operandos forem de tipos mistos, o resultado depende da configuração de [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  O exemplo a seguir ilustra o resultado quando `Option Strict` está `On`.  
  
 [!CODE [VbVbalrOperators#53](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#53)]  
  
 [!CODE [VbVbalrOperators#50](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#50)]  
[!CODE [VbVbalrOperators#51](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#51)]  
  
 O exemplo a seguir ilustra o resultado quando `Option Strict` está `Off`.  
  
 [!CODE [VbVbalrOperators#54](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#54)]  
  
 [!CODE [VbVbalrOperators#50](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#50)]  
[!CODE [VbVbalrOperators#52](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#52)]  
  
 Para eliminar ambiguidade, você deve usar o operador `&` em vez de `+` para concatenação.  
  
## Consulte também  
 [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [Operadores de concatenação](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)