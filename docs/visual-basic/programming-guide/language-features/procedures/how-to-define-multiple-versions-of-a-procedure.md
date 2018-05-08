---
title: Como definir várias versões de um procedimento (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Como definir várias versões de um procedimento (Visual Basic)
Você pode definir um procedimento em várias versões por *sobrecarga* -la, usando o mesmo nome mas uma lista de parâmetros diferentes para cada versão. O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem diferenciá-los por nome.  
  
 Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Para definir várias versões de um procedimento  
  
1.  Gravar um `Sub` ou `Function` declaração para cada versão do procedimento que você deseja definir. Use o mesmo nome do procedimento em cada declaração.  
  
2.  Preceder o `Sub` ou `Function` palavra-chave em cada declaração com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave. Opcionalmente, você pode omitir `Overloads` em declarações, mas se você incluir em qualquer uma das declarações, você deve incluí-lo em cada declaração.  
  
3.  Após cada instrução de declaração, grave o código de procedimento para manipular o caso específico em que o código de chamada fornece argumentos correspondentes a lista de parâmetros desta versão. Você não precisa testar para quais parâmetros forneceu o código de chamada. Visual Basic passa o controle para a versão correspondente do seu procedimento.  
  
4.  Cada versão do procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `Sub` procedimento para lançar uma transação contra um saldo do cliente. Ele usa o `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, use a mesma instrução de chamada em ambos os casos.  
  
 Para obter informações sobre como chamar essas versões do `post` procedimento, consulte [como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)  
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)  
 [Resolução de Sobrecarga](./overload-resolution.md)
