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
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094534"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="015be-102">Como enumerar um subconjunto de filas de impressão</span><span class="sxs-lookup"><span data-stu-id="015be-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="015be-103">Uma situação comum enfrentada por profissionais da TI (tecnologia da informação) que gerenciam um conjunto de impressoras de toda a empresa é gerar uma lista de impressoras que tenham determinadas características.</span><span class="sxs-lookup"><span data-stu-id="015be-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="015be-104">Essa funcionalidade é fornecida pelo método <xref:System.Printing.PrintServer.GetPrintQueues%2A> de um objeto <xref:System.Printing.PrintServer> e a enumeração <xref:System.Printing.EnumeratedPrintQueueTypes>.</span><span class="sxs-lookup"><span data-stu-id="015be-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="015be-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="015be-105">Example</span></span>  
 <span data-ttu-id="015be-106">No exemplo a seguir, o código começa criando uma matriz de sinalizadores que especifica as características das filas de impressão que desejamos listar.</span><span class="sxs-lookup"><span data-stu-id="015be-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="015be-107">Neste exemplo, estamos buscando filas de impressão que estejam instaladas localmente no servidor de impressão e que sejam compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="015be-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="015be-108">A enumeração de <xref:System.Printing.EnumeratedPrintQueueTypes> fornece muitas outras possibilidades.</span><span class="sxs-lookup"><span data-stu-id="015be-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="015be-109">Em seguida, o código cria um objeto <xref:System.Printing.LocalPrintServer>, uma classe derivada de <xref:System.Printing.PrintServer>.</span><span class="sxs-lookup"><span data-stu-id="015be-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="015be-110">O servidor de impressão local é o computador no qual o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="015be-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="015be-111">A última etapa significativa é passar a matriz para o método <xref:System.Printing.PrintServer.GetPrintQueues%2A>.</span><span class="sxs-lookup"><span data-stu-id="015be-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="015be-112">Por fim, os resultados são apresentados ao usuário.</span><span class="sxs-lookup"><span data-stu-id="015be-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="015be-113">Você pode estender este exemplo fazendo com que o loop `foreach` que passa por cada fila de impressão faça um exame adicional.</span><span class="sxs-lookup"><span data-stu-id="015be-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="015be-114">Por exemplo, você poderia retirar as impressoras que não dão suporte à impressão em duas laterais fazendo com que o loop chame cada método de <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> da fila de impressão e teste o valor retornado para a presença de Duplexing.</span><span class="sxs-lookup"><span data-stu-id="015be-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015be-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="015be-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="015be-116">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="015be-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="015be-117">Visão geral da impressão</span><span class="sxs-lookup"><span data-stu-id="015be-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="015be-118">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="015be-118">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
