---
title: Procedimentos do operador (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175013"
---
# <a name="operator-procedures-visual-basic"></a>Procedimentos do operador (Visual Basic)
Um procedimento de operador é uma série de instruções do Visual Basic que definem o comportamento de um operador padrão (como `*`, `<>`, ou `And`) em uma classe ou estrutura que você definiu. Isso também é chamado *sobrecarga de operador*.  
  
## <a name="when-to-define-operator-procedures"></a>Quando definir procedimentos de operador  
 Quando você tiver definido uma classe ou estrutura, você pode declarar variáveis sejam do tipo de classe ou estrutura. Às vezes, tal variável precisa participar de uma operação como parte de uma expressão. Para fazer isso, ele deve ser um operando de um operador.  
  
 Visual Basic define operadores somente em seu tipo de dados fundamental. Você pode definir o comportamento de um operador quando um ou ambos os operandos forem do tipo de sua classe ou estrutura.  
  
 Para obter mais informações, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Tipos de procedimento de operador  
 Um procedimento de operador pode ser um dos seguintes tipos:  
  
-   Uma definição de um operador unário onde o argumento é do tipo de sua classe ou estrutura.  
  
-   Uma definição de um operador binário onde pelo menos um dos argumentos é do tipo de sua classe ou estrutura.  
  
-   Uma definição de um operador de conversão onde o argumento é do tipo de sua classe ou estrutura.  
  
-   Uma definição de um operador de conversão que retorna o tipo de sua classe ou estrutura.  
  
 Operadores de conversão são sempre unários, e você sempre use `CType` como o operador que você está definindo.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A sintaxe para declarar um procedimento de operador é da seguinte maneira:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Você usa o `Widening` ou `Narrowing` palavra-chave apenas em um operador de conversão de tipo. O símbolo do operador é sempre [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para um operador de conversão de tipo.  
  
 Você declara dois operandos para definir um operador binário, e declara um operando para definir um operador unário, incluindo um operador de conversão de tipo. Todos os operandos devem ser declarados `ByVal`.  
  
 Você declara cada operando da mesma maneira que você declara parâmetros para [subprocedimentos](./sub-procedures.md).  
  
### <a name="data-type"></a>Tipo de dados  
 Porque você está definindo um operador em uma classe ou estrutura que você definiu, pelo menos um dos operandos deve ser do tipo de dados da classe ou estrutura. Para um operador de conversão de tipo, o operando ou o tipo de retorno deve ser do tipo de dados da classe ou estrutura.  
  
 Para obter mais detalhes, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Sintaxe de chamada  
 Invocar um procedimento de operador implicitamente, usando o símbolo do operador em uma expressão. Você fornece os operandos da mesma maneira que faria para operadores predefinidos.  
  
 A sintaxe para uma chamada implícita para um procedimento de operador é da seguinte maneira:  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 A estrutura a seguir armazena um valor inteiro com sinal de 128 bits como as partes constituintes de ordem alta e baixa-ordem. Ele define a `+` operador para adicionar dois `veryLong` valores e gerar um resultante `veryLong` valor.  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 O exemplo a seguir mostra uma chamada típica para o `+` operador definido no `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Como: Definir um operador](./how-to-define-an-operator.md)
- [Como: Definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Como: Chamar um procedimento de operador](./how-to-call-an-operator-procedure.md)
- [Como: Usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md)
