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
ms.openlocfilehash: ad824a1cef637edc99e6aaafc99d557167ea1f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="65ee9-102">Como pesquisar remotamente o status das impressoras</span><span class="sxs-lookup"><span data-stu-id="65ee9-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="65ee9-103">A qualquer momento em médias e grandes empresas, pode haver várias impressoras que não estão funcionando devido a atolamentos de papel ou falta de papel ou alguma outra situação problemática.</span><span class="sxs-lookup"><span data-stu-id="65ee9-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="65ee9-104">O conjunto avançado de propriedades da impressora exposto no [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] oferece um meio de executar uma pesquisa rápida dos estados das impressoras.</span><span class="sxs-lookup"><span data-stu-id="65ee9-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65ee9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65ee9-105">Example</span></span>  
 <span data-ttu-id="65ee9-106">As principais etapas para criar esse tipo de utilitário são as apresentadas a seguir.</span><span class="sxs-lookup"><span data-stu-id="65ee9-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1.  <span data-ttu-id="65ee9-107">Obter uma lista de todos os servidores de impressão.</span><span class="sxs-lookup"><span data-stu-id="65ee9-107">Obtain a list of all print servers.</span></span>  
  
2.  <span data-ttu-id="65ee9-108">Executar um loop pelos servidores para consultar suas filas de impressão.</span><span class="sxs-lookup"><span data-stu-id="65ee9-108">Loop through the servers to query their print queues.</span></span>  
  
3.  <span data-ttu-id="65ee9-109">Em cada passagem do loop do servidor, executar um loop em todas as filas do servidor e ler cada propriedade que pode indicar que a fila não está funcionando no momento.</span><span class="sxs-lookup"><span data-stu-id="65ee9-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="65ee9-110">O código a seguir é uma série de trechos de código.</span><span class="sxs-lookup"><span data-stu-id="65ee9-110">The code below is a series of snippets.</span></span> <span data-ttu-id="65ee9-111">Para simplificar, este exemplo presume que há uma lista delimitada por CRLF de servidores de impressão.</span><span class="sxs-lookup"><span data-stu-id="65ee9-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="65ee9-112">A variável `fileOfPrintServers` é um <xref:System.IO.StreamReader> objeto para este arquivo.</span><span class="sxs-lookup"><span data-stu-id="65ee9-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="65ee9-113">Como cada nome de servidor está em sua própria linha, qualquer chamada de <xref:System.IO.StreamReader.ReadLine%2A> obtém o nome do servidor next e move o <xref:System.IO.StreamReader>do cursor até o início da próxima linha.</span><span class="sxs-lookup"><span data-stu-id="65ee9-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="65ee9-114">Dentro do loop externo, o código cria um <xref:System.Printing.PrintServer> de objeto para o servidor de impressão mais recente e especifica que o aplicativo deve ter direitos administrativos no servidor.</span><span class="sxs-lookup"><span data-stu-id="65ee9-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65ee9-115">Se houver muitos servidores, você pode melhorar o desempenho usando o <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> construtores que inicializam somente as propriedades que você vai precisar.</span><span class="sxs-lookup"><span data-stu-id="65ee9-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="65ee9-116">O exemplo usa <xref:System.Printing.PrintServer.GetPrintQueues%2A> criar uma coleção de todos os do servidor da filas e começa a iterá-los.</span><span class="sxs-lookup"><span data-stu-id="65ee9-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="65ee9-117">Este loop interno contém uma estrutura de ramificação correspondente as duas maneiras de verificar o status da impressora:</span><span class="sxs-lookup"><span data-stu-id="65ee9-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
-   <span data-ttu-id="65ee9-118">Você pode ler os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade que é do tipo <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="65ee9-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
-   <span data-ttu-id="65ee9-119">Você pode ler cada propriedade relevante, como <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, e <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="65ee9-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="65ee9-120">Este exemplo demonstra os dois métodos, o usuário foi previamente solicitado sobre qual método usar e respondeu com "y" se quiser usar os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="65ee9-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="65ee9-121">Veja abaixo os detalhes dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="65ee9-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="65ee9-122">Por fim, os resultados são apresentados ao usuário.</span><span class="sxs-lookup"><span data-stu-id="65ee9-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="65ee9-123">Para verificar o status da impressora usando os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade, verifique cada flag relevante para ver se ela está definida.</span><span class="sxs-lookup"><span data-stu-id="65ee9-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="65ee9-124">O modo padrão para ver se um bit está definido em um conjunto de sinalizadores de bit é realizar uma operação lógica AND com o conjunto de sinalizadores como um operando e o próprio sinalizador como o outro.</span><span class="sxs-lookup"><span data-stu-id="65ee9-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="65ee9-125">Uma vez que o próprio sinalizador tem apenas um bit definido, o resultado do AND lógico é que, no máximo, esse mesmo bit é definido.</span><span class="sxs-lookup"><span data-stu-id="65ee9-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="65ee9-126">Para saber se ele é ou não, basta comparar o resultado do AND lógico com o sinalizador em si.</span><span class="sxs-lookup"><span data-stu-id="65ee9-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="65ee9-127">Para obter mais informações, consulte <xref:System.Printing.PrintQueueStatus>, o [& operador (referência de c#)](~/docs/csharp/language-reference/operators/and-operator.md), e <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="65ee9-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/and-operator.md), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="65ee9-128">Para cada atributo cujo bit é definido, o código adiciona um aviso ao relatório final que será apresentado ao usuário.</span><span class="sxs-lookup"><span data-stu-id="65ee9-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="65ee9-129">(O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)</span><span class="sxs-lookup"><span data-stu-id="65ee9-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="65ee9-130">Para verificar o status da impressora usando cada propriedade, você simplesmente lê cada propriedade e adiciona uma observação ao relatório final que será apresentado ao usuário se a propriedade for `true`.</span><span class="sxs-lookup"><span data-stu-id="65ee9-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="65ee9-131">(O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)</span><span class="sxs-lookup"><span data-stu-id="65ee9-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="65ee9-132">O método **ReportAvailabilityAtThisTime** foi criado no caso de você precisar determinar se a fila está disponível no momento atual do dia.</span><span class="sxs-lookup"><span data-stu-id="65ee9-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="65ee9-133">O método não fará nada se o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades forem iguais; porque o caso em que a impressora está disponível em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="65ee9-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="65ee9-134">Se eles forem diferentes, o método obtém a hora atual, que deve ser convertida no total de minutos após a meia noite, pois o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades são <xref:System.Int32>s representando minutos-após-meia-noite, não <xref:System.DateTime> objetos.</span><span class="sxs-lookup"><span data-stu-id="65ee9-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="65ee9-135">Por fim, o método verifica se o horário atual está entre os horários de início e "até".</span><span class="sxs-lookup"><span data-stu-id="65ee9-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="65ee9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65ee9-136">See Also</span></span>  
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
 [<span data-ttu-id="65ee9-137">& Operador (referência de c#)</span><span class="sxs-lookup"><span data-stu-id="65ee9-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)  
 [<span data-ttu-id="65ee9-138">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="65ee9-138">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="65ee9-139">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="65ee9-139">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
