---
title: 'Como: Alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 707fd2e470a9be1d61d2878eeff845b3cad270db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971919"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="c29df-102">Como: Alongar um ToolStripTextBox para preencher a largura restante de um ToolStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c29df-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="c29df-103">Quando você define o <xref:System.Windows.Forms.ToolStrip.Stretch%2A> propriedade de um <xref:System.Windows.Forms.ToolStrip> o controle para `true`, o controle preenche seu contêiner de ponta a ponta e é redimensionado quando o contêiner é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="c29df-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="c29df-104">Nessa configuração, talvez seja útil para alongar um item no controle, como um <xref:System.Windows.Forms.ToolStripTextBox>, para preencher o espaço disponível e redimensionar quando o controle é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="c29df-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="c29df-105">Esse alongamento será útil, por exemplo, se você desejar obter aparência e comportamento semelhantes para a barra de endereços do Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="c29df-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c29df-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c29df-106">Example</span></span>  
 <span data-ttu-id="c29df-107">O exemplo de código a seguir fornece uma classe derivada de <xref:System.Windows.Forms.ToolStripTextBox> chamado `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="c29df-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="c29df-108">Essa classe substitui o <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> método para calcular a largura disponível do pai <xref:System.Windows.Forms.ToolStrip> depois que a largura combinada de todos os outros itens foi subtraída de controle.</span><span class="sxs-lookup"><span data-stu-id="c29df-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="c29df-109">Este exemplo de código também fornece um <xref:System.Windows.Forms.Form> classe e um `Program` para demonstrar o novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="c29df-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c29df-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c29df-110">Compiling the Code</span></span>  
 <span data-ttu-id="c29df-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c29df-111">This example requires:</span></span>  
  
- <span data-ttu-id="c29df-112">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c29df-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29df-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c29df-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c29df-114">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c29df-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="c29df-115">Como: Usar a propriedade Spring de forma interativa em um StatusStrip</span><span class="sxs-lookup"><span data-stu-id="c29df-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
