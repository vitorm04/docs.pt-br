---
title: Como alterar o layout de um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590836"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="a6a04-102">Como alterar o layout de um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a6a04-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="a6a04-103">O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle pode ser exibido em um (itens de rolagem vertical) do vertical ou horizontal (itens de rolagem horizontal) orientação.</span><span class="sxs-lookup"><span data-stu-id="a6a04-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="a6a04-104">Você pode alterar a orientação em tempo de design ou em tempo de execução alterando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a6a04-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="a6a04-105">Se você alterar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade em tempo de execução, você talvez queira redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> e reposicionar os controles filho.</span><span class="sxs-lookup"><span data-stu-id="a6a04-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6a04-106">Se você reposicionar controles no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> em tempo de execução, você precisará chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> métodos no início e no final do bloco de código que reposiciona os controles.</span><span class="sxs-lookup"><span data-stu-id="a6a04-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="a6a04-107">Para alterar o layout em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a6a04-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="a6a04-108">No Designer de Formulários do Windows, selecione o controle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="a6a04-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6a04-109">Você deve selecionar a borda externa do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle clicando na região inferior do controle, não na parte superior <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> região.</span><span class="sxs-lookup"><span data-stu-id="a6a04-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="a6a04-110">Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriedade como <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="a6a04-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="a6a04-111">Para alterar o layout em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a6a04-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="a6a04-112">Adicione o seguinte código para um menu ou botão `Click` manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="a6a04-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="a6a04-113">Na maioria dos casos, você desejará adicionar código semelhante ao mostrado na seção de exemplo para redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> e reorganizar os controles para se ajustar à nova orientação.</span><span class="sxs-lookup"><span data-stu-id="a6a04-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6a04-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6a04-114">Example</span></span>  
 <span data-ttu-id="a6a04-115">O exemplo a seguir mostra como responder a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> evento em um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a6a04-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="a6a04-116">Este exemplo requer que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle chamado `DataRepeater1` em um formulário e que seu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contêm dois <xref:System.Windows.Forms.TextBox> controles denominados `TextBox1` e `TextBox2`.</span><span class="sxs-lookup"><span data-stu-id="a6a04-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a6a04-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6a04-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [<span data-ttu-id="a6a04-118">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="a6a04-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="a6a04-119">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="a6a04-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="a6a04-120">Como alterar a aparência de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="a6a04-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
