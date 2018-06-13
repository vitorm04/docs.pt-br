---
title: Como proteger um argumento de procedimento contra alterações de valor (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: d2e131b770d8498a634d946a5900f9b373ca7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651512"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Como proteger um argumento de procedimento contra alterações de valor (Visual Basic)
Se um procedimento declara um parâmetro como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic fornece o código do procedimento uma referência direta para o elemento de programação subjacente do argumento no código de chamada. Isso permite que o procedimento para alterar o valor subjacente do argumento no código de chamada. Em alguns casos, o código de chamada talvez queira proteger contra essa alteração.  
  
 Você sempre pode proteger um argumento de alteração, declarando o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) no procedimento. Se desejar alterar um argumento fornecido em alguns casos, mas outros não, você pode declará-la `ByRef` e permitir que o código de chamada determinar o mecanismo de passagem em cada chamada. Ele faz isso colocando o argumento correspondente entre parênteses para passá-lo por valor ou não envolve em parênteses para passá-lo por referência. Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos. O `increase` procedimento simplesmente adiciona um para cada elemento. O `replace` procedimento atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento. No entanto, a reatribuição não afeta a variável array subjacente no código de chamada.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41". Porque a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.  
  
 O segundo `MsgBox` chamada exibe "Após Replace (n): 11, 21, 31, 41". Porque `n` é passado `ByVal`, `replace` não é possível modificar a variável `n` no código de chamada atribuindo uma nova matriz. Quando `replace` cria a nova instância de matriz `k` e o atribui à variável local `a`, ele perde a referência à `n` passado pelo código de chamada. Quando ele é alterado os membros de `a`, somente a matriz local `k` é afetado. Portanto, `replace` não incrementa os valores de matriz `n` no código de chamada.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O padrão no Visual Basic é passar argumentos por valor. No entanto, é uma boa prática para incluir qualquer um de programação de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado. Isso facilita a leitura do seu código.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Diferenças entre argumentos modificáveis e não modificáveis](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Como alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Como forçar um argumento a ser passado por Valor](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
