---
title: "Noções básicas sobre agilização em PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3373cb6a2c535bd7d42eb062e1f9727952f7cfb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-speedup-in-plinq"></a>Noções básicas sobre agilização em PLINQ
O objetivo principal do PLINQ é acelerar a execução do LINQ para consultas de objetos, executando os delegados de consulta em paralelo em computadores com vários núcleos. PLINQ funciona melhor quando o processamento de cada elemento em uma coleção de origem é independente, sem estado compartilhado envolvidas entre os delegados individuais. Essas operações são comuns em LINQ para objetos e em PLINQ e são chamadas de "*agradavelmente paralelo*" porque elas se prestam facilmente para o planejamento de vários threads. No entanto, nem todas as consultas consistem inteiramente em operações agradavelmente paralelo; Na maioria dos casos, uma consulta envolve alguns operadores que o não pode ser paralelizado ou que lenta a execução paralela. E até mesmo com consultas que são totalmente agradavelmente paralelas, PLINQ deve ainda dividir a fonte de dados e agendar o trabalho em threads e geralmente mesclar os resultados quando a consulta é concluída. Todas essas operações adicionar ao custo computacional de paralelização; Esses custos de adição de paralelização são chamados *sobrecarga*. Para obter um desempenho ideal em uma consulta PLINQ, o objetivo é maximizar as partes agradavelmente paralelas e minimizar as partes que exigem a sobrecarga. Este artigo fornece informações que ajudarão você a escrever consultas PLINQ que são mais eficientes possível, enquanto ainda produzindo resultados corretos.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Fatores que afetam o desempenho da consulta PLINQ  
 As seções a seguir lista alguns dos principais fatores que afetam o desempenho consulta paralela. Essas são instruções gerais que, por si só, não são suficientes para prever o desempenho de consulta em todos os casos. Como sempre, é importante medir o desempenho real de consultas específicas em computadores com uma variedade de configurações de representante e carrega.  
  
1.  Custo computacional geral do trabalho.  
  
     Para obter o aumento de velocidade, uma consulta PLINQ deve ter suficiente trabalho agradavelmente paralelo para deslocar a sobrecarga. O trabalho pode ser expresso como o custo computacional de cada representante multiplicado pelo número de elementos na coleção de origem. Supondo que uma operação pode ser colocado em paralelo, computacionalmente mais caro é, maior a possibilidade de aumento de velocidade. Por exemplo, se uma função usa um milissegundo para executar, uma consulta sequencial em 1000 elementos levará um segundo para executar essa operação, enquanto um paralelo de consulta em um computador com quatro núcleos pode levar apenas 250 milissegundos. Isso resulta em um aumento de velocidade de 750 milissegundos. Se a função necessário um segundo a ser executada para cada elemento, o aumento de velocidade seria 750 segundos. Se o representante é muito dispendioso, PLINQ pode oferecer um aumento de velocidade significativo com apenas alguns itens na coleção de origem. Por outro lado, coleções de origem pequeno com delegados triviais geralmente não são bons candidatos para PLINQ.  
  
     No exemplo a seguir, queryA provavelmente é uma boa candidata para PLINQ, supondo que sua função Select envolve uma grande parte do trabalho. queryB provavelmente não é um bom candidato porque não há suficiente trabalho na instrução Select, e a sobrecarga de paralelização serão deslocadas a maior parte ou todo o aumento de velocidade.  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2.  O número de núcleos lógicos no sistema (grau de paralelismo).  
  
     Esse ponto é um resultado óbvio para a seção anterior, consultas paralelas agradavelmente executadas mais rapidamente em computadores com mais núcleos porque o trabalho pode ser dividido entre mais threads simultâneos. A quantidade geral de aumento de velocidade depende de qual porcentagem do trabalho geral da consulta é paralelizável. No entanto, não presuma que todas as consultas serão executado duas vezes mais rápida em um computador com oito núcleos como um computador de quatro núcleos. Quando o ajuste de consultas para otimizar o desempenho, é importante medir os resultados reais em computadores com vários números de núcleos. Esse ponto está relacionado ao ponto #1: grandes conjuntos de dados são necessários para tirar proveito dos recursos de computação maiores.  
  
3.  O número e tipo de operações.  
  
     PLINQ fornece o operador AsOrdered para situações em que é necessário para manter a ordem dos elementos na sequência de origem. Há um custo associado com a ordenação, mas esse custo é geralmente pequena. Da mesma forma, operações de GroupBy e Join causar sobrecarga. PLINQ funciona melhor quando é permitido para processar os elementos na coleção de origem em qualquer ordem e passá-las para o próximo operador assim que estiverem prontas. Para saber mais, veja [Preservação da ordem em PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
4.  O formulário da execução da consulta.  
  
     Se você estiver armazenando os resultados de uma consulta chamando ToArray ou ToList, os resultados de todos os threads paralelos devem ser mesclados na estrutura de dados único. Isso envolve um custo computacional inevitável. Da mesma forma, se você iterar os resultados usando um loop foreach (para cada um no Visual Basic), os resultados de threads de trabalho precisam ser serializados para o thread de enumerador. Mas se você quiser executar alguma ação com base no resultado de cada thread, você pode usar o método ForAll para executar esse trabalho em vários threads.  
  
5.  O tipo de opções de mesclagem.  
  
     PLINQ pode ser configurado para o buffer de saída e produzi-las em partes ou todos de uma vez, depois que o conjunto de resultados inteiro é produzido, ou se encontram aos resultados individuais de fluxo como eles são produzidos. O primeiro resultado é o menor tempo de execução geral e a último resulta em menor latência entre elementos gerou.  Enquanto as opções de mesclagem nem sempre têm um grande impacto no desempenho geral da consulta, elas podem afetar o desempenho percebido porque eles controlam quanto tempo um usuário deve aguardar para ver os resultados. Para saber mais, veja [Opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
6.  O tipo de particionamento.  
  
     Em alguns casos, uma consulta PLINQ em uma coleção de origem indexável pode resultar em uma carga de trabalho desbalanceada. Quando isso ocorrer, você poderá aumentar o desempenho da consulta ao criar um particionador personalizado. Para saber mais, veja [Particionadores personalizados para PLINQ e TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Quando o PLINQ escolhe modo sequencial  
 PLINQ sempre tenta executar uma consulta de pelo menos tão rápida como a consulta executaria sequencialmente. Embora PLINQ não examinar como computacionalmente caras de representantes de usuário são ou grande como a fonte de entrada é, ele parecerá para determinada consulta "formas". Especificamente, ele procura por operadores de consulta ou combinações de operadores que causam normalmente uma consulta para executar mais lentamente no modo paralelo. Quando encontra essas formas, PLINQ por padrão reverterá ao modo sequencial.  
  
 No entanto, após a medir o desempenho de consulta específico, você pode determinar que ele é realmente executado mais rapidamente no modo paralelo. Nesses casos, você pode usar o <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> sinalizador por meio de <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> método para instruir o PLINQ para paralelizar a consulta. Para saber mais, veja [Como especificar o modo de execução em PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
 A lista a seguir descreve as formas de consulta PLINQ por padrão será executado em modo sequencial:  
  
-   Consultas que contêm um Select, Where, indexada SelectMany indexada, ou cláusula de ElementAt após um operador de classificação ou filtragem removidos ou reorganizados índices originais.  
  
-   Consultas que contêm um salto Take, TakeWhile, operador SkipWhile e onde índices na sequência de origem não estão na ordem original.  
  
-   As consultas que contêm Zip ou SequenceEquals, a menos que uma das fontes de dados tem um índice solicitado originalmente e fonte de dados é indexável (ou seja, uma matriz ou IList(T)).  
  
-   Consultas que contêm Concat, a menos que ela é aplicada a fontes de dados indexáveis.  
  
-   Consultas que contêm inversa, a menos que aplicado a uma fonte de dados indexáveis.  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
