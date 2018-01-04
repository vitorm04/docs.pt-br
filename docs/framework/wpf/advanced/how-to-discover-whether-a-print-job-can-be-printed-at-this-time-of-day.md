---
title: "Como descobrir se um trabalho de impressão pode ser impresso a esta hora do dia"
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
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef9da205792823b7069024c5e4a3e9ac80d60a24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Como descobrir se um trabalho de impressão pode ser impresso a esta hora do dia
Filas de impressão não estão sempre disponíveis 24 horas por dia. Eles têm propriedades de tempo de início e término que podem ser definidas para torná-las indisponíveis em determinados momentos do dia. Esse recurso pode ser usado, por exemplo, para reservar uma impressora para uso exclusivo de um determinado departamento após as 17h. Esse departamento teria uma fila diferente na impressora do que a que outros departamentos usam. A fila para os outros departamentos seria definida como indisponível após as 17h, enquanto a fila para o departamento favorecido poderia ser definida para estar sempre disponível.  
  
 Além disso, os próprios trabalhos de impressão podem ser definidos para serem impressos apenas dentro de um período especificado.  
  
 O <xref:System.Printing.PrintQueue> e <xref:System.Printing.PrintSystemJobInfo> classes expostas no [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] fornecem um meio de verificar remotamente se um determinado trabalho de impressão pode imprimir em uma determinada fila no momento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é um exemplo que pode diagnosticar problemas com um trabalho de impressão.  
  
 Há duas etapas principais para esse tipo de função, da seguinte maneira.  
  
1.  Leitura de <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades do <xref:System.Printing.PrintQueue> para determinar se o horário atual está entre eles.  
  
2.  Leitura de <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> e <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> propriedades do <xref:System.Printing.PrintSystemJobInfo> para determinar se o horário atual está entre eles.  
  
 Mas complicações surgem do fato de que essas propriedades não são <xref:System.DateTime> objetos. Em vez disso, eles são <xref:System.Int32> objetos que expressa a hora do dia, como o número de minutos decorridos desde a meia-noite. Além disso, não se trata de meia-noite no fuso horário atual, mas meia-noite no UTC (Tempo Universal Coordenado).  
  
 O primeiro exemplo de código apresenta o método estático **ReportQueueAndJobAvailability**, que é passado um <xref:System.Printing.PrintSystemJobInfo> e chama métodos auxiliares para determinar se o trabalho pode ser impresso no horário atual e, se não, quando pode ser impresso. Observe que um <xref:System.Printing.PrintQueue> não for passado para o método. Isso ocorre porque o <xref:System.Printing.PrintSystemJobInfo> inclui uma referência à fila na sua <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> propriedade.  
  
 Os métodos subordinados incluem sobrecarregados **ReportAvailabilityAtThisTime** método que pode receber um <xref:System.Printing.PrintQueue> ou um <xref:System.Printing.PrintSystemJobInfo> como um parâmetro. Também há um **TimeConverter.ConvertToLocalHumanReadableTime**. Todos esses métodos são discutidos abaixo.  
  
 O método **ReportQueueAndJobAvailability** começa verificando se a fila ou o trabalho de impressão está indisponível no momento. Se um deles estiver indisponível, ele verificará se a fila está indisponível. Se ela não estiver disponível, o método relatará esse fato e a hora em que a fila estará disponível novamente. Em seguida, ele verifica o trabalho e, se ele estiver indisponível, relatará o próximo intervalo em que ela pode ser impressa. Por fim, o método relata o horário mais próximo em que o trabalho pode ser impresso. Ele é o segundo dos dois horários a seguir.  
  
-   A hora em que a fila de impressão ficará disponível.  
  
-   A hora em que o trabalho de impressão ficará disponível.  
  
 Ao reportar horários do dia, o <xref:System.DateTime.ToShortTimeString%2A> método também é chamado porque esse método suprime os anos, meses e dias da saída. Você não pode restringir a disponibilidade de uma fila de impressão ou de um trabalho de impressão para dias, meses ou anos específicos.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 As duas sobrecargas do **ReportAvailabilityAtThisTime** método são idênticos, exceto o tipo passado a elas, portanto, somente o <xref:System.Printing.PrintQueue> versão é apresentada a seguir.  
  
> [!NOTE]
>  O fato de que os métodos são idênticos exceto pelo tipo levanta a questão de por que o exemplo não cria um método genérico **ReportAvailabilityAtThisTime\<T>**. O motivo é que tal método precisa ser restrito a uma classe que tem o **StartTimeOfDay** e **UntilTimeOfDay** propriedades que chama o método, mas um método genérico só pode ser restrito a um classe e a única classe comuns em um único <xref:System.Printing.PrintQueue> e <xref:System.Printing.PrintSystemJobInfo> a herança árvore é <xref:System.Printing.PrintSystemObject> que não tem tais propriedades.  
  
 O **ReportAvailabilityAtThisTime** método (apresentado no código de exemplo abaixo) começa inicializando uma <xref:System.Boolean> Sentinela variável `true`. Ele será redefinido para `false` se a fila não estiver disponível.  
  
 Em seguida, o método verifica se as horas de início e "até" são idênticas. Se forem, a fila sempre estará disponível, então o método retornará `true`.  
  
 Se a fila não estiver disponível o tempo todo, o método usa estático <xref:System.DateTime.UtcNow%2A> propriedade para obter a hora atual como uma <xref:System.DateTime> objeto. (Não precisamos do tempo local porque o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades são na hora UTC.)  
  
 No entanto, essas duas propriedades não são <xref:System.DateTime> objetos. Eles são <xref:System.Int32>s expressando o horário como o número de minutos após-meia-noite-UTC. Portanto, precisamos converter nosso <xref:System.DateTime> objeto minutos após meia-noite. Quando isso é feito, o método simplesmente verifica se "agora" está entre as horas de início da fila e "até", define a sentinela como falsa caso "agora" não esteja entre as duas horas e retorna a sentinela.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 O método **TimeConverter.ConvertToLocalHumanReadableTime** (apresentado no código de exemplo abaixo) não usa nenhum método introduzido com [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], portanto, a discussão é breve. O método tem uma tarefa de conversão dupla: ele deve receber um inteiro expressando minutos após a meia-noite e convertê-lo em um horário legível, e precisa convertê-lo no horário local. Isso é feito criando primeiro uma <xref:System.DateTime> objeto que é definido para meia-noite UTC e, em seguida, usa o <xref:System.DateTime.AddMinutes%2A> método para adicionar os minutos que foram passados para o método. Isso retorna um novo <xref:System.DateTime> expressando o horário original que foi passado para o método. O <xref:System.DateTime.ToLocalTime%2A> método converte isso para o horário local.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)
