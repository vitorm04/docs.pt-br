---
title: "Alterar seleção em um RichTextBox de forma programática"
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
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f645a5719425742ba02f8f9056ca788fd6fdb931
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="84bc0-102">Alterar seleção em um RichTextBox de forma programática</span><span class="sxs-lookup"><span data-stu-id="84bc0-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="84bc0-103">Este exemplo mostra como alterar programaticamente a seleção atual em um <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="84bc0-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="84bc0-104">Essa seleção é o mesmo que o usuário selecionou o conteúdo usando a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="84bc0-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84bc0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84bc0-105">Example</span></span>  
 <span data-ttu-id="84bc0-106">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve um conjunto nomeado <xref:System.Windows.Controls.RichTextBox> controle com conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="84bc0-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="84bc0-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84bc0-107">Example</span></span>  
 <span data-ttu-id="84bc0-108">O código a seguir seleciona algum texto arbitrário programaticamente quando o usuário clica dentro de <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="84bc0-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="84bc0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84bc0-109">See Also</span></span>  
 [<span data-ttu-id="84bc0-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="84bc0-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="84bc0-111">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="84bc0-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
