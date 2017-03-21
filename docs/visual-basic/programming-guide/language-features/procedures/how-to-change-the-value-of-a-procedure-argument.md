---
title: 'Como: alterar o valor de um argumento de procedimento (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6c42a50b75bcc70ae0a3f70771b9e1f85626004b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Como alterar o valor de um argumento de procedimento (Visual Basic)
Quando você chama um procedimento, cada argumento que você fornecer corresponde a um dos parâmetros definidos no procedimento. Em alguns casos, o código do procedimento pode alterar o valor subjacente um argumento no código de chamada. Em outros casos, o procedimento pode alterar apenas sua cópia local de um argumento.  
  
 Quando você chama o procedimento [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] faz uma cópia local de cada argumento que é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Para cada argumento passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece o código do procedimento uma referência direta ao elemento de programação subjacente o argumento o código de chamada.  
  
 Se o elemento base no código de chamada é um elemento modificável e o argumento é passado `ByRef`, o código do procedimento pode usar a referência direta para alterar o valor do elemento no código de chamada.  
  
## <a name="changing-the-underlying-value"></a>Alterar o valor subjacente  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Para alterar o valor subjacente de um argumento de procedimento no código de chamada  
  
1.  Na declaração do procedimento, especifique [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente ao argumento.  
  
2.  No código de chamada, passe um elemento de programação modificável como o argumento.  
  
3.  No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.  
  
4.  No código do procedimento, use o nome do parâmetro para atribuir um valor para o elemento base no código de chamada.  
  
 Consulte o exemplo mais para baixo para ver uma demonstração.  
  
## <a name="changing-local-copies"></a>Alterando cópias locais  
 Se o elemento base no código de chamada é um elemento não modificável, ou se o argumento é passado `ByVal`, o procedimento não pode alterar o valor no código de chamada. No entanto, o procedimento pode alterar sua cópia local de um argumento.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Para alterar a cópia de um argumento de procedimento no código de procedimento  
  
1.  Na declaração do procedimento, especifique [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente ao argumento.  
  
     -ou-  
  
     No código de chamada, coloque o argumento entre parênteses na lista de argumentos. Isso força [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para passar o argumento por valor, mesmo se o parâmetro correspondente especifica `ByRef`.  
  
2.  No código do procedimento, use o nome do parâmetro para atribuir um valor para a cópia local do argumento. O valor subjacente no código de chamada não é alterado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos. O `increase` procedimento simplesmente adiciona um para cada elemento. O `replace` procedimento atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento.  
  
 [!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41". Porque a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.  
  
 O segundo `MsgBox` chamada exibe "Após Replace (n): 101, 201, 301". Porque `n` é passado `ByRef`, `replace` pode modificar a variável `n` no código de chamada e atribuir uma nova matriz para ele. Porque `n` é um tipo de referência, `replace` também pode alterar seus membros.  
  
 Você pode impedir que o procedimento modificar a variável no código de chamada. Consulte [como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Quando uma variável é passada por referência, você deve usar o `ByRef` palavra-chave para especificar esse mecanismo.  
  
 O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor. No entanto, é boa prática incluir de programação a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado. Isso torna seu código mais fácil de ler.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre há um risco potencial em permitir que um procedimento alterar o valor subjacente um argumento no código de chamada. Verifique se você espera que esse valor seja alterado e esteja preparado para verificá-lo para validade antes de usá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre argumentos modificável e não modificável](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md)   
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
