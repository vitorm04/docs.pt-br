---
title: Como alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213929e52f08fff19eb7641092789501c31648e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="424d8-102">Como alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="424d8-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="424d8-103">Quando você define o <xref:System.Windows.Forms.ToolStrip.Stretch%2A> propriedade de um <xref:System.Windows.Forms.ToolStrip> controle `true`, o controle preenche seu contêiner de ponta a ponta e pode ser redimensionada quando o contêiner é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="424d8-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="424d8-104">Nessa configuração, talvez seja útil para alongar um item no controle, como um <xref:System.Windows.Forms.ToolStripTextBox>para preencher o espaço disponível e redimensionados quando o controle é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="424d8-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="424d8-105">Esse alongamento será útil, por exemplo, se você desejar obter aparência e comportamento semelhantes para a barra de endereços do Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="424d8-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="424d8-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="424d8-106">Example</span></span>  
 <span data-ttu-id="424d8-107">O exemplo de código a seguir fornece uma classe derivada de <xref:System.Windows.Forms.ToolStripTextBox> chamado `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="424d8-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="424d8-108">Esta classe substitui o <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> método para calcular a largura disponível do pai <xref:System.Windows.Forms.ToolStrip> depois que a largura combinada de todos os outros itens foi subtraída de controle.</span><span class="sxs-lookup"><span data-stu-id="424d8-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="424d8-109">Este exemplo de código também fornece um <xref:System.Windows.Forms.Form> classe e um `Program` classe para demonstrar o comportamento de novo.</span><span class="sxs-lookup"><span data-stu-id="424d8-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="424d8-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="424d8-110">Compiling the Code</span></span>  
 <span data-ttu-id="424d8-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="424d8-111">This example requires:</span></span>  
  
-   <span data-ttu-id="424d8-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="424d8-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="424d8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="424d8-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="424d8-114">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="424d8-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="424d8-115">Como usar a propriedade Spring de forma interativa em um StatusStrip</span><span class="sxs-lookup"><span data-stu-id="424d8-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
