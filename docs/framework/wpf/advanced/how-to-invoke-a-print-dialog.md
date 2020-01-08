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
ms.openlocfilehash: 6d7bc322079718d17a921ef34af79145b021e3a7
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636088"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="af670-102">Como invocar uma caixa de diálogo Imprimir</span><span class="sxs-lookup"><span data-stu-id="af670-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="af670-103">Para fornecer a capacidade de imprimir a partir do seu aplicativo, você pode simplesmente criar e abrir um objeto <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="af670-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af670-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af670-104">Example</span></span>  
 <span data-ttu-id="af670-105">O controle de <xref:System.Windows.Controls.PrintDialog> fornece um único ponto de entrada para envio de trabalho de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuração e XPS.</span><span class="sxs-lookup"><span data-stu-id="af670-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="af670-106">O controle é fácil de usar e pode ser instanciado usando marcação ou código [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af670-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="af670-107">O exemplo a seguir demonstra como instanciar e abrir o controle no código e como imprimir por meio dele.</span><span class="sxs-lookup"><span data-stu-id="af670-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="af670-108">Também mostra como assegurar que o diálogo dê ao usuário a opção de definir um intervalo específico de páginas.</span><span class="sxs-lookup"><span data-stu-id="af670-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="af670-109">O código do exemplo pressupõe que existe um arquivo FixedDocumentSequence.xps na raiz da unidade C:.</span><span class="sxs-lookup"><span data-stu-id="af670-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="af670-110">Uma vez que a caixa de diálogo estiver aberta, os usuários poderão selecionar as impressoras instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="af670-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="af670-111">Eles também terão a opção de selecionar o [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) para criar um arquivo XPS (XML Paper Specification) em vez de imprimir.</span><span class="sxs-lookup"><span data-stu-id="af670-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af670-112">O controle <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> do WPF, que é discutido neste tópico, não deve ser confundido com o componente <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="af670-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="af670-113">Estritamente falando, você pode usar o método <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> sem nunca abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="af670-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="af670-114">Assim, o controle pode ser utilizado como um componente de impressão não visto.</span><span class="sxs-lookup"><span data-stu-id="af670-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="af670-115">Mas, por motivos de desempenho, seria melhor usar o método <xref:System.Printing.PrintQueue.AddJob%2A> ou um dos muitos métodos <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> do <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="af670-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="af670-116">Para saber mais, consulte [Impressão Programada de Arquivos XPS](how-to-programmatically-print-xps-files.md).</span><span class="sxs-lookup"><span data-stu-id="af670-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af670-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="af670-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="af670-118">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="af670-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="af670-119">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="af670-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="af670-120">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="af670-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
