---
title: Procedimentos recursivos (Visual Basic) | Documentos do Microsoft
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
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
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
ms.openlocfilehash: 9fc95cd5f7cfd5637f6282c6ef571eb81bac1816
ms.lasthandoff: 03/13/2017

---
# <a name="recursive-procedures-visual-basic"></a>Procedimentos recursivos (Visual Basic)
A *recursiva* procedimento é aquela que chama a mesmo. Em geral, isso não é a maneira mais eficiente para gravar [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.  
  
 O procedimento a seguir usa a recursão para calcular o fatorial do argumento original.  
  
 [!code-vb[VbVbcnProcedures&#51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considerações sobre com procedimentos recursivos  
 **Limitando condições**. Você deve criar um procedimento de recursiva para testar a pelo menos uma condição que pode finalizar a recursão e você também deverá manipular o caso em que nenhuma dessas condições for atendida dentro de um número razoável de chamadas recursivas. Pelo menos uma condição que pode ser atendida sem falhas, o procedimento é executado um alto risco de execução em um loop infinito.  
  
 **Uso de memória**. Seu aplicativo tem uma quantidade limitada de espaço para variáveis locais. Cada vez que um procedimento chama a próprio, ele usa mais do que o espaço para cópias adicionais de suas variáveis locais. Se esse processo continua indefinidamente, eventualmente causar um <xref:System.StackOverflowException>erro.</xref:System.StackOverflowException>  
  
 **Eficiência**. Você pode substituir quase sempre um loop de recursão. Um loop não tem a sobrecarga de passagem de argumentos, inicializando o armazenamento adicional e retornar valores. O desempenho pode ser muito melhor sem chamadas recursivas.  
  
 **Recursão mútua**. Você pode observar um desempenho muito ruim, ou até mesmo um loop infinito, se dois procedimentos chamam uns aos outros. Esse design apresenta os mesmos problemas como um procedimento único recursiva, mas pode ser difícil de detectar e depurar.  
  
 **Chamando com parênteses**. Quando uma `Function` procedimento chama a mesmo recursivamente, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos. Caso contrário, o nome de função é usado como o que representa o valor de retorno da função.  
  
 **Teste**. Se você escrever um procedimento recursiva, você deve testá-lo com muito cuidado para certificar-se de que ele atende sempre alguma condição de limitação. Você também deve garantir que você não pode ficar sem memória devido a ter muitas chamadas recursivas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.StackOverflowException></xref:System.StackOverflowException>   
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Solução de problemas de exceções: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
