---
title: Como alterar o valor de um argumento de procedimento (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba23c8f0b4b0b6e751546019af902a6305b9ef53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Como alterar o valor de um argumento de procedimento (Visual Basic)
Quando você chama um procedimento, cada argumento que você fornecer corresponde a um dos parâmetros definidos no procedimento. Em alguns casos, o código do procedimento pode alterar o valor subjacente um argumento no código de chamada. Em outros casos, o procedimento pode alterar apenas sua cópia local de um argumento.  
  
 Quando você chamar o procedimento [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] faz uma cópia local de cada argumento que é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Para cada argumento passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fornece o código do procedimento uma referência direta para o elemento de programação subjacente do argumento no código de chamada.  
  
 Se o elemento base no código de chamada é um elemento modificável e o argumento é passado `ByRef`, o código do procedimento pode usar a referência direta para alterar o valor do elemento no código de chamada.  
  
## <a name="changing-the-underlying-value"></a>Alterar o valor subjacente  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Para alterar o valor subjacente de um argumento de procedimento no código de chamada  
  
1.  Na declaração do procedimento, especifique [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente ao argumento.  
  
2.  No código de chamada, passe um elemento de programação modificável como o argumento.  
  
3.  No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.  
  
4.  No código do procedimento, use o nome do parâmetro para atribuir um valor para o elemento subjacente no código de chamada.  
  
 Consulte o exemplo mais para baixo para ver uma demonstração.  
  
## <a name="changing-local-copies"></a>Alterando cópias locais  
 Se o elemento base no código de chamada é um elemento não modificável, ou se o argumento é passado `ByVal`, o procedimento não pode alterar o valor no código de chamada. No entanto, o procedimento pode alterar sua cópia local de um argumento.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Para alterar a cópia de um argumento de procedimento no código do procedimento  
  
1.  Na declaração do procedimento, especifique [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente ao argumento.  
  
     -ou-  
  
     No código de chamada, coloque o argumento entre parênteses na lista de argumentos. Isso força [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para passar o argumento por valor, mesmo se o parâmetro correspondente especifica `ByRef`.  
  
2.  No código do procedimento, use o nome do parâmetro para atribuir um valor para a cópia local do argumento. O valor subjacente no código de chamada não é alterado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos. O `increase` procedimento simplesmente adiciona um para cada elemento. O `replace` procedimento atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41". Porque a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.  
  
 O segundo `MsgBox` chamada exibe "Após Replace (n): 101, 201, 301". Porque `n` é passado `ByRef`, `replace` pode modificar a variável `n` no código de chamada e atribuir uma nova matriz para ele. Porque `n` é um tipo de referência, `replace` também pode alterar seus membros.  
  
 Você pode impedir que o procedimento a modificar a variável no código de chamada. Consulte [como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Quando uma variável é passada por referência, você deve usar o `ByRef` palavra-chave para especificar esse mecanismo.  
  
 O padrão no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] é passar argumentos por valor. No entanto, é uma boa prática para incluir qualquer um de programação de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado. Isso facilita a leitura do seu código.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre há um risco potencial em permitir que um procedimento alterar o valor subjacente um argumento no código de chamada. Verifique se você espera que esse valor a ser alterado e esteja preparado para verificá-lo para validade antes de usá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Diferenças entre argumentos modificáveis e não modificáveis](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Como proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Como forçar um argumento a ser passado por Valor](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
