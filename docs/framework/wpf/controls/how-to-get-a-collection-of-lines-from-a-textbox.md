---
title: 'Como: Obter uma coleção de linhas de um TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224631"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="2573e-102">Como: Obter uma coleção de linhas de um TextBox</span><span class="sxs-lookup"><span data-stu-id="2573e-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="2573e-103">Este exemplo mostra como obter um conjunto de linhas de texto de um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="2573e-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2573e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2573e-104">Example</span></span>  
 <span data-ttu-id="2573e-105">O exemplo a seguir mostra um método simple que usa um <xref:System.Windows.Controls.TextBox> como o argumento e retorna um <xref:System.Collections.Specialized.StringCollection> que contém as linhas de texto na **caixa de texto**.</span><span class="sxs-lookup"><span data-stu-id="2573e-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="2573e-106">O <xref:System.Windows.Controls.TextBox.LineCount%2A> propriedade é usada para determinar quantas linhas estão atualmente em de **TextBox**e o <xref:System.Windows.Controls.TextBox.GetLineText%2A> método é usado para extrair cada linha e adicioná-lo à coleção de linhas.</span><span class="sxs-lookup"><span data-stu-id="2573e-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="2573e-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2573e-107">See also</span></span>

- [<span data-ttu-id="2573e-108">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="2573e-108">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="2573e-109">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2573e-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
