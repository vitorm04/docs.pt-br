---
title: "Procedimentos do operador (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "sobrecarga de operador"
  - "procedimentos de Operador"
  - "operadores [Visual Basic], sobrecarga"
  - "operadores sobrecarregados"
  - "procedimentos, operator"
  - "sintaxe, Procedimentos de Operador"
  - "código do Visual Basic, operadores"
  - "código do Visual Basic, procedimentos"
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedimentos do operador (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um procedimento de operador é uma série de declarações [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] que definem o comportamento de um operador padrão \(tais como `*`, `<>`, ou `And`\) em uma classe ou estrutura que você definiu.  Isto também é chamado de  *sobrecarga de operador* .  
  
## Quando Definir Procedimentos de Operador  
 Quando definir uma classe ou estrutura, você pode declarar variaveis para que sejam do tipo da classe ou da estrutura.  Às vezes, tal variável precisa participar em uma operação como parte de uma expressão.  Para fazer isto, é necessário que seja um operando de um operador.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]define operadores somente em seu tipo de dados fundamental.  Você pode definir o comportamento de um operador quando um ou ambos os operandos são do tipo da sua classe ou estrutura.  
  
 Para obter mais informações, consulte [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## Tipos de Procedimento de Operador  
 Um operador de procedimento pode ser de um dos tipos seguintes:  
  
-   Uma definição de um operador unário onde o argumento é do tipo da sua classe ou estrutura.  
  
-   Uma definição de um operador binário onde pelo menos um dos argumentos é do tipo da sua classe ou estrutura.  
  
-   Uma definição de um operador de conversão onde o argumento é do tipo da sua classe ou estrutura.  
  
-   Uma definição de um operador de conversão que retorna o tipo da sua classe ou estrutura.  
  
 Operadores de conversão são sempre unários, e você sempre usa `CType` como o operador que você está definindo.  
  
## Sintaxe da Declaração  
 A sintaxe para declarar um operador de procedimento é a seguinte:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Você usa a palavra chave  `Widening` ou  `Narrowing` somente para um operador de conversão de tipo.  O símbolo do operador é sempre [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para operador de conversão de tipo.  
  
 Você declara dois operandos para definir um operador binário, e declara um operando para definir um operador unário, incluindo um operador de conversão de tipo.  Todos operandos devem ser declarados `ByVal`.  
  
 Você declara cada operando da mesma forma que declara parâmetros para [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md).  
  
### Tipo de dados  
 Como você está definindo um operador em uma classe ou estrutura que você definiu, pelo menos um dos operandos deve ser do tipo de dado da classe ou estrutura.  Para o operador de conversão de tipo, tanto o operando quanto o tipo de retorno devem ser do tipo de dado da classe ou estrutura.  
  
 Para mais detalhes, consulte [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## Sintaxe de Chamada  
 Você invoca um procedimento de operador de maneira implícita, ao utilizar o simbolo do operador em uma expressão.  Você fornece os operandos da mesma forma que você faz para operadores pré\-definidos.  
  
 A sintaxe para uma chamada implícita para um procedimento de operador é a seguinte:  
  
 `Dim testStruct As`  *nomedaestrutura*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### Ilustração de Declaração e Chamada  
 A seguinte estrutura armazena uma valor inteiro sinalizado de 128 bits constituinte de partes de alta\-ordem e baixa\-ordem.  Define o operador `+` para somar dois valores  `veryLong`  e gerar como resultado um valor  `veryLong` .  
  
 [!code-vb[VbVbcnProcedures#23](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 O exemplo a seguir mostra uma chamada típica para o operador `+` definido em  `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Para maiores informações e exemplos, acesse[Sobrecarga de Operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Como chamar um procedimento de operador](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [Como usar uma classe que define operadores](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)