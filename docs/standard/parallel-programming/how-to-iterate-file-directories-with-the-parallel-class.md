---
title: "Como: Fazer iterações de diretórios de arquivos com a Classe Paralela"
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
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c21aadf70eaccafc8c8ec9c4efefff1c66abc6b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Como: Fazer iterações de diretórios de arquivos com a Classe Paralela
Em muitos casos, a iteração de arquivo é uma operação que pode ser facilmente colocados em paralelo. O tópico [como: iterar diretórios de arquivos com PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) mostra a maneira mais fácil para executar essa tarefa para muitos cenários. No entanto, complicações podem ocorrer quando seu código precisa lidar com vários tipos de exceções que podem surgir ao acessar o sistema de arquivos. O exemplo a seguir mostra uma abordagem para o problema. Ele usa uma iteração de pilha para percorrer todos os arquivos e pastas em um diretório especificado e ele permite que seu código para capturar e manipular várias exceções. É claro que, de forma que você manipule as exceções fica a seu critério.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir itera os diretórios sequencialmente, mas processa os arquivos em paralelo. Isso provavelmente é a melhor abordagem quando você tem uma grande proporção de diretório do arquivo. Também é possível paralelizar a iteração de diretório e acessar cada arquivo em sequência. Provavelmente não é eficiente para paralelizar os loops, a menos que especificamente destinados uma máquina com um grande número de processadores. No entanto, como em todos os casos, você deve testar seu aplicativo cuidadosamente para determinar a melhor abordagem.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Neste exemplo, o arquivo de e/s é executado de maneira síncrona. Ao lidar com arquivos grandes ou conexões lentas de rede, talvez seja preferível para acessar os arquivos de forma assíncrona. Você pode combinar as técnicas de e/s assíncronas com iteração paralela. Para obter mais informações, consulte [Programação assíncrona do .NET Framework tradicional e TPL](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 O exemplo usa o local `fileCount` variável para manter uma contagem do número total de arquivos processados. Porque a variável pode ser acessada simultaneamente por várias tarefas, o acesso a ele é sincronizado ao chamar o <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> método.  
  
 Observe que, se uma exceção é lançada no principal thread, os threads que são iniciados pelo <xref:System.Threading.Tasks.Parallel.ForEach%2A> método pode continuar a executar. Para interromper esses threads, você pode definir uma variável booleana em seus manipuladores de exceção e verificar seu valor em cada iteração do loop paralelo. Se o valor indica que uma exceção foi gerada, use o <xref:System.Threading.Tasks.ParallelLoopState> variável interromper ou interrupção do loop. Para obter mais informações, consulte [como: interromper ou interromper um loop Parallel. for](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).  
  
## <a name="see-also"></a>Consulte também  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
