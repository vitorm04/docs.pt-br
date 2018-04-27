---
title: Procedimentos do operador (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8fba5180da6498d280fa4192937c39d3e33168e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="operator-procedures-visual-basic"></a>Procedimentos do operador (Visual Basic)
Um procedimento de operador é uma série de instruções do Visual Basic que definem o comportamento de um operador padrão (como `*`, `<>`, ou `And`) em uma classe ou estrutura que você definiu. Isso também é chamado de *sobrecarga de operador*.  
  
## <a name="when-to-define-operator-procedures"></a>Quando definir procedimentos de operador  
 Quando você tiver definido uma classe ou estrutura, você pode declarar variáveis sejam do tipo de classe ou estrutura. Às vezes, tal variável precisa participar de uma operação como parte de uma expressão. Para fazer isso, ele deve ser um operando de um operador.  
  
 Visual Basic define operadores somente em seu tipo de dados básico. Você pode definir o comportamento de um operador quando um ou ambos os operandos são do tipo de sua classe ou estrutura.  
  
 Para obter mais informações, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Tipos de procedimento de operador  
 Um procedimento de operador pode ser um dos seguintes tipos:  
  
-   Uma definição de um operador unário onde o argumento é do tipo de sua classe ou estrutura.  
  
-   Uma definição de um operador binário onde pelo menos um dos argumentos é do tipo de sua classe ou estrutura.  
  
-   Uma definição de um operador de conversão onde o argumento é do tipo de sua classe ou estrutura.  
  
-   Uma definição de um operador de conversão que retorna o tipo de sua classe ou estrutura.  
  
 Operadores de conversão são sempre unários, e você sempre usar `CType` como o operador que você está definindo.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A sintaxe para declarar um procedimento de operador é da seguinte maneira:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operando1*`[,`*operand2* `]) As` *tipo de dados*   
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Você usa o `Widening` ou `Narrowing` palavra-chave somente em um operador de conversão de tipo. O símbolo do operador é sempre [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para um operador de conversão de tipo.  
  
 Você declara dois operandos para definir um operador binário, e declara um operando para definir um operador unário, incluindo um operador de conversão de tipo. Todos os operandos devem ser declarados `ByVal`.  
  
 Você declara cada operando da mesma maneira que você declarar parâmetros para [subprocedimentos](./sub-procedures.md).  
  
### <a name="data-type"></a>Tipo de dados  
 Como você está definindo um operador em uma classe ou estrutura que você definiu, pelo menos um dos operandos deve ser do tipo de dados da classe ou estrutura. Para um operador de conversão de tipo, o operando ou o tipo de retorno deve ser do tipo de dados da classe ou estrutura.  
  
 Para obter mais detalhes, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>A sintaxe de chamada  
 Você chamar um procedimento de operador implicitamente, usando o símbolo do operador em uma expressão. Você fornece os operandos da mesma maneira que faria para operadores predefinidos.  
  
 A sintaxe para chamar um procedimento de operador implícito é da seguinte maneira:  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol*   `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 A seguinte estrutura armazena um valor inteiro assinado de 128 bits como as partes superiores e inferiores constituintes. Define o `+` para adicionar dois `veryLong` valores e gerar um resultante `veryLong` valor.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 O exemplo a seguir mostra uma chamada típica para o `+` operador definido em `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Para obter mais informações e exemplos, consulte [Sobrecarga de operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Como definir um operador](./how-to-define-an-operator.md)  
 [Como definir um operador de conversão](./how-to-define-a-conversion-operator.md)  
 [Como chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)  
 [Como usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)
