---
title: 'Como: Descobrir se um trabalho de impressão pode ser impresso a esta hora do dia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947805"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Como: Descobrir se um trabalho de impressão pode ser impresso a esta hora do dia
Filas de impressão não estão sempre disponíveis 24 horas por dia. Eles têm propriedades de tempo de início e término que podem ser definidas para torná-las indisponíveis em determinados momentos do dia. Esse recurso pode ser usado, por exemplo, para reservar uma impressora para uso exclusivo de um determinado departamento após as 17h. Esse departamento teria uma fila diferente na impressora do que a que outros departamentos usam. A fila para os outros departamentos seria definida como indisponível após as 17h, enquanto a fila para o departamento favorecido poderia ser definida para estar sempre disponível.  
  
 Além disso, os próprios trabalhos de impressão podem ser definidos para serem impressos apenas dentro de um período especificado.  
  
 As <xref:System.Printing.PrintQueue> classes <xref:System.Printing.PrintSystemJobInfo> e expostas nas APIs do Microsoft .NET Framework fornecem um meio para verificar remotamente se um determinado trabalho de impressão pode imprimir em uma determinada fila na hora atual.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é um exemplo que pode diagnosticar problemas com um trabalho de impressão.  
  
 Há duas etapas principais para esse tipo de função, da seguinte maneira.  
  
1. Leia as <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> propriedades <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> e de <xref:System.Printing.PrintQueue> para determinar se a hora atual está entre elas.  
  
2. Leia as <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> propriedades <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> e de <xref:System.Printing.PrintSystemJobInfo> para determinar se a hora atual está entre elas.  
  
 Mas complicações surgem do fato de que essas propriedades não <xref:System.DateTime> são objetos. Em vez disso <xref:System.Int32> , eles são objetos que expressam a hora do dia como o número de minutos desde a meia-noite. Além disso, não se trata de meia-noite no fuso horário atual, mas meia-noite no UTC (Tempo Universal Coordenado).  
  
 O primeiro exemplo de código apresenta o método estático **ReportQueueAndJobAvailability**, que é passado <xref:System.Printing.PrintSystemJobInfo> a e chama métodos auxiliares para determinar se o trabalho pode ser impresso na hora atual e, se não, quando ele pode ser impresso. Observe que um <xref:System.Printing.PrintQueue> não é passado para o método. Isso ocorre porque o <xref:System.Printing.PrintSystemJobInfo> inclui uma referência à fila em sua <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> propriedade.  
  
 Os métodos subordinados incluem o método **ReportAvailabilityAtThisTime** sobrecarregado que pode usar um <xref:System.Printing.PrintQueue> ou um <xref:System.Printing.PrintSystemJobInfo> parâmetro. Também há um **TimeConverter.ConvertToLocalHumanReadableTime**. Todos esses métodos são discutidos abaixo.  
  
 O método **ReportQueueAndJobAvailability** começa verificando se a fila ou o trabalho de impressão está indisponível no momento. Se um deles estiver indisponível, ele verificará se a fila está indisponível. Se ela não estiver disponível, o método relatará esse fato e a hora em que a fila estará disponível novamente. Em seguida, ele verifica o trabalho e, se ele estiver indisponível, relatará o próximo intervalo em que ela pode ser impressa. Por fim, o método relata o horário mais próximo em que o trabalho pode ser impresso. Ele é o segundo dos dois horários a seguir.  
  
- A hora em que a fila de impressão ficará disponível.  
  
- A hora em que o trabalho de impressão ficará disponível.  
  
 Ao relatar horas do dia, o <xref:System.DateTime.ToShortTimeString%2A> método também é chamado porque esse método suprime os anos, os meses e os dias da saída. Você não pode restringir a disponibilidade de uma fila de impressão ou de um trabalho de impressão para dias, meses ou anos específicos.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 As duas sobrecargas do método **ReportAvailabilityAtThisTime** são idênticas, exceto pelo tipo passado para elas, de modo que <xref:System.Printing.PrintQueue> apenas a versão seja apresentada abaixo.  
  
> [!NOTE]
> O fato de que os métodos são idênticos exceto pelo tipo levanta a questão de por que o exemplo não cria um método genérico **ReportAvailabilityAtThisTime\<T>** . O motivo é que tal método teria que ser restrito a uma classe que tem as propriedades **StartTimeOfDay** e **UntilTimeOfDay** que o método chama, mas um método genérico só pode ser restrito a uma única classe e à única classe comum para ambos e na árvore de herança é <xref:System.Printing.PrintSystemObject> que não tem essas propriedades. <xref:System.Printing.PrintSystemJobInfo> <xref:System.Printing.PrintQueue>  
  
 O método **ReportAvailabilityAtThisTime** (apresentado no exemplo de código abaixo) começa inicializando uma <xref:System.Boolean> variável Sentinel para `true`. Ele será redefinido para `false` se a fila não estiver disponível.  
  
 Em seguida, o método verifica se as horas de início e "até" são idênticas. Se forem, a fila sempre estará disponível, então o método retornará `true`.  
  
 Se a fila não estiver disponível o tempo todo, o método usará a <xref:System.DateTime.UtcNow%2A> propriedade estática para obter a hora atual como <xref:System.DateTime> um objeto. (Não precisamos do horário local porque as <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> Propriedades e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> estão em hora UTC.)  
  
 No entanto, essas duas propriedades <xref:System.DateTime> não são objetos. Eles estão <xref:System.Int32>expressando o tempo como o número de minutos após-UTC-meia-noite. Então, precisamos converter nosso <xref:System.DateTime> objeto em minutos após a meia-noite. Quando isso é feito, o método simplesmente verifica se "agora" está entre as horas de início da fila e "até", define a sentinela como falsa caso "agora" não esteja entre as duas horas e retorna a sentinela.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 O método **TimeConverter. ConvertToLocalHumanReadableTime** (apresentado no exemplo de código abaixo) não usa nenhum método introduzido com Microsoft .NET Framework, portanto, a discussão é breve. O método tem uma tarefa de conversão dupla: ele deve receber um inteiro expressando minutos após a meia-noite e convertê-lo em um horário legível, e precisa convertê-lo no horário local. Ele realiza isso primeiro criando um <xref:System.DateTime> objeto que é definido como meia-noite UTC e, em seguida, usa o <xref:System.DateTime.AddMinutes%2A> método para adicionar os minutos que foram passados para o método. Isso retorna uma nova <xref:System.DateTime> expressar a hora original que foi passada para o método. Em <xref:System.DateTime.ToLocalTime%2A> seguida, o método o converte para a hora local.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
