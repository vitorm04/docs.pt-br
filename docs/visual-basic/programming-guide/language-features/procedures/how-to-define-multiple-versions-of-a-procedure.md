---
title: "Como: definir várias versões de um procedimento (Visual Basic) | Documentos do Microsoft"
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
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
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
ms.openlocfilehash: 0228083ce00a0f552227fd7ae8f0f5a24f65148e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Como definir várias versões de um procedimento (Visual Basic)
Você pode definir um procedimento em múltiplas versões por *sobrecarga* -lo, usando o mesmo nome mas uma lista de parâmetros diferentes para cada versão. O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem diferenciá-los pelo nome.  
  
 Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Para definir várias versões de um procedimento  
  
1.  Escrever um `Sub` ou `Function` uma instrução de declaração para cada versão do procedimento que você deseja definir. Use o mesmo nome do procedimento em cada declaração.  
  
2.  Preceder o `Sub` ou `Function` palavra-chave em cada declaração com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave. Opcionalmente, você pode omitir `Overloads` em declarações, mas se você incluí-lo em qualquer um das declarações, você deve incluí-lo em cada declaração.  
  
3.  Após cada instrução de declaração, escreva código de procedimento para manipular a ocorrência específica onde o código de chamada fornece argumentos correspondentes a lista de parâmetros da versão. Você não precisa testar para quais parâmetros o código de chamada forneceu. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passa o controle para a versão correspondente do seu procedimento.  
  
4.  Cada versão do procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `Sub` procedimento para lançar uma transação contra um saldo do cliente. Ele usa o `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.  
  
 [!code-vb[VbVbcnProcedures&#72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, use a mesma instrução de chamada em ambos os casos.  
  
 Para obter informações sobre como chamar essas versões do `post` procedimento, consulte [como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md)   
 [Resolução de Sobrecarga](./overload-resolution.md)
