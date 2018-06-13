---
title: Como enumerar um subconjunto de filas de impressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: 3e616b3b61b4b1b561d5bdb7e51525f391901a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543583"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="c9bb5-102">Como enumerar um subconjunto de filas de impressão</span><span class="sxs-lookup"><span data-stu-id="c9bb5-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="c9bb5-103">Uma situação comum enfrentada por profissionais da TI (tecnologia da informação) que gerenciam um conjunto de impressoras de toda a empresa é gerar uma lista de impressoras que tenham determinadas características.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="c9bb5-104">Essa funcionalidade é fornecida pelo <xref:System.Printing.PrintServer.GetPrintQueues%2A> método de um <xref:System.Printing.PrintServer> objeto e o <xref:System.Printing.EnumeratedPrintQueueTypes> enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9bb5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9bb5-105">Example</span></span>  
 <span data-ttu-id="c9bb5-106">No exemplo a seguir, o código começa criando uma matriz de sinalizadores que especifica as características das filas de impressão que desejamos listar.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="c9bb5-107">Neste exemplo, estamos buscando filas de impressão que estejam instaladas localmente no servidor de impressão e que sejam compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="c9bb5-108">O <xref:System.Printing.EnumeratedPrintQueueTypes> enumeração fornece muitas outras possibilidades.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="c9bb5-109">O código, em seguida, cria um <xref:System.Printing.LocalPrintServer> do objeto, uma classe derivada de <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="c9bb5-110">O servidor de impressão local é o computador no qual o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="c9bb5-111">O último passo significativo é passar a matriz de <xref:System.Printing.PrintServer.GetPrintQueues%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="c9bb5-112">Por fim, os resultados são apresentados ao usuário.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="c9bb5-113">Você pode estender este exemplo fazendo com que o loop `foreach` que passa por cada fila de impressão faça um exame adicional.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="c9bb5-114">Por exemplo, você pode retirar as impressoras que dão suporte a impressão de dois lados fazendo com que a chamada de loop cada fila de impressão <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> método e teste o valor retornado para a presença de duplicação.</span><span class="sxs-lookup"><span data-stu-id="c9bb5-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9bb5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9bb5-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="c9bb5-116">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="c9bb5-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="c9bb5-117">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="c9bb5-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="c9bb5-118">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="c9bb5-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
