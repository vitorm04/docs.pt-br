---
title: Armazenando tinta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: 4089aa7942105c14eb628c75edb7f53ffacfaeb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053361"
---
# <a name="storing-ink"></a><span data-ttu-id="ee250-102">Armazenando tinta</span><span class="sxs-lookup"><span data-stu-id="ee250-102">Storing Ink</span></span>
<span data-ttu-id="ee250-103">O <xref:System.Windows.Ink.StrokeCollection.Save%2A> métodos oferecem suporte para armazenar a tinta em tinta serializada Format (ISF).</span><span class="sxs-lookup"><span data-stu-id="ee250-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="ee250-104">Construtores para o <xref:System.Windows.Ink.StrokeCollection> classe dão suporte para a leitura de dados de tinta.</span><span class="sxs-lookup"><span data-stu-id="ee250-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="ee250-105">Armazenamento de tinta e a recuperação</span><span class="sxs-lookup"><span data-stu-id="ee250-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="ee250-106">Esta seção discute como armazenar e recuperar tinta no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plataforma.</span><span class="sxs-lookup"><span data-stu-id="ee250-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="ee250-107">O exemplo a seguir implementa um manipulador de eventos de clique de botão que apresenta ao usuário uma caixa de diálogo Salvar arquivo e salva a tinta de um <xref:System.Windows.Controls.InkCanvas> em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ee250-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="ee250-108">O exemplo a seguir implementa um manipulador de eventos de clique de botão que apresenta ao usuário uma caixa de diálogo Abrir arquivo e lê a tinta do arquivo em um <xref:System.Windows.Controls.InkCanvas> elemento.</span><span class="sxs-lookup"><span data-stu-id="ee250-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="ee250-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee250-109">See also</span></span>

- <xref:System.Windows.Controls.InkCanvas>
- [<span data-ttu-id="ee250-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="ee250-110">Windows Presentation Foundation</span></span>](../index.md)
