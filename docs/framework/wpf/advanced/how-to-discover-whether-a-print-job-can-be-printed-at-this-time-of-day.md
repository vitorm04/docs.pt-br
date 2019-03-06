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
ms.openlocfilehash: 2e93fe23a6084fec4e2a251b0361c29a4207e621
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352731"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Como: Descobrir se um trabalho de impressão pode ser impresso a esta hora do dia
Filas de impressão não estão sempre disponíveis 24 horas por dia. Eles têm propriedades de tempo de início e término que podem ser definidas para torná-las indisponíveis em determinados momentos do dia. Esse recurso pode ser usado, por exemplo, para reservar uma impressora para uso exclusivo de um determinado departamento após as 17h. Esse departamento teria uma fila diferente na impressora do que a que outros departamentos usam. A fila para os outros departamentos seria definida como indisponível após as 17h, enquanto a fila para o departamento favorecido poderia ser definida para estar sempre disponível.  
  
 Além disso, os próprios trabalhos de impressão podem ser definidos para serem impressos apenas dentro de um período especificado.  
  
 O <xref:System.Printing.PrintQueue> e <xref:System.Printing.PrintSystemJobInfo> classes expostas no [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] do Microsoft .NET Framework fornecem um meio de verificar remotamente se um determinado trabalho de impressão pode imprimir em uma determinada fila no momento atual.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é um exemplo que pode diagnosticar problemas com um trabalho de impressão.  
  
 Há duas etapas principais para esse tipo de função, da seguinte maneira.  
  
1.  Leia as <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades do <xref:System.Printing.PrintQueue> para determinar se o horário atual está entre eles.  
  
2.  Leia as <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> e <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> propriedades do <xref:System.Printing.PrintSystemJobInfo> para determinar se o horário atual está entre eles.  
  
 Mas complicações surgem do fato de que essas propriedades não são <xref:System.DateTime> objetos. Em vez disso, eles são <xref:System.Int32> objetos que expressam a hora do dia, como o número de minutos decorridos desde a meia-noite. Além disso, não se trata de meia-noite no fuso horário atual, mas meia-noite no UTC (Tempo Universal Coordenado).  
  
 O primeiro exemplo de código apresenta o método estático **ReportQueueAndJobAvailability**, que é passado um <xref:System.Printing.PrintSystemJobInfo> e chama métodos auxiliares para determinar se o trabalho pode ser impresso no horário atual e, se não, quando pode ser impresso. Observe que um <xref:System.Printing.PrintQueue> não é passado para o método. Isso ocorre porque o <xref:System.Printing.PrintSystemJobInfo> inclui uma referência para a fila em sua <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> propriedade.  
  
 Os métodos subordinados incluem sobrecarregado **ReportAvailabilityAtThisTime** método que pode receber um <xref:System.Printing.PrintQueue> ou um <xref:System.Printing.PrintSystemJobInfo> como um parâmetro. Também há um **TimeConverter.ConvertToLocalHumanReadableTime**. Todos esses métodos são discutidos abaixo.  
  
 O método **ReportQueueAndJobAvailability** começa verificando se a fila ou o trabalho de impressão está indisponível no momento. Se um deles estiver indisponível, ele verificará se a fila está indisponível. Se ela não estiver disponível, o método relatará esse fato e a hora em que a fila estará disponível novamente. Em seguida, ele verifica o trabalho e, se ele estiver indisponível, relatará o próximo intervalo em que ela pode ser impressa. Por fim, o método relata o horário mais próximo em que o trabalho pode ser impresso. Ele é o segundo dos dois horários a seguir.  
  
-   A hora em que a fila de impressão ficará disponível.  
  
-   A hora em que o trabalho de impressão ficará disponível.  
  
 Ao relatar horários do dia, o <xref:System.DateTime.ToShortTimeString%2A> método também é chamado porque esse método suprime os anos, meses e dias da saída. Você não pode restringir a disponibilidade de uma fila de impressão ou de um trabalho de impressão para dias, meses ou anos específicos.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 As duas sobrecargas do **ReportAvailabilityAtThisTime** método são idênticos exceto pelo tipo passado a elas, portanto, somente o <xref:System.Printing.PrintQueue> versão é apresentada abaixo.  
  
> [!NOTE]
>  O fato de que os métodos são idênticos exceto pelo tipo levanta a questão de por que o exemplo não cria um método genérico **ReportAvailabilityAtThisTime\<T>**. O motivo é que tal método precisaria ser restrito a uma classe que tem o **StartTimeOfDay** e **UntilTimeOfDay** propriedades que o método chama, mas um método genérico só pode ser restrito a um única classe e a única classe comum a ambos <xref:System.Printing.PrintQueue> e <xref:System.Printing.PrintSystemJobInfo> na herança de árvore é <xref:System.Printing.PrintSystemObject> que não tem tais propriedades.  
  
 O **ReportAvailabilityAtThisTime** método (apresentado no código de exemplo abaixo) começa inicializando uma <xref:System.Boolean> variável de sentinela como `true`. Ele será redefinido para `false` se a fila não estiver disponível.  
  
 Em seguida, o método verifica se as horas de início e "até" são idênticas. Se forem, a fila sempre estará disponível, então o método retornará `true`.  
  
 Se a fila não estiver disponível o tempo todo, o método usa estático <xref:System.DateTime.UtcNow%2A> propriedade para obter a hora atual como um <xref:System.DateTime> objeto. (Não precisamos do horário local porque o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades estão no horário UTC.)  
  
 No entanto, essas duas propriedades não são <xref:System.DateTime> objetos. Eles são <xref:System.Int32>expressando o horário como o número de minutos após-meia-noite-UTC. Portanto, precisamos converter nosso <xref:System.DateTime> objeto minutos após meia-noite. Quando isso é feito, o método simplesmente verifica se "agora" está entre as horas de início da fila e "até", define a sentinela como falsa caso "agora" não esteja entre as duas horas e retorna a sentinela.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 O **TimeConverter** método (apresentado no código de exemplo abaixo) não usa nenhum método introduzido com o Microsoft .NET Framework, então a discussão é breve. O método tem uma tarefa de conversão dupla: ele deve receber um inteiro expressando minutos após a meia-noite e convertê-lo em um horário legível, e precisa convertê-lo no horário local. Isso é feito criando primeiro uma <xref:System.DateTime> objeto que é definido como meia-noite UTC e, em seguida, usa o <xref:System.DateTime.AddMinutes%2A> método para adicionar os minutos que foram passados para o método. Isso retorna um novo <xref:System.DateTime> expressando o horário original que foi passado para o método. O <xref:System.DateTime.ToLocalTime%2A> método, em seguida, converte isso para o horário local.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
