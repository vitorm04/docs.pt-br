---
title: Procedimentos recursivos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 8ea7741c943ea563fbd0c7649ac0ff85b2f9ebba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-procedures-visual-basic"></a>Procedimentos recursivos (Visual Basic)
Um *recursiva* procedimento é aquele que chama a mesmo. Em geral, isso não é a maneira mais eficiente para gravar o código do Visual Basic.  
  
 O procedimento a seguir usa a recursão para calcular o fatorial do argumento original.  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considerações sobre com procedimentos recursivos  
 **Das condições de limitação**. Você deve criar um procedimento recursiva para testar a pelo menos uma condição que pode encerrar a recursão, e você também deve tratar o caso em que nenhuma dessas condições é atendida dentro de um número razoável de chamadas recursivas. Pelo menos uma condição que possa ser atendida sem falhar, o procedimento é executado um alto risco de execução em um loop infinito.  
  
 **Uso de Memória**. Seu aplicativo tem uma quantidade limitada de espaço para variáveis locais. Cada vez que um procedimento chama a mesmo, ele usa mais do que o espaço para cópias adicionais de suas variáveis locais. Se esse processo continua indefinidamente, eventualmente faz com que um <xref:System.StackOverflowException> erro.  
  
 **Eficiência**. Quase sempre, você pode substituir um loop de recursão. Um loop não tem a sobrecarga de argumentos de passagem, inicializar o armazenamento adicional e retornar valores. O desempenho pode ser muito melhor sem chamadas recursivas.  
  
 **Recursão mútua**. Você pode observar muito baixo desempenho ou até mesmo um loop infinito, se dois procedimentos chamam uma à outra. Esse design apresenta os mesmos problemas como um procedimento único recursiva, mas pode ser difícil de detectar e depurar.  
  
 **Chamando com parênteses**. Quando uma `Function` procedimento chama recursivamente a mesmo, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos. Caso contrário, o nome da função é executado como que representa o valor de retorno da função.  
  
 **Teste**. Se você gravar um procedimento recursiva, você deve testá-lo com muito cuidado para garantir que ele atenda sempre alguma condição de limitação. Você também deve garantir que você não pode ficar sem memória devido a ter muitas chamadas recursivas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.StackOverflowException>  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Solução de problemas de exceções: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
