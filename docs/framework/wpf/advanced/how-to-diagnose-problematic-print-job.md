---
title: 'Como: Diagnosticar um trabalho de impressão problemático'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
ms.openlocfilehash: 181248f69684860fd43648952ef4eb3cced1c0ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944630"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Como: Diagnosticar um trabalho de impressão problemático
Administradores de rede frequentemente recebem reclamações de usuários sobre trabalhos de impressão que não são impressos ou são impressos lentamente. O rico conjunto de propriedades do trabalho de impressão exposto nas APIs do Microsoft .NET Framework fornece um meio para executar um diagnóstico remoto rápido de trabalhos de impressão.  
  
## <a name="example"></a>Exemplo  
 As principais etapas para criar esse tipo de utilitário são as apresentadas a seguir.  
  
1. Identifique o trabalho de impressão sobre o qual o usuário está reclamando. Frequentemente, os usuários não conseguem fazer isso com precisão. Talvez eles não saibam os nomes dos servidores de impressão ou impressoras. Eles podem descrever o local da impressora em uma terminologia diferente da usada na definição de sua <xref:System.Printing.PrintQueue.Location%2A> propriedade. Portanto, é uma boa ideia gerar uma lista dos trabalhos enviados atualmente pelo usuário. Se houver mais de um, a comunicação entre o usuário e o administrador de sistema de impressão poderá ser usada para identificar o trabalho que está tendo problemas. As subetapas são as seguintes.  
  
    1. Obter uma lista de todos os servidores de impressão.  
  
    2. Executar um loop pelos servidores para consultar suas filas de impressão.  
  
    3. Em cada passagem do loop do servidor, percorra em loop todas as filas do servidor para consultar seus trabalhos  
  
    4. Em cada passo do loop da fila, percorra em loop sobre seus trabalhos e colete informações de identificação sobre aqueles que foram enviados pelo usuário que fez a reclamação.  
  
2. Quando o trabalho de impressão problemático for identificado, examine as propriedades relevantes para ver qual pode ser o problema. Por exemplo, o trabalho está em estado de erro ou a impressora que atende a fila ficou offline antes que o trabalho fosse impresso?  
  
 O código a seguir é uma série de exemplos de código. O primeiro exemplo de código contém o loop pelas filas de impressão. (Etapa 1c acima.) A variável `myPrintQueues` é o <xref:System.Printing.PrintQueueCollection> objeto para o servidor de impressão atual.  
  
 O exemplo de código começa atualizando o objeto de fila de <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>impressão atual com. Isso garante que as propriedades do objeto representem precisamente o estado da impressora física que ele representa. Em seguida, o aplicativo obtém a coleção de trabalhos de impressão atualmente na fila de <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>impressão usando.  
  
 Em seguida, o aplicativo executa um <xref:System.Printing.PrintSystemJobInfo> loop na coleção e <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> compara cada propriedade com o alias do usuário reclamativo. Se forem iguais, o aplicativo adiciona informações de identificação sobre o trabalho à cadeia de caracteres que será apresentada. (As variáveis `userName` e `jobList` são inicializadas anteriormente no aplicativo.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 O exemplo de código a seguir usa o aplicativo a partir da Etapa 2. (Veja acima.) O trabalho problemático foi identificado e o aplicativo solicita as informações que o identificarão. A partir dessas informações, <xref:System.Printing.PrintServer>ele <xref:System.Printing.PrintQueue>cria objetos <xref:System.Printing.PrintSystemJobInfo> , e.  
  
 Nesse ponto, o aplicativo contém uma estrutura de ramificação correspondente às duas maneiras de verificar o status do trabalho da impressora:  
  
- Você pode ler os sinalizadores da <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> propriedade que é do tipo. <xref:System.Printing.PrintJobStatus>  
  
- Você pode ler cada propriedade relevante, como <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> e <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Este exemplo demonstra os dois métodos, de modo que o usuário foi solicitado anteriormente a qual método usar e respondeu com "Y" se ele quisesse usar os sinalizadores da <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> propriedade. Veja abaixo os detalhes dos dois métodos. Por fim, o aplicativo usa um método chamado **ReportQueueAndJobAvailability** para relatar se o trabalho pode ser impresso a esta hora do dia. Esse método é abordado em [Descobrir se um trabalho de impressão pode ser impresso a esta hora do dia](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Para verificar o status do trabalho de impressão usando os <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> sinalizadores da propriedade, você verifica cada sinalizador relevante para ver se ele está definido. O modo padrão para ver se um bit está definido em um conjunto de sinalizadores de bit é realizar uma operação lógica AND com o conjunto de sinalizadores como um operando e o próprio sinalizador como o outro. Uma vez que o próprio sinalizador tem apenas um bit definido, o resultado do AND lógico é que, no máximo, esse mesmo bit é definido. Para saber se ele é ou não, basta comparar o resultado do AND lógico com o sinalizador em si. Para obter mais informações, <xref:System.Printing.PrintJobStatus>consulte o [operador de &C# (referência)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)e <xref:System.FlagsAttribute>.  
  
 Para cada atributo cujo bit estiver definido, o código relata isso para a tela do console e, às vezes, sugere uma maneira de responder. (O método **HandlePausedJob** que é chamado se a fila ou o trabalho estiver em pausa é abordado abaixo.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Para verificar o status do trabalho de impressão usando propriedades separadas, basta ler cada propriedade e, se a propriedade for `true`, relatar isso para a tela do console e, possivelmente, sugerir uma maneira de responder. (O método **HandlePausedJob** que é chamado se a fila ou o trabalho estiver em pausa é abordado abaixo.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 O método **HandlePausedJob** permite que o usuário do aplicativo retome remotamente trabalhos em pausa. Como pode haver um bom motivo para a fila de impressão ter sido colocada em pausa, o método começa solicitando que o usuário decida se deseja retomá-la. Se a resposta for "Y", o <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> método será chamado.  
  
 Em seguida, será solicitado que o decida se o trabalho propriamente dito deve ser retomado, caso ele tenha sido colocado em pausa independentemente da fila de impressão. (Compare <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> e <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Se a resposta for "Y", <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> será chamada; caso contrário <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> , será chamado.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [Operador de &C# (referência)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
