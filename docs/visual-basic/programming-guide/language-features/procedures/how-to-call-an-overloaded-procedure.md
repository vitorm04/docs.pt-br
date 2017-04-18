---
title: 'Como: chamar um procedimento sobrecarregado (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, procedures
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 0da83aa63bf013d841f2a01a535726f3b03497a1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Como chamar um procedimento sobrecarregado (Visual Basic)
A vantagem de sobrecarregar um procedimento é na flexibilidade da chamada. O código de chamada pode obter as informações necessárias para passar para o procedimento e, em seguida, chamar um único nome de procedimento, não importa quais argumentos ele está passando.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Para chamar um procedimento que tem mais de uma versão definida  
  
1.  No código de chamada, determine quais dados devem passar para o procedimento.  
  
2.  Escreva a chamada de procedimento da maneira normal, apresentando os dados na lista de argumentos. Certifique-se de que os argumentos correspondam à lista de parâmetro em uma das versões definidas para o procedimento.  
  
3.  Você não precisa determinar qual versão do procedimento a ser chamado. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passa o controle para a versão correspondente a lista de argumentos.  
  
     A exemplo a seguir chama o `post` procedimento declarado em [como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md). Obtém a identificação do cliente, determina se é um `String` ou um `Integer`e, em seguida, em ambos os casos chama o mesmo procedimento.  
  
     [!code-vb[56 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures&#57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md)   
 [Resolução de sobrecarga](./overload-resolution.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)
