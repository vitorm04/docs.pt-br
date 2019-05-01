---
title: 'Como: Usar a classe FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: f33a297ae07d5509d2b4d9a98636086ac433a57f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051033"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="f4b04-102">Como: Usar a classe FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="f4b04-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="f4b04-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4b04-103">Example</span></span>  
 <span data-ttu-id="f4b04-104">Este exemplo mostra como criar uma instância de <xref:System.Windows.FontSizeConverter> e usá-lo para alterar o tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="f4b04-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="f4b04-105">O exemplo define um método personalizado chamado `changeSize` que converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em um separado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância do <xref:System.Double>e posteriormente em um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f4b04-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="f4b04-106">Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.FontSizeConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de uma <xref:System.Windows.Controls.ListBoxItem> a uma instância do <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="f4b04-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="f4b04-107">Esse valor, em seguida, é passado de volta como o valor da <xref:System.Windows.Controls.TextBlock.FontSize%2A> propriedade do <xref:System.Windows.Controls.TextBlock> elemento.</span><span class="sxs-lookup"><span data-stu-id="f4b04-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="f4b04-108">Este exemplo também define um segundo método personalizado que é chamado `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="f4b04-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="f4b04-109">Este método converte o <xref:System.Windows.Controls.ContentControl.Content%2A> do <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.String>e, em seguida, passa o valor para o <xref:System.Windows.Controls.TextBlock.FontFamily%2A> propriedade do <xref:System.Windows.Controls.TextBlock> elemento.</span><span class="sxs-lookup"><span data-stu-id="f4b04-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="f4b04-110">Este exemplo não é executado.</span><span class="sxs-lookup"><span data-stu-id="f4b04-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f4b04-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4b04-111">See also</span></span>

- <xref:System.Windows.FontSizeConverter>
