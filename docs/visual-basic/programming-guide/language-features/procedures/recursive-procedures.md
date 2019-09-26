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
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274349"
---
# <a name="recursive-procedures-visual-basic"></a>Procedimentos recursivos (Visual Basic)

Um procedimento *recursivo* é aquele que chama a si mesmo. Em geral, essa não é a maneira mais eficiente de escrever Visual Basic código.  
  
 O procedimento a seguir usa a recursão para calcular o fatorial de seu argumento original.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considerações com procedimentos recursivos

 **Limitando condições**. Você deve criar um procedimento Recursivo para testar pelo menos uma condição que pode encerrar a recursão e também deve lidar com o caso em que nenhuma condição é satisfeita dentro de um número razoável de chamadas recursivas. Sem pelo menos uma condição que possa ser atendida sem falha, o procedimento executa um alto risco de execução em um loop infinito.

 **Uso de Memória**. Seu aplicativo tem uma quantidade limitada de espaço para variáveis locais. Cada vez que um procedimento chama a si mesmo, ele usa mais desse espaço para cópias adicionais de suas variáveis locais. Se esse processo continuar indefinidamente, ele eventualmente causará um <xref:System.StackOverflowException> erro.

 **Eficiência**. Quase sempre é possível substituir um loop pela recursão. Um loop não tem a sobrecarga de passar argumentos, inicializar armazenamento adicional e retornar valores. Seu desempenho pode ser muito melhor sem chamadas recursivas.

 **Recursão mútua**. Você pode observar um desempenho muito ruim, ou até mesmo um loop infinito, se dois procedimentos chamarem uns aos outros. Esse tipo de design apresenta os mesmos problemas que um único procedimento Recursivo, mas pode ser mais difícil de detectar e depurar.

 **Chamada com parênteses**. Quando um `Function` procedimento chama-se recursivamente, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos. Caso contrário, o nome da função será obtido como representando o valor de retorno da função.

 **Testando**. Se você escrever um procedimento Recursivo, deverá testá-lo com muito cuidado para garantir que ele sempre atenda a alguma condição de limitação. Você também deve garantir que não seja possível ficar sem memória devido a ter muitas chamadas recursivas.

## <a name="see-also"></a>Consulte também

- <xref:System.StackOverflowException>
- [Procedimentos](index.md)
- [Subprocedimentos](sub-procedures.md)
- [Procedimentos de Função](function-procedures.md)
- [Procedimentos de Propriedade](property-procedures.md)
- [Procedimentos de Operador](operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](procedure-parameters-and-arguments.md)
- [Sobrecarga de Procedimento](procedure-overloading.md)
- [Solução de problemas de Procedimentos](troubleshooting-procedures.md)
- [Estruturas de Loop](../control-flow/loop-structures.md)
