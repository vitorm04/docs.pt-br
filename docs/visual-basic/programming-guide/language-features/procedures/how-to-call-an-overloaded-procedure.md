---
title: Como chamar um procedimento sobrecarregado (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 802a312d6ec6640594f3c6b662202d1ffcf2376d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Como chamar um procedimento sobrecarregado (Visual Basic)
A vantagem de sobrecarregar um procedimento é a flexibilidade da chamada. O código de chamada pode obter as informações necessárias para passar para o procedimento e, em seguida, chamar um único nome de procedimento, não importa quais argumentos está passando.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Para chamar um procedimento que tem mais de uma versão definida  
  
1.  No código de chamada, determine quais dados a serem passados para o procedimento.  
  
2.  Grave a chamada de procedimento da maneira normal, apresentando os dados na lista de argumentos. Certifique-se de que os argumentos correspondem à lista de parâmetro em uma das versões definidas para o procedimento.  
  
3.  Você não precisa determinar qual versão do procedimento a ser chamado. Visual Basic passa o controle para a versão correspondente a lista de argumentos.  
  
     A exemplo a seguir chama o `post` procedimento declarado em [como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md). Obtém a identificação do cliente, determina se é um `String` ou um `Integer`e, em seguida, em ambos os casos chama o mesmo procedimento.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)  
 [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)  
 [Resolução de Sobrecarga](./overload-resolution.md)  
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)
