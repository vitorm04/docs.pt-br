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
# <a name="how-to-validate-and-merge-printtickets"></a>Como: Validar e mesclar PrintTickets
O [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [esquema de impressão](https://go.microsoft.com/fwlink/?LinkId=186397) inclui os elementos flexível <xref:System.Printing.PrintCapabilities> e <xref:System.Printing.PrintTicket> extensível e. O primeiro lista os recursos de um dispositivo de impressão e o último especifica como o dispositivo deve usar esses recursos em relação a uma sequência específica de documentos, a um documento individual ou a uma página individual.  
  
 Uma sequência de tarefas comuns de um aplicativo que dá suporte à impressão seria o seguinte.  
  
1. Determinar os recursos da impressora.  
  
2. Configure um <xref:System.Printing.PrintTicket> para usar esses recursos.  
  
3. Valide o <xref:System.Printing.PrintTicket>.  
  
 Este artigo mostra como fazer isso.  
  
## <a name="example"></a>Exemplo  
 No exemplo simples abaixo, interessa-nos apenas se a impressora oferece impressão em frente e verso – a duplexação. As principais etapas são as seguintes.  
  
1. Obtenha um <xref:System.Printing.PrintCapabilities> objeto com o <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> método.  
  
2. Teste a presença da capacidade desejada. No exemplo a seguir, testamos a <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> propriedade <xref:System.Printing.PrintCapabilities> do objeto para a presença da capacidade de impressão em ambos os lados de uma folha de papel com o "folheio de página" ao longo do lado do mais longo da planilha. Como <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> é uma coleção, usamos o `Contains` método de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    > Essa etapa não é estritamente necessária. O <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> método usado abaixo verificará cada solicitação <xref:System.Printing.PrintTicket> no em relação aos recursos da impressora. Se a impressora não oferecer suporte à funcionalidade solicitada, o driver de impressora substituirá uma solicitação alternativa <xref:System.Printing.PrintTicket> no retornado pelo método.  
  
3. Se a impressora oferecer suporte a Duplexing, o código de <xref:System.Printing.PrintTicket> exemplo criará um que solicita Duplexing. Mas o aplicativo não especifica todas as configurações de impressora possíveis disponíveis no <xref:System.Printing.PrintTicket> elemento. Isso seria um desperdício de tempo do programa e do programador. Em vez disso, o código define apenas a solicitação de duplex e, em <xref:System.Printing.PrintTicket> seguida, mescla isso com um existente, totalmente <xref:System.Printing.PrintTicket>configurado e validado,, nesse caso, <xref:System.Printing.PrintTicket>o padrão do usuário.  
  
4. Da mesma forma, o exemplo <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> chama o método para mesclar o novo <xref:System.Printing.PrintTicket> , o mínimo, com <xref:System.Printing.PrintTicket>o padrão do usuário. Isso retorna um <xref:System.Printing.ValidationResult> que inclui o novo <xref:System.Printing.PrintTicket> como uma de suas propriedades.  
  
5. Em seguida, o exemplo testa se <xref:System.Printing.PrintTicket> as novas solicitações se esfrentem. Se isso acontecer, em seguida, o exemplo o tornará o novo tíquete de impressão padrão do usuário. Se a etapa 2 acima tivesse sido deixada de fora e a impressora não oferecesse suporte à duplexação no lado longo da folha, o teste teria resultado em `false`. (Consulte a observação acima).  
  
6. A última etapa significativa é confirmar a alteração para a <xref:System.Printing.PrintQueue.UserPrintTicket%2A> propriedade <xref:System.Printing.PrintQueue> do com o <xref:System.Printing.PrintQueue.Commit%2A> método.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Para que seja possível testar este exemplo rapidamente, o restante dele será apresentado logo abaixo. Crie um projeto e um namespace e, em seguida, cole os dois snippets de código deste artigo no bloco do namespace.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
- [Esquema de Impressão](https://go.microsoft.com/fwlink/?LinkId=186397)
