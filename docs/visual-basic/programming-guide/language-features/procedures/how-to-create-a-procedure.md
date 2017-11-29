---
title: Como criar um procedimento (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a44918b7a1426d215cee0ff2981f5763432a48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Como criar um procedimento (Visual Basic)
Você coloca um procedimento entre uma declaração inicial (`Sub` ou `Function`) e uma declaração final (`End Sub` ou `End Function`). Todo o código do procedimento fica entre essas instruções.  
  
 Um procedimento não pode conter outro procedimento, portanto, suas instruções iniciais e final devem estar fora de qualquer outro procedimento.  
  
 Se você tiver código que executa a mesma tarefa em locais diferentes, pode gravar a tarefa uma vez como um procedimento e chamá-lo a partir de locais diferentes em seu código.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Para criar um procedimento que não retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Sub` instrução, seguida por um `End Sub` instrução.  
  
2.  No `Sub` instrução, siga o `Sub` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses.  
  
3.  Colocar instruções de código do procedimento entre o `Sub` e `End Sub` instruções.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.  
  
2.  No `Function` instrução, siga o `Function` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses e, em seguida, um `As` cláusula especificando o tipo de dados do valor de retorno.  
  
3.  Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.  
  
4.  Use um `Return` instrução para retornar o valor para o código de chamada.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Para conectar seu novo procedimento com os blocos antigos e repetitivos de código  
  
1.  Certifique-se de que definir o novo procedimento em um local onde o código antigo tem acesso a ele.  
  
2.  No seu bloco de código repetitivo antigo, substitua as declarações que executam a tarefa repetitiva com uma única instrução que chama o `Sub` ou `Function` procedimento.  
  
3.  Se seu procedimento é um `Function` que retorna um valor, certifique-se de que sua declaração de chamada executa uma ação com o valor retornado, como fazê-lo em uma variável, ou então o valor será perdido.  
  
## <a name="example"></a>Exemplo  
 O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dado os valores dos outros dois lados.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Procedimentos Recursivos](./recursive-procedures.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
