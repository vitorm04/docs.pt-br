---
title: "Como definir o conteúdo de texto de um controle TextBox"
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
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8da173fb91745f83aac2b4461a917c1fff6e9cb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="7ed26-102">Como definir o conteúdo de texto de um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="7ed26-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="7ed26-103">Este exemplo mostra como usar o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade para definir o conteúdo de texto inicial de um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="7ed26-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="7ed26-104">**Observação** Embora o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] poderia usar a versão do exemplo o `<TextBox.Text>` marcas ao redor do texto de cada botão <xref:System.Windows.Controls.TextBox> conteúdo, não é necessário porque o <xref:System.Windows.Controls.TextBox> aplica-se a <xref:System.Windows.Markup.ContentPropertyAttribute> de atributo para o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7ed26-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="7ed26-105">Para obter mais informações, consulte [visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="7ed26-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ed26-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ed26-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="7ed26-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ed26-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="7ed26-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ed26-108">See Also</span></span>  
 [<span data-ttu-id="7ed26-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="7ed26-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="7ed26-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="7ed26-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
