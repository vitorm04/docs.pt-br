---
title: Como obter uma coleção de linhas a partir de um TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 64187527da3cfb97343e2036338822d479dd997a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="e696a-102">Como obter uma coleção de linhas a partir de um TextBox</span><span class="sxs-lookup"><span data-stu-id="e696a-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="e696a-103">Este exemplo mostra como obter um conjunto de linhas de texto de um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e696a-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e696a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e696a-104">Example</span></span>  
 <span data-ttu-id="e696a-105">O exemplo a seguir mostra um método simple que usa um <xref:System.Windows.Controls.TextBox> como o argumento e retorna um <xref:System.Collections.Specialized.StringCollection> contendo as linhas do texto no **caixa de texto**.</span><span class="sxs-lookup"><span data-stu-id="e696a-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="e696a-106">O <xref:System.Windows.Controls.TextBox.LineCount%2A> propriedade é usada para determinar quantas linhas estão atualmente no **TextBox**e o <xref:System.Windows.Controls.TextBox.GetLineText%2A> método é usado para extrair cada linha e adicioná-lo à coleção de linhas.</span><span class="sxs-lookup"><span data-stu-id="e696a-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="e696a-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e696a-107">See Also</span></span>  
 [<span data-ttu-id="e696a-108">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="e696a-108">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="e696a-109">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="e696a-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
