---
title: "Procedimentos recursivos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "funções [Visual Basic], chamando recursivamente"
  - "procedimentos, Chamando "
  - "procedimentos, recursivo"
  - "procedimentos, que se chamam"
  - "recursão"
  - "procedimentos recursivos"
  - "código do Visual Basic, procedimentos"
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedimentos recursivos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A  *recursiva* procedimento é aquele que chama a mesmo.  Em geral, isso não é a maneira mais eficiente gravar [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.  
  
 O procedimento a seguir usa a recursão para calcular o fatorial de seu argumento original.  
  
 [!code-vb[VbVbcnProcedures#51](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## Considerações com procedimentos recursiva  
 **Condições limitantes**.  Você deve criar um procedimento recursiva para testar a pelo menos uma condição que pode finalizar a recursão e você também deve tratar o caso em que nenhuma dessas condições for satisfeita dentro de um número razoável de chamadas recursivas.  Pelo menos uma condição que pode ser atendida sem falha, o seu procedimento é executado um alto risco de execução em um loop infinito.  
  
 **Uso de memória**.  Seu aplicativo tem uma quantidade limitada de espaço para as variáveis locais.  Sempre que um procedimento chama a mesmo, ele usa muito mais do que o espaço para cópias adicionais de variáveis locais.  Se esse processo continua indefinidamente, ele eventualmente causará um <xref:System.StackOverflowException> erro.  
  
 **Eficiência**.  Quase sempre, você pode substituir um loop de recursão.  Um loop não tem a sobrecarga de passando argumentos, Inicializando armazenamento adicional e retornar valores.  O desempenho pode ser muito melhor sem chamadas recursivas.  
  
 **Recursão mútua**.  Você pode observar um desempenho muito fraco ou até mesmo um loop infinito, se dois procedimentos chamam uns aos outros.  Tal um design apresenta os mesmos problemas como um procedimento único recursiva, mas pode ser difícil de detectar e depurar.  
  
 **Chamando com parênteses**.  Quando um `Function` procedimento chama a mesma recursivamente, você deve seguir o nome do procedimento com parênteses, mesmo se não houver nenhuma lista de argumentos.  Caso contrário, o nome da função será executado como que representa o valor de retorno da função.  
  
 **Testes**.  Se você escrever um procedimento recursiva, você deve testá\-lo com muito cuidado para certificar\-se de que ele sempre atende a alguma condição de limitação.  Você também deve garantir que você não pode ficar sem memória devido a ter muitas chamadas recursivas.  
  
## Consulte também  
 <xref:System.StackOverflowException>   
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Solucionando problemas de procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Exceções de solução de problemas: System.StackOverflowException](../Topic/Troubleshooting%20Exceptions:%20System.StackOverflowException.md)