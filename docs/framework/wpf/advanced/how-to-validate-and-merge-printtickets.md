---
title: 'Como: Validar e mesclar PrintTickets'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918343"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="c89cc-102">Como: Validar e mesclar PrintTickets</span><span class="sxs-lookup"><span data-stu-id="c89cc-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="c89cc-103">O [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [esquema de impressão](https://go.microsoft.com/fwlink/?LinkId=186397) inclui os elementos flexível <xref:System.Printing.PrintCapabilities> e <xref:System.Printing.PrintTicket> extensível e.</span><span class="sxs-lookup"><span data-stu-id="c89cc-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="c89cc-104">O primeiro lista os recursos de um dispositivo de impressão e o último especifica como o dispositivo deve usar esses recursos em relação a uma sequência específica de documentos, a um documento individual ou a uma página individual.</span><span class="sxs-lookup"><span data-stu-id="c89cc-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="c89cc-105">Uma sequência de tarefas comuns de um aplicativo que dá suporte à impressão seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="c89cc-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="c89cc-106">Determinar os recursos da impressora.</span><span class="sxs-lookup"><span data-stu-id="c89cc-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="c89cc-107">Configure um <xref:System.Printing.PrintTicket> para usar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="c89cc-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="c89cc-108">Valide o <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="c89cc-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="c89cc-109">Este artigo mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="c89cc-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c89cc-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c89cc-110">Example</span></span>  
 <span data-ttu-id="c89cc-111">No exemplo simples abaixo, interessa-nos apenas se a impressora oferece impressão em frente e verso – a duplexação.</span><span class="sxs-lookup"><span data-stu-id="c89cc-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="c89cc-112">As principais etapas são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="c89cc-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="c89cc-113">Obtenha um <xref:System.Printing.PrintCapabilities> objeto com o <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c89cc-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="c89cc-114">Teste a presença da capacidade desejada.</span><span class="sxs-lookup"><span data-stu-id="c89cc-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="c89cc-115">No exemplo a seguir, testamos a <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> propriedade <xref:System.Printing.PrintCapabilities> do objeto para a presença da capacidade de impressão em ambos os lados de uma folha de papel com o "folheio de página" ao longo do lado do mais longo da planilha.</span><span class="sxs-lookup"><span data-stu-id="c89cc-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="c89cc-116">Como <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> é uma coleção, usamos o `Contains` método de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="c89cc-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c89cc-117">Essa etapa não é estritamente necessária.</span><span class="sxs-lookup"><span data-stu-id="c89cc-117">This step is not strictly necessary.</span></span> <span data-ttu-id="c89cc-118">O <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> método usado abaixo verificará cada solicitação <xref:System.Printing.PrintTicket> no em relação aos recursos da impressora.</span><span class="sxs-lookup"><span data-stu-id="c89cc-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="c89cc-119">Se a impressora não oferecer suporte à funcionalidade solicitada, o driver de impressora substituirá uma solicitação alternativa <xref:System.Printing.PrintTicket> no retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="c89cc-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="c89cc-120">Se a impressora oferecer suporte a Duplexing, o código de <xref:System.Printing.PrintTicket> exemplo criará um que solicita Duplexing.</span><span class="sxs-lookup"><span data-stu-id="c89cc-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="c89cc-121">Mas o aplicativo não especifica todas as configurações de impressora possíveis disponíveis no <xref:System.Printing.PrintTicket> elemento.</span><span class="sxs-lookup"><span data-stu-id="c89cc-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="c89cc-122">Isso seria um desperdício de tempo do programa e do programador.</span><span class="sxs-lookup"><span data-stu-id="c89cc-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="c89cc-123">Em vez disso, o código define apenas a solicitação de duplex e, em <xref:System.Printing.PrintTicket> seguida, mescla isso com um existente, totalmente <xref:System.Printing.PrintTicket>configurado e validado,, nesse caso, <xref:System.Printing.PrintTicket>o padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="c89cc-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="c89cc-124">Da mesma forma, o exemplo <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> chama o método para mesclar o novo <xref:System.Printing.PrintTicket> , o mínimo, com <xref:System.Printing.PrintTicket>o padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="c89cc-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="c89cc-125">Isso retorna um <xref:System.Printing.ValidationResult> que inclui o novo <xref:System.Printing.PrintTicket> como uma de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="c89cc-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="c89cc-126">Em seguida, o exemplo testa se <xref:System.Printing.PrintTicket> as novas solicitações se esfrentem.</span><span class="sxs-lookup"><span data-stu-id="c89cc-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="c89cc-127">Se isso acontecer, em seguida, o exemplo o tornará o novo tíquete de impressão padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="c89cc-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="c89cc-128">Se a etapa 2 acima tivesse sido deixada de fora e a impressora não oferecesse suporte à duplexação no lado longo da folha, o teste teria resultado em `false`.</span><span class="sxs-lookup"><span data-stu-id="c89cc-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="c89cc-129">(Consulte a observação acima).</span><span class="sxs-lookup"><span data-stu-id="c89cc-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="c89cc-130">A última etapa significativa é confirmar a alteração para a <xref:System.Printing.PrintQueue.UserPrintTicket%2A> propriedade <xref:System.Printing.PrintQueue> do com o <xref:System.Printing.PrintQueue.Commit%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c89cc-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="c89cc-131">Para que seja possível testar este exemplo rapidamente, o restante dele será apresentado logo abaixo.</span><span class="sxs-lookup"><span data-stu-id="c89cc-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="c89cc-132">Crie um projeto e um namespace e, em seguida, cole os dois snippets de código deste artigo no bloco do namespace.</span><span class="sxs-lookup"><span data-stu-id="c89cc-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="c89cc-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c89cc-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="c89cc-134">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="c89cc-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="c89cc-135">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="c89cc-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="c89cc-136">Esquema de Impressão</span><span class="sxs-lookup"><span data-stu-id="c89cc-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
