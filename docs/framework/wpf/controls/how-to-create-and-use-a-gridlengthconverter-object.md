---
title: Como criar e usar um objeto GridLengthConverter
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
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300916ec102682e1d886d43fbe70eeaf088d6454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="35fc6-102">Como criar e usar um objeto GridLengthConverter</span><span class="sxs-lookup"><span data-stu-id="35fc6-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="35fc6-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35fc6-103">Example</span></span>  
 <span data-ttu-id="35fc6-104">O exemplo a seguir mostra como criar e usar uma instância de <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="35fc6-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="35fc6-105">O exemplo define um método personalizado chamado `changeCol`, que passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.GridLengthConverter> que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.ListBoxItem> para uma instância de <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="35fc6-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="35fc6-106">O valor convertido, em seguida, é passado de volta como o valor da <xref:System.Windows.Controls.ColumnDefinition.Width%2A> propriedade o <xref:System.Windows.Controls.ColumnDefinition> elemento.</span><span class="sxs-lookup"><span data-stu-id="35fc6-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="35fc6-107">O exemplo também define um segundo método personalizado, chamado `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="35fc6-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="35fc6-108">Este método converte o <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> de um <xref:System.Windows.Controls.Slider> para um <xref:System.String> e, em seguida, passa que o valor de volta para o <xref:System.Windows.Controls.ColumnDefinition> como o <xref:System.Windows.Controls.ColumnDefinition.Width%2A> do elemento.</span><span class="sxs-lookup"><span data-stu-id="35fc6-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="35fc6-109">Observe que um separado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo define o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="35fc6-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="35fc6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35fc6-110">See Also</span></span>  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
