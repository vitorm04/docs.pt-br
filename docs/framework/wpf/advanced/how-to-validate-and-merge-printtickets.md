---
title: Como validar e mesclar PrintTickets
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
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2c2929f37895f0dee5529a5bf90f84146585032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="afcd2-102">Como validar e mesclar PrintTickets</span><span class="sxs-lookup"><span data-stu-id="afcd2-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="afcd2-103">O [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [esquema de impressão](http://go.microsoft.com/fwlink/?LinkId=186397) inclui flexíveis e extensíveis <xref:System.Printing.PrintCapabilities> e <xref:System.Printing.PrintTicket> elementos.</span><span class="sxs-lookup"><span data-stu-id="afcd2-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](http://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="afcd2-104">O primeiro lista os recursos de um dispositivo de impressão e o último especifica como o dispositivo deve usar esses recursos em relação a uma sequência específica de documentos, a um documento individual ou a uma página individual.</span><span class="sxs-lookup"><span data-stu-id="afcd2-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="afcd2-105">Uma sequência de tarefas comuns de um aplicativo que dá suporte à impressão seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="afcd2-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="afcd2-106">Determinar os recursos da impressora.</span><span class="sxs-lookup"><span data-stu-id="afcd2-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="afcd2-107">Configurar um <xref:System.Printing.PrintTicket> para usar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="afcd2-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="afcd2-108">Validar o <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="afcd2-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="afcd2-109">Este artigo mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="afcd2-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afcd2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afcd2-110">Example</span></span>  
 <span data-ttu-id="afcd2-111">No exemplo simples abaixo, interessa-nos apenas se a impressora oferece impressão em frente e verso – a duplexação.</span><span class="sxs-lookup"><span data-stu-id="afcd2-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="afcd2-112">As principais etapas são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="afcd2-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="afcd2-113">Obter um <xref:System.Printing.PrintCapabilities> do objeto com o <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> método.</span><span class="sxs-lookup"><span data-stu-id="afcd2-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="afcd2-114">Teste a presença da capacidade desejada.</span><span class="sxs-lookup"><span data-stu-id="afcd2-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="afcd2-115">No exemplo a seguir, podemos testar o <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> propriedade o <xref:System.Printing.PrintCapabilities> a presença de capacidade de impressão nos dois lados de uma folha de papel com "Ativar da página" do objeto ao longo do tempo lado da folha de.</span><span class="sxs-lookup"><span data-stu-id="afcd2-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="afcd2-116">Como <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> é uma coleção, usamos o `Contains` método <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="afcd2-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="afcd2-117">Essa etapa não é estritamente necessária.</span><span class="sxs-lookup"><span data-stu-id="afcd2-117">This step is not strictly necessary.</span></span> <span data-ttu-id="afcd2-118">O <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> método usado abaixo verificará cada solicitação no <xref:System.Printing.PrintTicket> contra os recursos da impressora.</span><span class="sxs-lookup"><span data-stu-id="afcd2-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="afcd2-119">Se o recurso solicitado não é suportado pela impressora, o driver de impressora substituirá uma solicitação alternativa no <xref:System.Printing.PrintTicket> retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="afcd2-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="afcd2-120">Se a impressora oferecer suporte a duplicação, o código de exemplo cria um <xref:System.Printing.PrintTicket> que pede a duplicação.</span><span class="sxs-lookup"><span data-stu-id="afcd2-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="afcd2-121">Mas o aplicativo não especifica todas as possíveis configurações de impressora disponíveis no <xref:System.Printing.PrintTicket> elemento.</span><span class="sxs-lookup"><span data-stu-id="afcd2-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="afcd2-122">Isso seria um desperdício de tempo do programa e do programador.</span><span class="sxs-lookup"><span data-stu-id="afcd2-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="afcd2-123">Em vez disso, o código define apenas a solicitação de duplicação e, em seguida, mescla este <xref:System.Printing.PrintTicket> com um existente, totalmente configurado e validado, <xref:System.Printing.PrintTicket>, nesse caso, o padrão do usuário <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="afcd2-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="afcd2-124">Da mesma forma, o exemplo chama o <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> método para mesclar a nova mínima, <xref:System.Printing.PrintTicket> com o padrão do usuário <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="afcd2-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="afcd2-125">Isso retorna um <xref:System.Printing.ValidationResult> que inclui o novo <xref:System.Printing.PrintTicket> como uma de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="afcd2-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="afcd2-126">O exemplo, em seguida, testa se o novo <xref:System.Printing.PrintTicket> solicita a duplicação.</span><span class="sxs-lookup"><span data-stu-id="afcd2-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="afcd2-127">Se isso acontecer, em seguida, o exemplo o tornará o novo tíquete de impressão padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="afcd2-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="afcd2-128">Se a etapa 2 acima tivesse sido deixada de fora e a impressora não oferecesse suporte à duplexação no lado longo da folha, o teste teria resultado em `false`.</span><span class="sxs-lookup"><span data-stu-id="afcd2-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="afcd2-129">(Consulte a observação acima).</span><span class="sxs-lookup"><span data-stu-id="afcd2-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="afcd2-130">A última etapa significativa é confirmar a alteração para o <xref:System.Printing.PrintQueue.UserPrintTicket%2A> propriedade o <xref:System.Printing.PrintQueue> com o <xref:System.Printing.PrintQueue.Commit%2A> método.</span><span class="sxs-lookup"><span data-stu-id="afcd2-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="afcd2-131">Para que seja possível testar este exemplo rapidamente, o restante dele será apresentado logo abaixo.</span><span class="sxs-lookup"><span data-stu-id="afcd2-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="afcd2-132">Crie um projeto e um namespace e, em seguida, cole os dois trechos de código deste artigo no bloco do namespace.</span><span class="sxs-lookup"><span data-stu-id="afcd2-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="afcd2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afcd2-133">See Also</span></span>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="afcd2-134">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="afcd2-134">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="afcd2-135">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="afcd2-135">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="afcd2-136">Esquema de Impressão</span><span class="sxs-lookup"><span data-stu-id="afcd2-136">Print Schema</span></span>](http://go.microsoft.com/fwlink/?LinkId=186397)
