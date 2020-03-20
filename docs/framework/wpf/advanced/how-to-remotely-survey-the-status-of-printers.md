---
title: Como pesquisar remotamente o status das impressoras
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187036"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Como pesquisar remotamente o status das impressoras
A qualquer momento em médias e grandes empresas, pode haver várias impressoras que não estão funcionando devido a atolamentos de papel ou falta de papel ou alguma outra situação problemática. O rico conjunto de propriedades de impressora expostas nas APIs do Microsoft .NET Framework fornece um meio para realizar um levantamento rápido dos estados das impressoras.  
  
## <a name="example"></a>Exemplo  
 As principais etapas para criar esse tipo de utilitário são as apresentadas a seguir.  
  
1. Obter uma lista de todos os servidores de impressão.  
  
2. Executar um loop pelos servidores para consultar suas filas de impressão.  
  
3. Em cada passagem do loop do servidor, executar um loop em todas as filas do servidor e ler cada propriedade que pode indicar que a fila não está funcionando no momento.  
  
 O código a seguir é uma série de snippets de código. Para simplificar, este exemplo presume que há uma lista delimitada por CRLF de servidores de impressão. A `fileOfPrintServers` variável <xref:System.IO.StreamReader> é um objeto para este arquivo. Uma vez que cada nome de servidor <xref:System.IO.StreamReader.ReadLine%2A> está em sua própria linha, qualquer chamada de recebe o nome do próximo servidor e move o <xref:System.IO.StreamReader>cursor para o início da próxima linha.  
  
 Dentro do loop externo, <xref:System.Printing.PrintServer> o código cria um objeto para o servidor de impressão mais recente e especifica que o aplicativo deve ter direitos administrativos para o servidor.  
  
> [!NOTE]
> Se houver muitos servidores, você pode melhorar o <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> desempenho usando os construtores que apenas inicializam as propriedades que você vai precisar.  
  
 O exemplo <xref:System.Printing.PrintServer.GetPrintQueues%2A> então usa para criar uma coleção de todas as filas do servidor e começa a fazer loop através delas. Este loop interno contém uma estrutura de ramificação correspondente as duas maneiras de verificar o status da impressora:  
  
- Você pode ler as <xref:System.Printing.PrintQueue.QueueStatus%2A> bandeiras da <xref:System.Printing.PrintQueueStatus>propriedade que é do tipo .  
  
- Você pode ler cada <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>propriedade <xref:System.Printing.PrintQueue.IsPaperJammed%2A>relevante, como , e .  
  
 Este exemplo demonstra ambos os métodos, de modo que o usuário foi previamente solicitado sobre qual método <xref:System.Printing.PrintQueue.QueueStatus%2A> usar e respondeu com "y" se quisesse usar as bandeiras da propriedade. Veja abaixo os detalhes dos dois métodos.  
  
 Por fim, os resultados são apresentados ao usuário.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Para verificar o status da <xref:System.Printing.PrintQueue.QueueStatus%2A> impressora usando as bandeiras da propriedade, verifique cada sinalizador relevante para ver se está definido. O modo padrão para ver se um bit está definido em um conjunto de sinalizadores de bit é realizar uma operação lógica AND com o conjunto de sinalizadores como um operando e o próprio sinalizador como o outro. Uma vez que o próprio sinalizador tem apenas um bit definido, o resultado do AND lógico é que, no máximo, esse mesmo bit é definido. Para saber se ele é ou não, basta comparar o resultado do AND lógico com o sinalizador em si. Para obter mais <xref:System.Printing.PrintQueueStatus>informações, consulte o Operador de <xref:System.FlagsAttribute>& [(C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)e .  
  
 Para cada atributo cujo bit é definido, o código adiciona um aviso ao relatório final que será apresentado ao usuário. (O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Para verificar o status da impressora usando cada propriedade, você simplesmente lê cada propriedade e adiciona uma observação ao relatório final que será apresentado ao usuário se a propriedade for `true`. (O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 O método **ReportAvailabilityAtThisTime** foi criado no caso de você precisar determinar se a fila está disponível no momento atual do dia.  
  
 O método não fará <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> nada se as propriedades e as propriedades forem iguais; porque nesse caso a impressora está disponível o tempo todo. Se forem diferentes, o método obtém o tempo atual que, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> em <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> seguida, tem que ser convertido em minutos totais depois da meia-noite porque as propriedades e as propriedades estão <xref:System.Int32>representando minutos após a meia-noite, não <xref:System.DateTime> objetos. Por fim, o método verifica se o horário atual está entre os horários de início e "até".  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [operador de& (Referência C#)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Documentos no WPF](documents-in-wpf.md)
- [Visão geral da impressão](printing-overview.md)
