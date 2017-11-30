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
# <a name="how-to-validate-and-merge-printtickets"></a>Como validar e mesclar PrintTickets
O [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [esquema de impressão](http://go.microsoft.com/fwlink/?LinkId=186397) inclui flexíveis e extensíveis <xref:System.Printing.PrintCapabilities> e <xref:System.Printing.PrintTicket> elementos. O primeiro lista os recursos de um dispositivo de impressão e o último especifica como o dispositivo deve usar esses recursos em relação a uma sequência específica de documentos, a um documento individual ou a uma página individual.  
  
 Uma sequência de tarefas comuns de um aplicativo que dá suporte à impressão seria o seguinte.  
  
1.  Determinar os recursos da impressora.  
  
2.  Configurar um <xref:System.Printing.PrintTicket> para usar esses recursos.  
  
3.  Validar o <xref:System.Printing.PrintTicket>.  
  
 Este artigo mostra como fazer isso.  
  
## <a name="example"></a>Exemplo  
 No exemplo simples abaixo, interessa-nos apenas se a impressora oferece impressão em frente e verso – a duplexação. As principais etapas são as seguintes.  
  
1.  Obter um <xref:System.Printing.PrintCapabilities> do objeto com o <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> método.  
  
2.  Teste a presença da capacidade desejada. No exemplo a seguir, podemos testar o <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> propriedade o <xref:System.Printing.PrintCapabilities> a presença de capacidade de impressão nos dois lados de uma folha de papel com "Ativar da página" do objeto ao longo do tempo lado da folha de. Como <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> é uma coleção, usamos o `Contains` método <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Essa etapa não é estritamente necessária. O <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> método usado abaixo verificará cada solicitação no <xref:System.Printing.PrintTicket> contra os recursos da impressora. Se o recurso solicitado não é suportado pela impressora, o driver de impressora substituirá uma solicitação alternativa no <xref:System.Printing.PrintTicket> retornado pelo método.  
  
3.  Se a impressora oferecer suporte a duplicação, o código de exemplo cria um <xref:System.Printing.PrintTicket> que pede a duplicação. Mas o aplicativo não especifica todas as possíveis configurações de impressora disponíveis no <xref:System.Printing.PrintTicket> elemento. Isso seria um desperdício de tempo do programa e do programador. Em vez disso, o código define apenas a solicitação de duplicação e, em seguida, mescla este <xref:System.Printing.PrintTicket> com um existente, totalmente configurado e validado, <xref:System.Printing.PrintTicket>, nesse caso, o padrão do usuário <xref:System.Printing.PrintTicket>.  
  
4.  Da mesma forma, o exemplo chama o <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> método para mesclar a nova mínima, <xref:System.Printing.PrintTicket> com o padrão do usuário <xref:System.Printing.PrintTicket>. Isso retorna um <xref:System.Printing.ValidationResult> que inclui o novo <xref:System.Printing.PrintTicket> como uma de suas propriedades.  
  
5.  O exemplo, em seguida, testa se o novo <xref:System.Printing.PrintTicket> solicita a duplicação. Se isso acontecer, em seguida, o exemplo o tornará o novo tíquete de impressão padrão do usuário. Se a etapa 2 acima tivesse sido deixada de fora e a impressora não oferecesse suporte à duplexação no lado longo da folha, o teste teria resultado em `false`. (Consulte a observação acima).  
  
6.  A última etapa significativa é confirmar a alteração para o <xref:System.Printing.PrintQueue.UserPrintTicket%2A> propriedade o <xref:System.Printing.PrintQueue> com o <xref:System.Printing.PrintQueue.Commit%2A> método.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Para que seja possível testar este exemplo rapidamente, o restante dele será apresentado logo abaixo. Crie um projeto e um namespace e, em seguida, cole os dois trechos de código deste artigo no bloco do namespace.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Esquema de Impressão](http://go.microsoft.com/fwlink/?LinkId=186397)
