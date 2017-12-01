---
title: LINQ paralelo (PLINQ)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0028d3d8c30bbc7f0592a4462ca1eeb80c8b1f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parallel-linq-plinq"></a>LINQ paralelo (PLINQ)
LINQ paralelo (PLINQ) é uma implementação paralela de objetos LINQ to. PLINQ implementa o conjunto completo de operadores de consulta padrão LINQ como métodos de extensão para o <xref:System.Linq> namespace e tem operadores adicionais para operações paralelas. PLINQ combina a simplicidade e a legibilidade de sintaxe LINQ com o poder da programação paralela. Assim como código que tem como destino a biblioteca paralela de tarefas, consultas PLINQ ampliar o grau de simultaneidade com base nos recursos do computador host.  
  
 Em muitos cenários, PLINQ pode aumentar significativamente a velocidade de LINQ para consultas de objetos usando todos os núcleos disponíveis no computador host com mais eficiência. Esse aumento do desempenho traz a potência de computação de alto desempenho para a área de trabalho.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução ao PLINQ](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [Preservação da ordem em PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [Opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [Como criar e executar uma consulta PLINQ simples](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [Como controlar a ordem em uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [Como combinar consultas LINQ paralelas e sequenciais](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [Como tratar exceções em uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [Como cancelar uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [Como escrever uma função de agregação PLINQ personalizada](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [Como especificar o modo de execução em PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [Como especificar opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [Como iterar diretórios de arquivos com PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [Como avaliar o desempenho da consulta PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [Exemplo de dados PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable>  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
