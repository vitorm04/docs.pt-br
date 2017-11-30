---
title: Como usar a classe FontSizeConverter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcf2d7348ca5b6b9d3b2edc44f92afbd46d32594
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="4c9ec-102">Como usar a classe FontSizeConverter</span><span class="sxs-lookup"><span data-stu-id="4c9ec-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="4c9ec-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c9ec-103">Example</span></span>  
 <span data-ttu-id="4c9ec-104">Este exemplo mostra como criar uma instância de <xref:System.Windows.FontSizeConverter> e usá-lo para alterar o tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="4c9ec-105">O exemplo define um método personalizado chamado `changeSize` que converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em uma separada [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância de <xref:System.Double>e posteriormente em um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="4c9ec-106">Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.FontSizeConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.ListBoxItem> para uma instância de <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="4c9ec-107">Esse valor é passado, em seguida, como o valor da <xref:System.Windows.Controls.TextBlock.FontSize%2A> propriedade o <xref:System.Windows.Controls.TextBlock> elemento.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="4c9ec-108">Este exemplo também define um segundo método personalizado que é chamado `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="4c9ec-109">Este método converte o <xref:System.Windows.Controls.ContentControl.Content%2A> do <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.String>e, em seguida, passa o valor para o <xref:System.Windows.Controls.TextBlock.FontFamily%2A> propriedade o <xref:System.Windows.Controls.TextBlock> elemento.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="4c9ec-110">Este exemplo não é executado.</span><span class="sxs-lookup"><span data-stu-id="4c9ec-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4c9ec-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c9ec-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
