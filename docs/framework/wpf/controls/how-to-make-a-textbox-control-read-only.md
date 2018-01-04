---
title: Como tornar um controle TextBox somente leitura
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d3acf1e5065633f9f4c75f24780230525b01ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="87ff9-102">Como tornar um controle TextBox somente leitura</span><span class="sxs-lookup"><span data-stu-id="87ff9-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="87ff9-103">Este exemplo mostra como configurar um <xref:System.Windows.Controls.TextBox> controle por não permitir a entrada do usuário ou modificação.</span><span class="sxs-lookup"><span data-stu-id="87ff9-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ff9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87ff9-104">Example</span></span>  
 <span data-ttu-id="87ff9-105">Para impedir que usuários modifiquem o conteúdo de um <xref:System.Windows.Controls.TextBox> controlar, defina o <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo **true**.</span><span class="sxs-lookup"><span data-stu-id="87ff9-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="87ff9-106">O <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo afeta somente a entrada do usuário; ele não afeta o texto definido no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] descrição de um <xref:System.Windows.Controls.TextBox> controle ou definir programaticamente por meio de texto a <xref:System.Windows.Controls.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="87ff9-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="87ff9-107">O valor padrão de <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> é **false**.</span><span class="sxs-lookup"><span data-stu-id="87ff9-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ff9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87ff9-108">See Also</span></span>  
 [<span data-ttu-id="87ff9-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="87ff9-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="87ff9-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="87ff9-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
