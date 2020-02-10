---
title: Como enumerar um subconjunto de filas de impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094534"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Como enumerar um subconjunto de filas de impressão
Uma situação comum enfrentada por profissionais da TI (tecnologia da informação) que gerenciam um conjunto de impressoras de toda a empresa é gerar uma lista de impressoras que tenham determinadas características. Essa funcionalidade é fornecida pelo método <xref:System.Printing.PrintServer.GetPrintQueues%2A> de um objeto <xref:System.Printing.PrintServer> e a enumeração <xref:System.Printing.EnumeratedPrintQueueTypes>.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o código começa criando uma matriz de sinalizadores que especifica as características das filas de impressão que desejamos listar. Neste exemplo, estamos buscando filas de impressão que estejam instaladas localmente no servidor de impressão e que sejam compartilhadas. A enumeração de <xref:System.Printing.EnumeratedPrintQueueTypes> fornece muitas outras possibilidades.  
  
 Em seguida, o código cria um objeto <xref:System.Printing.LocalPrintServer>, uma classe derivada de <xref:System.Printing.PrintServer>. O servidor de impressão local é o computador no qual o aplicativo está em execução.  
  
 A última etapa significativa é passar a matriz para o método <xref:System.Printing.PrintServer.GetPrintQueues%2A>.  
  
 Por fim, os resultados são apresentados ao usuário.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Você pode estender este exemplo fazendo com que o loop `foreach` que passa por cada fila de impressão faça um exame adicional. Por exemplo, você poderia retirar as impressoras que não dão suporte à impressão em duas laterais fazendo com que o loop chame cada método de <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> da fila de impressão e teste o valor retornado para a presença de Duplexing.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão geral da impressão](printing-overview.md)
- [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer)
