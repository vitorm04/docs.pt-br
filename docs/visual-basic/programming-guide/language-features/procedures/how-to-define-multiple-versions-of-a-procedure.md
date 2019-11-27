---
title: Como definir várias versões de um procedimento
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 83e96e271f6613aa325d59a0ca2fce9fc69fe059
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350484"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Como definir várias versões de um procedimento (Visual Basic)
Você pode definir um procedimento em várias versões *sobrecarregando* -a, usando o mesmo nome, mas uma lista de parâmetros diferente para cada versão. A finalidade do sobrecarregamento é definir várias versões de um procedimento bem relacionadas sem precisar diferenciá-las por nome.  
  
 Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Para definir várias versões de um procedimento  
  
1. Escreva uma instrução de declaração de `Sub` ou `Function` para cada versão do procedimento que você deseja definir. Use o mesmo nome de procedimento em cada declaração.  
  
2. Preceda a palavra-chave `Sub` ou `Function` em cada declaração com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) . Opcionalmente, você pode omitir `Overloads` nas declarações, mas se você incluí-la em qualquer uma das declarações, deverá incluí-la em cada declaração.  
  
3. Seguindo cada instrução de declaração, escreva o código do procedimento para lidar com o caso específico em que o código de chamada fornece argumentos correspondentes à lista de parâmetros da versão. Você não precisa testar quais parâmetros o código de chamada forneceu. Visual Basic passa o controle para a versão correspondente do procedimento.  
  
4. Termine cada versão do procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um procedimento `Sub` para lançar uma transação em relação ao saldo de um cliente. Ele usa a palavra-chave `Overloads` para definir duas versões do procedimento, uma que aceita o cliente pelo nome e a outra por número da conta.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer`e, em seguida, usar a mesma instrução de chamada em ambos os casos.  
  
 Para obter informações sobre como chamar essas versões do procedimento de `post`, consulte [como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Verifique se cada uma de suas versões sobrecarregadas tem o mesmo nome de procedimento, mas uma lista de parâmetros diferente.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)
- [Resolução de Sobrecarga](./overload-resolution.md)
