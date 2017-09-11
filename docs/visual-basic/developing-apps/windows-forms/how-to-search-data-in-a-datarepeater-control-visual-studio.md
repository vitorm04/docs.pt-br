---
title: 'Como: pesquisar dados em um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: 11
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
ms.openlocfilehash: a9e323222d64b2adcca905930df61ffc2970e7e8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="28756-102">Como pesquisar dados em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="28756-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="28756-103">Quando você estiver usando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle que contém muitos registros, talvez você queira permitir que os usuários procurar um registro específico.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="28756-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="28756-104">Em vez de pesquisar os dados no próprio controle, você pode implementar uma pesquisa por meio de consulta subjacente <xref:System.Windows.Forms.BindingSource>.</xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="28756-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="28756-105">Se o item for encontrado, você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>propriedade para selecionar o item e rolá-lo no modo de exibição.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A></span><span class="sxs-lookup"><span data-stu-id="28756-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="28756-106">Para implementar a pesquisa</span><span class="sxs-lookup"><span data-stu-id="28756-106">To implement search</span></span>  
  
1.  <span data-ttu-id="28756-107">Arraste um <xref:System.Windows.Forms.TextBox>de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="28756-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="28756-108">Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="28756-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="28756-109">Arraste um <xref:System.Windows.Forms.Button>de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="28756-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="28756-110">Na janela Propriedades, altere o **nome** propriedade **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="28756-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="28756-111">Alterar o **texto** propriedade **pesquisa**.</span><span class="sxs-lookup"><span data-stu-id="28756-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="28756-112">Clique duas vezes o <xref:System.Windows.Forms.Button>de controle para abrir o Editor de códigos e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.</xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="28756-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     <span data-ttu-id="28756-113">[!code-vb[&#1; VbPowerPacksDataRepeaterSearch](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterSearch n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="28756-113">[!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
 [!code-cs[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]</span></span>  
  
     <span data-ttu-id="28756-114">Substitua *ProductsBindingSource* com o nome do <xref:System.Windows.Forms.BindingSource>para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e substitua *ProductID* com o nome do campo que você deseja pesquisar.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="28756-114">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28756-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28756-115">See Also</span></span>  
 <span data-ttu-id="28756-116"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="28756-116"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="28756-117"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="28756-117"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="28756-118"> [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="28756-118"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="28756-119"> [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="28756-119"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)</span></span>
