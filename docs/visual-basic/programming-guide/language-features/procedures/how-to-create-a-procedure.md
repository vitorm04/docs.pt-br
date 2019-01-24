---
title: 'Como: Criar um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 06fed04a0ebe7a0b3111a94308d15d01bcf47c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636528"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Como: Criar um procedimento (Visual Basic)
Você coloca um procedimento entre uma declaração inicial (`Sub` ou `Function`) e uma declaração final (`End Sub` ou `End Function`). Todo o código do procedimento fica entre essas instruções.  
  
 Um procedimento não pode conter outro procedimento, portanto, suas declarações inicial e finais devem estar fora de qualquer outro procedimento.  
  
 Se você tiver um código que executa a mesma tarefa em locais diferentes, você pode escrever a tarefa uma vez como um procedimento e chamá-lo de locais diferentes em seu código.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Para criar um procedimento que não retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Sub` instrução, seguida por um `End Sub` instrução.  
  
2.  No `Sub` instrução, siga o `Sub` palavra-chave com o nome do procedimento, em seguida, a lista de parâmetros entre parênteses.  
  
3.  Colocar instruções de código do procedimento entre o `Sub` e `End Sub` instruções.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.  
  
2.  No `Function` instrução, siga as `Function` palavra-chave com o nome do procedimento, em seguida, a lista de parâmetros entre parênteses e, em seguida, um `As` cláusula especificando o tipo de dados do valor de retorno.  
  
3.  Colocar instruções de código do procedimento entre o `Function` e `End Function` instruções.  
  
4.  Use um `Return` instrução para retornar o valor para o código de chamada.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Para conectar-se o seu novo procedimento com os blocos antigos e repetitivos de código  
  
1.  Certifique-se de que definir o novo procedimento em um local em que o código antigo tem acesso a ele.  
  
2.  No seu bloco de código repetitivo antigo, substitua as instruções que executam as tarefas repetitivas com uma única instrução que chama o `Sub` ou `Function` procedimento.  
  
3.  Se seu procedimento é um `Function` que retorna um valor, certifique-se de que sua instrução de chamada executa uma ação com o valor retornado, como armazená-los em uma variável, ou então o valor será perdido.  
  
## <a name="example"></a>Exemplo  
 O seguinte `Function` procedimento calcula o lado mais longo, ou hipotenusa de um triângulo, considerando os valores para os dois lados.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Procedimentos Recursivos](./recursive-procedures.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programação orientada a objeto (Visual Basic)](../../concepts/object-oriented-programming.md)
