---
title: 'Como: Usar um objeto ThicknessConverter'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: ebfb8642a01f6d602f4e5ffa58fde6a8ee0b4e1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075945"
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="702c8-102">Como: Usar um objeto ThicknessConverter</span><span class="sxs-lookup"><span data-stu-id="702c8-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="702c8-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="702c8-103">Example</span></span>  
 <span data-ttu-id="702c8-104">Este exemplo mostra como criar uma instância de <xref:System.Windows.ThicknessConverter> e usá-lo para alterar a espessura de uma borda.</span><span class="sxs-lookup"><span data-stu-id="702c8-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="702c8-105">O exemplo define um método personalizado chamado `changeThickness`; esse método primeiro converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em um separado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância do <xref:System.Windows.Thickness>e posteriormente converte o conteúdo em um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="702c8-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="702c8-106">Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.ThicknessConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de uma <xref:System.Windows.Controls.ListBoxItem> a uma instância do <xref:System.Windows.Thickness>.</span><span class="sxs-lookup"><span data-stu-id="702c8-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="702c8-107">Esse valor, em seguida, é passado de volta como o valor da <xref:System.Windows.Controls.Border.BorderThickness%2A> propriedade do <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="702c8-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="702c8-108">Este exemplo não é executado.</span><span class="sxs-lookup"><span data-stu-id="702c8-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="702c8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="702c8-109">See also</span></span>

- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- <span data-ttu-id="702c8-110">[Como: Alterar a propriedade Margin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="702c8-110">[How to: Change the Margin Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))</span></span>
- <span data-ttu-id="702c8-111">[Como: Converter um ListBoxItem em um novo tipo de dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="702c8-111">[How to: Convert a ListBoxItem to a new Data Type](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))</span></span>
- [<span data-ttu-id="702c8-112">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="702c8-112">Panels Overview</span></span>](../controls/panels-overview.md)
