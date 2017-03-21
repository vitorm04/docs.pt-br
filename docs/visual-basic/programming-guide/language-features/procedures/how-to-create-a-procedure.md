---
title: 'Como: criar um procedimento (Visual Basic) | Documentos do Microsoft'
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
- procedures, defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures, about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
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
ms.openlocfilehash: 7d07cfc5f3918d3211de4f171a044c459e196997
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-procedure-visual-basic"></a>Como criar um procedimento (Visual Basic)
Você coloca um procedimento entre uma declaração inicial (`Sub` ou `Function`) e uma declaração final (`End Sub` ou `End Function`). Todo o código do procedimento fica entre essas instruções.  
  
 Um procedimento não pode conter outro procedimento, portanto, suas declarações inicial e final devem estar fora de qualquer outro procedimento.  
  
 Se você tiver um código que executa a mesma tarefa em locais diferentes, você pode escrever a tarefa uma vez como um procedimento e, em seguida, chamá-la em locais diferentes em seu código.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Para criar um procedimento que não retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Sub` instrução, seguida por um `End Sub` instrução.  
  
2.  No `Sub` instrução, siga o `Sub` palavra-chave com o nome do procedimento, a lista de parâmetros entre parênteses.  
  
3.  Coloque as declarações de código do procedimento entre o `Sub` e `End Sub` instruções.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Para criar um procedimento que retorna um valor  
  
1.  Fora de qualquer outro procedimento, utilize uma `Function` instrução, seguida por um `End Function` instrução.  
  
2.  No `Function` instrução, siga o `Function` o nome do procedimento, a lista de parâmetros entre parênteses, a palavra-chave e, em seguida, um `As` cláusula especificando o tipo de dados do valor de retorno.  
  
3.  Coloque as declarações de código do procedimento entre o `Function` e `End Function` instruções.  
  
4.  Use um `Return` instrução para retornar o valor para o código de chamada.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Para conectar seu novo procedimento com os blocos antigos e repetitivos de código  
  
1.  Certifique-se de que definir o novo procedimento em um local onde o código antigo tem acesso a ele.  
  
2.  No seu bloco de código repetitivo antigo, substitua as declarações que executam a tarefa repetitiva com uma declaração única que chama o `Sub` ou `Function` procedimento.  
  
3.  Se seu procedimento é um `Function` que retorna um valor, garanta que sua declaração de chamada executa uma ação com o valor retornado, como armazená-lo em uma variável, ou então o valor será perdido.  
  
## <a name="example"></a>Exemplo  
 O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo, considerando os valores para os dois lados.  
  
 [!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Procedimentos recursivos](./recursive-procedures.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programação Orientada a Objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
