---
title: 'Como: alterar o Layout de um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 52d74202c26d22027840e872712e6fbc1bcf7e00
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="6df45-102">Como alterar o layout de um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6df45-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="6df45-103">O <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle pode ser exibido em um horizontal (itens de rolagem horizontal) ou vertical (itens de rolagem vertical) orientação.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="6df45-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="6df45-104">Você pode alterar a orientação em tempo de design ou em tempo de execução alterando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="6df45-105">Se você alterar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>propriedade em tempo de execução, você talvez queira redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>e reposicionar os controles filho.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6df45-106">Se você reposicionar controles no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>em tempo de execução, você precisará chamar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>e <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>métodos no início e no final do bloco de código que reposiciona os controles.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="6df45-107">Para alterar o layout em tempo de design</span><span class="sxs-lookup"><span data-stu-id="6df45-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="6df45-108">No Windows Forms Designer, selecione o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="6df45-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6df45-109">Você deve selecionar a borda externa do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle clicando na área inferior do controle, não na parte superior <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>região.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="6df45-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="6df45-110">Na janela Propriedades, defina a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>propriedade para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="6df45-111">Para alterar o layout em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6df45-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="6df45-112">Adicione o seguinte código para um botão ou menu `Click` manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="6df45-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     <span data-ttu-id="6df45-113">[!code-cs[&#1; VbPowerPacksDataRepeaterLayout](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterLayout n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6df45-113">[!code-cs[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]</span></span>  
  
2.  <span data-ttu-id="6df45-114">Na maioria dos casos, você desejará adicionar código semelhante ao mostrado na seção de exemplo para redimensionar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>e reordenar os controles para se ajustar à nova orientação.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-114">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6df45-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6df45-115">Example</span></span>  
 <span data-ttu-id="6df45-116">O exemplo a seguir mostra como responder a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged>evento em um manipulador de eventos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged></span><span class="sxs-lookup"><span data-stu-id="6df45-116">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="6df45-117">Este exemplo requer que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle chamado `DataRepeater1` em um formulário e que sua <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>contêm dois <xref:System.Windows.Forms.TextBox>controles denominados `TextBox1` e `TextBox2`.</xref:System.Windows.Forms.TextBox> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="6df45-117">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 <span data-ttu-id="6df45-118">[!code-cs[N º&2; VbPowerPacksDataRepeaterLayout](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs) ] 
 [!code-vb [VbPowerPacksDataRepeaterLayout n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6df45-118">[!code-cs[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df45-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6df45-119">See Also</span></span>  
 <span data-ttu-id="6df45-120"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="6df45-120"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
 <span data-ttu-id="6df45-121"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-121"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A></span></span>   
 <span data-ttu-id="6df45-122"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-122"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A></span></span>   
 <span data-ttu-id="6df45-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A></span><span class="sxs-lookup"><span data-stu-id="6df45-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A></span></span>   
<span data-ttu-id="6df45-124"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6df45-124"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="6df45-125"> [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6df45-125"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="6df45-126"> [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="6df45-126"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)</span></span>
