---
title: "Como enumerar um subconjunto de filas de impressão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 397ec40e2d8a0694e208296593687e9268546fc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Como enumerar um subconjunto de filas de impressão
Uma situação comum enfrentada por profissionais da TI (tecnologia da informação) que gerenciam um conjunto de impressoras de toda a empresa é gerar uma lista de impressoras que tenham determinadas características. Essa funcionalidade é fornecida pelo <xref:System.Printing.PrintServer.GetPrintQueues%2A> método de um <xref:System.Printing.PrintServer> objeto e o <xref:System.Printing.EnumeratedPrintQueueTypes> enumeração.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o código começa criando uma matriz de sinalizadores que especifica as características das filas de impressão que desejamos listar. Neste exemplo, estamos buscando filas de impressão que estejam instaladas localmente no servidor de impressão e que sejam compartilhadas. O <xref:System.Printing.EnumeratedPrintQueueTypes> enumeração fornece muitas outras possibilidades.  
  
 O código, em seguida, cria um <xref:System.Printing.LocalPrintServer> do objeto, uma classe derivada de <xref:System.Printing.PrintServer>. O servidor de impressão local é o computador no qual o aplicativo está em execução.  
  
 O último passo significativo é passar a matriz de <xref:System.Printing.PrintServer.GetPrintQueues%2A> método.  
  
 Por fim, os resultados são apresentados ao usuário.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Você pode estender este exemplo fazendo com que o loop `foreach` que passa por cada fila de impressão faça um exame adicional. Por exemplo, você pode retirar as impressoras que dão suporte a impressão de dois lados fazendo com que a chamada de loop cada fila de impressão <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> método e teste o valor retornado para a presença de duplicação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
