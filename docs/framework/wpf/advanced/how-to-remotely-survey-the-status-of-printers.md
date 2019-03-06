---
title: 'Como: Pesquisar remotamente o status das impressoras'
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
ms.openlocfilehash: 6eba3c5edd9095a25c0a387a3b37f68e3799d1c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359699"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="89002-102">Como: Pesquisar remotamente o status das impressoras</span><span class="sxs-lookup"><span data-stu-id="89002-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="89002-103">A qualquer momento em médias e grandes empresas, pode haver várias impressoras que não estão funcionando devido a atolamentos de papel ou falta de papel ou alguma outra situação problemática.</span><span class="sxs-lookup"><span data-stu-id="89002-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="89002-104">O conjunto avançado de propriedades da impressora exposto no [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] do Microsoft .NET Framework fornecem um meio para executar uma pesquisa rápida dos Estados das impressoras.</span><span class="sxs-lookup"><span data-stu-id="89002-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89002-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89002-105">Example</span></span>  
 <span data-ttu-id="89002-106">As principais etapas para criar esse tipo de utilitário são as apresentadas a seguir.</span><span class="sxs-lookup"><span data-stu-id="89002-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1.  <span data-ttu-id="89002-107">Obter uma lista de todos os servidores de impressão.</span><span class="sxs-lookup"><span data-stu-id="89002-107">Obtain a list of all print servers.</span></span>  
  
2.  <span data-ttu-id="89002-108">Executar um loop pelos servidores para consultar suas filas de impressão.</span><span class="sxs-lookup"><span data-stu-id="89002-108">Loop through the servers to query their print queues.</span></span>  
  
3.  <span data-ttu-id="89002-109">Em cada passagem do loop do servidor, executar um loop em todas as filas do servidor e ler cada propriedade que pode indicar que a fila não está funcionando no momento.</span><span class="sxs-lookup"><span data-stu-id="89002-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="89002-110">O código a seguir é uma série de snippets de código.</span><span class="sxs-lookup"><span data-stu-id="89002-110">The code below is a series of snippets.</span></span> <span data-ttu-id="89002-111">Para simplificar, este exemplo presume que há uma lista delimitada por CRLF de servidores de impressão.</span><span class="sxs-lookup"><span data-stu-id="89002-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="89002-112">A variável `fileOfPrintServers` é um <xref:System.IO.StreamReader> objeto para este arquivo.</span><span class="sxs-lookup"><span data-stu-id="89002-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="89002-113">Como cada nome de servidor está em sua própria linha, qualquer chamada de <xref:System.IO.StreamReader.ReadLine%2A> obtém o nome do próximo servidor e move o <xref:System.IO.StreamReader>do cursor até o início da próxima linha.</span><span class="sxs-lookup"><span data-stu-id="89002-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="89002-114">Dentro do loop externo, o código cria um <xref:System.Printing.PrintServer> de objeto para o servidor de impressão mais recente e especifica que o aplicativo deve ter direitos administrativos no servidor.</span><span class="sxs-lookup"><span data-stu-id="89002-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89002-115">Se houver muitos servidores, você pode melhorar o desempenho usando o <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> construtores que inicializam somente as propriedades que serão necessárias.</span><span class="sxs-lookup"><span data-stu-id="89002-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="89002-116">O exemplo usa <xref:System.Printing.PrintServer.GetPrintQueues%2A> a fim de criar uma coleção de todas as do servidor das filas e começa a executar um loop nelas.</span><span class="sxs-lookup"><span data-stu-id="89002-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="89002-117">Este loop interno contém uma estrutura de ramificação correspondente as duas maneiras de verificar o status da impressora:</span><span class="sxs-lookup"><span data-stu-id="89002-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
-   <span data-ttu-id="89002-118">Você pode ler os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade que é do tipo <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="89002-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
-   <span data-ttu-id="89002-119">Você pode ler cada propriedade relevante, como <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, e <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="89002-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="89002-120">Este exemplo demonstra ambos métodos, o usuário foi previamente consultado sobre qual método usar e respondeu com "y" se quiser usar os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="89002-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="89002-121">Veja abaixo os detalhes dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="89002-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="89002-122">Por fim, os resultados são apresentados ao usuário.</span><span class="sxs-lookup"><span data-stu-id="89002-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="89002-123">Para verificar o status da impressora usando os sinalizadores do <xref:System.Printing.PrintQueue.QueueStatus%2A> propriedade, que você verifique cada sinalizador relevante para ver se ele está definido.</span><span class="sxs-lookup"><span data-stu-id="89002-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="89002-124">O modo padrão para ver se um bit está definido em um conjunto de sinalizadores de bit é realizar uma operação lógica AND com o conjunto de sinalizadores como um operando e o próprio sinalizador como o outro.</span><span class="sxs-lookup"><span data-stu-id="89002-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="89002-125">Uma vez que o próprio sinalizador tem apenas um bit definido, o resultado do AND lógico é que, no máximo, esse mesmo bit é definido.</span><span class="sxs-lookup"><span data-stu-id="89002-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="89002-126">Para saber se ele é ou não, basta comparar o resultado do AND lógico com o sinalizador em si.</span><span class="sxs-lookup"><span data-stu-id="89002-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="89002-127">Para obter mais informações, consulte <xref:System.Printing.PrintQueueStatus>, o [& operador (C# referência)](~/docs/csharp/language-reference/operators/and-operator.md), e <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="89002-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/and-operator.md), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="89002-128">Para cada atributo cujo bit é definido, o código adiciona um aviso ao relatório final que será apresentado ao usuário.</span><span class="sxs-lookup"><span data-stu-id="89002-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="89002-129">(O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)</span><span class="sxs-lookup"><span data-stu-id="89002-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="89002-130">Para verificar o status da impressora usando cada propriedade, você simplesmente lê cada propriedade e adiciona uma observação ao relatório final que será apresentado ao usuário se a propriedade for `true`.</span><span class="sxs-lookup"><span data-stu-id="89002-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="89002-131">(O método **ReportAvailabilityAtThisTime** chamado no final do código é discutido abaixo.)</span><span class="sxs-lookup"><span data-stu-id="89002-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="89002-132">O método **ReportAvailabilityAtThisTime** foi criado no caso de você precisar determinar se a fila está disponível no momento atual do dia.</span><span class="sxs-lookup"><span data-stu-id="89002-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="89002-133">O método não fará nada se o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriedades forem iguais, porque nesse caso, a impressora está disponível em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="89002-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="89002-134">Se eles forem diferentes, o método obtém a hora atual, que então precisará ser convertida no total de minutos após a meia noite, pois o <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> e <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> as propriedades são <xref:System.Int32>s que representa minutos-após a meia noite, não <xref:System.DateTime> objetos.</span><span class="sxs-lookup"><span data-stu-id="89002-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="89002-135">Por fim, o método verifica se o horário atual está entre os horários de início e "até".</span><span class="sxs-lookup"><span data-stu-id="89002-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="89002-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89002-136">See also</span></span>
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
- [<span data-ttu-id="89002-137">& Operador (C# referência)</span><span class="sxs-lookup"><span data-stu-id="89002-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)
- [<span data-ttu-id="89002-138">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="89002-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="89002-139">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="89002-139">Printing Overview</span></span>](printing-overview.md)
