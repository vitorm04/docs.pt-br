---
title: Como invocar uma caixa de diálogo Imprimir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 75a4160366766efbd19d6e8ae26fbec102e7f95b
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924494"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="c9663-102">Como invocar uma caixa de diálogo Imprimir</span><span class="sxs-lookup"><span data-stu-id="c9663-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="c9663-103">Para fornecer a capacidade de imprimir a partir do seu aplicativo, você pode simplesmente criar e abrir um <xref:System.Windows.Controls.PrintDialog> objeto.</span><span class="sxs-lookup"><span data-stu-id="c9663-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9663-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9663-104">Example</span></span>  
 <span data-ttu-id="c9663-105">O <xref:System.Windows.Controls.PrintDialog> controle fornece um único ponto de entrada para o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , configuração e envio de trabalho XPS.</span><span class="sxs-lookup"><span data-stu-id="c9663-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="c9663-106">O controle é fácil de usar e pode ser instanciado usando marcação ou código [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9663-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="c9663-107">O exemplo a seguir demonstra como instanciar e abrir o controle no código e como imprimir por meio dele.</span><span class="sxs-lookup"><span data-stu-id="c9663-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="c9663-108">Também mostra como assegurar que o diálogo dê ao usuário a opção de definir um intervalo específico de páginas.</span><span class="sxs-lookup"><span data-stu-id="c9663-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="c9663-109">O código do exemplo pressupõe que existe um arquivo FixedDocumentSequence.xps na raiz da unidade C:.</span><span class="sxs-lookup"><span data-stu-id="c9663-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="c9663-110">Uma vez que a caixa de diálogo estiver aberta, os usuários poderão selecionar as impressoras instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c9663-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="c9663-111">Eles também terão a opção de selecionar o [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) para criar um arquivo XPS (XML Paper Specification) em vez de imprimir.</span><span class="sxs-lookup"><span data-stu-id="c9663-111">They will also have the option of selecting the [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9663-112">O <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> controle do WPF, que é discutido neste tópico, não deve ser confundido com o <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> componente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c9663-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="c9663-113">Estritamente falando, você pode usar o <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> método sem nunca abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c9663-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="c9663-114">Assim, o controle pode ser utilizado como um componente de impressão não visto.</span><span class="sxs-lookup"><span data-stu-id="c9663-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="c9663-115">Mas, por motivos de desempenho, seria melhor usar o <xref:System.Printing.PrintQueue.AddJob%2A> método ou um dos muitos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> métodos do <xref:System.Windows.Xps.XpsDocumentWriter> .</span><span class="sxs-lookup"><span data-stu-id="c9663-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="c9663-116">Para saber mais sobre isso, veja [arquivos XPS de impressão programaticamente](how-to-programmatically-print-xps-files.md).</span><span class="sxs-lookup"><span data-stu-id="c9663-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9663-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="c9663-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="c9663-118">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="c9663-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="c9663-119">Visão geral da impressão</span><span class="sxs-lookup"><span data-stu-id="c9663-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="c9663-120">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="c9663-120">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
