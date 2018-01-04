---
title: Como pesquisar remotamente o status das impressoras
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
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eef67d6ade8fb2a17edadff35fc3155608f831cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Como pesquisar remotamente o status das impressoras
A qualquer momento em médias e grandes empresas, pode haver várias impressoras que não estão funcionando devido a atolamentos de papel ou falta de papel ou alguma outra situação problemática. O conjunto avançado de propriedades da impressora exposto no [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] oferece um meio de executar uma pesquisa rápida dos estados das impressoras.  
  
## <a name="example"></a>Exemplo  
 As principais etapas para criar esse tipo de utilitário são as apresentadas a seguir.  
  
1.  Obter uma lista de todos os servidores de impressão.  
  
2.  Executar um loop pelos servidores para consultar suas filas de impressão.  
  
3.  Em cada passagem do loop do servidor, executar um loop em todas as filas do servidor e ler cada propriedade que pode indicar que a fila não está funcionando no momento.  
  
 O código a seguir é uma série de trechos de código. Para simplificar, este exemplo presume que há uma lista delimitada por CRLF de servidores de impressão. A variável `fileOfPrintServers` é um <xref:System.IO.StreamReader> objeto para este arquivo. Como cada nome de servidor está em sua própria linha, qualquer chamada de <xref:System.IO.StreamReader.ReadLine%2A> obtém o nome do servidor next e move o <xref:System.IO.StreamReader>do cursor até o início da próxima linha.  
  
 Dentro do loop externo, o código cria um <xref:System.Printing.PrintServer> de objeto para o servidor de impressão mais recente e especifica que o aplicativo deve ter direitos administrativos no servidor.  
  
> [!NOTE]
>  Se houver muitos servidores, você pode melhorar o desempenho usando o <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> construtores que inicializam somente as propriedades que você vai precisar.  
  
 O exemplo usa <xref:System.Printing.PrintServer.GetPrintQueues%2A> criar uma coleção de todos os do servidor da filas e começa a iterá-los. Este loop interno contém uma estrutura de ramificação correspondente as duas maneiras de verificar o status da impressora:  
  
-   Você pode ler os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade que é do tipo <xref:System.Printing.PrintQueueStatus>.  
  
-   Você pode ler cada propriedade relevante, como <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, e <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Este exemplo demonstra os dois métodos, o usuário foi previamente solicitado sobre qual método usar e respondeu com "y" se quiser usar os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade. Veja abaixo os detalhes dos dois métodos.  
  
 Por fim, os resultados são apresentados ao usuário.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Para verificar o status da impressora usando os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade, verifique cada flag relevante para ver se ela está definida. O modo padrão para ver se um bit está definido em um conjunto de sinalizadores de bit é realizar uma operação lógica AND com o conjunto de sinalizadores como um operando e o próprio sinalizador como o outro. Uma vez que o próprio sinalizador tem apenas um bit definido, o resultado do AND lógico é que, no máximo, esse mesmo bit é definido. Para saber se ele é ou não, basta comparar o resultado do AND lógico com o sinalizador em si. Para obter mais informações, consulte <xref:System.Printing.PrintQueueStatus>, o [& operador (referência de c#)](~/docs/csharp/language-reference/operators/and-operator.md), e <xref:System.FlagsAttribute>.  
  
 Para cada atributo cujo bit é definido, o código adiciona um aviso ao relatório final que será apresentado ao usuário. (O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Para verificar o status da impressora usando cada propriedade, você simplesmente lê cada propriedade e adiciona uma observação ao relatório final que será apresentado ao usuário se a propriedade for `true`. (O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 O método **ReportAvailabilityAtThisTime** foi criado no caso de você precisar determinar se a fila está disponível no momento atual do dia.  
  
 O método não fará nada se o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades forem iguais; porque o caso em que a impressora está disponível em todos os momentos. Se eles forem diferentes, o método obtém a hora atual, que deve ser convertida no total de minutos após a meia noite, pois o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades são <xref:System.Int32>s representando minutos-após-meia-noite, não <xref:System.DateTime> objetos. Por fim, o método verifica se o horário atual está entre os horários de início e "até".  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [& Operador (referência de c#)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)
