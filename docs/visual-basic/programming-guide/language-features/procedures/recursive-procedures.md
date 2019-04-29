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
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791821"
---
# <a name="recursive-procedures-visual-basic"></a>Procedimentos recursivos (Visual Basic)
Um *recursiva* procedimento é aquele que chama a mesmo. Em geral, isso não é a maneira mais eficiente para gravar o código do Visual Basic.  
  
 O procedimento a seguir usa a recursão para calcular o fatorial de seu argumento original.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considerações sobre procedimentos recursivos  
 **Das condições de limitação**. Você deve projetar um procedimento recursivo para testar a pelo menos uma condição que pode encerrar a recursão, e você também deve tratar o caso em que nenhuma dessas condições for atendida dentro de um número razoável de chamadas recursivas. Pelo menos uma condição que pode ser atendida sem falhar, o procedimento é executado um alto risco de execução em um loop infinito.  
  
 **Uso de Memória**. Seu aplicativo tem uma quantidade limitada de espaço para as variáveis locais. Cada vez que um procedimento chama a próprio, ele usa muito mais do que o espaço para cópias adicionais de suas variáveis locais. Se esse processo continua indefinidamente, ela eventualmente fará com que um <xref:System.StackOverflowException> erro.  
  
 **Eficiência**. Quase sempre você pode substituir um loop de recursão. Um loop não tem a sobrecarga de passagem de argumentos, inicializando o armazenamento adicional e retornar valores. O desempenho pode ser muito melhor sem chamadas recursivas.  
  
 **Recursão mútua**. Você pode observar um desempenho muito ruim, ou até mesmo um loop infinito, se dois procedimentos chamam uns aos outros. Esse design apresenta os mesmos problemas de um procedimento recursivo única, mas pode ser difícil de detectar e depurar.  
  
 **Chamando com parênteses**. Quando um `Function` procedimento chama a mesmo recursivamente, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos. Caso contrário, o nome da função é executado como que representa o valor de retorno da função.  
  
 **Teste**. Se você escrever um procedimento recursivo, você deve testá-lo com muito cuidado para garantir que ele atende às sempre alguma condição de limitação. Você também deve garantir que você não pode ficar sem memória devido a ter muitas chamadas recursivas.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.StackOverflowException>
- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
