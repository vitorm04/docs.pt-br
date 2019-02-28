---
title: 'Como: Definir várias versões de um procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: baaaca13755b9fdc11308ff3e4df39835dbe466e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980770"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Como: Definir várias versões de um procedimento (Visual Basic)
Você pode definir um procedimento em várias versões por *sobrecarga* -lo, usando o mesmo nome mas uma lista de parâmetros diferentes para cada versão. O objetivo de sobrecarga é definir várias versões intimamente relacionadas de um procedimento sem a necessidade para diferenciá-los por nome.  
  
 Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Para definir várias versões de um procedimento  
  
1.  Gravar uma `Sub` ou `Function` instrução de declaração para cada versão do procedimento que você deseja definir. Use o mesmo nome do procedimento em cada declaração.  
  
2.  Preceda a `Sub` ou `Function` palavra-chave em cada declaração com o [sobrecarrega](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave. Opcionalmente, você pode omitir `Overloads` em declarações, mas se você incluí-lo em qualquer uma das declarações, você deve incluí-lo em cada declaração.  
  
3.  Após cada instrução de declaração, escreva um código de procedimento para manipular o caso específico em que o código de chamada fornece argumentos correspondentes a lista de parâmetros desta versão. Você não precisa testar para quais parâmetros o código de chamada forneceu. Visual Basic passa o controle para a versão correspondente do seu procedimento.  
  
4.  Cada versão do procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `Sub` procedimento para lançar uma transação em relação ao saldo do cliente. Ele usa o `Overloads` palavra-chave para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, use a mesma instrução de chamada em ambos os casos.  
  
 Para obter informações sobre como chamar essas versões dos `post` procedimento, consulte [como: Chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferentes.  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como: Sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)
- [Resolução de Sobrecarga](./overload-resolution.md)
