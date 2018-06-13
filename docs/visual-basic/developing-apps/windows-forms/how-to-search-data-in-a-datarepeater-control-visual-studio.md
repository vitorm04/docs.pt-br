---
title: Como pesquisar dados em um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 689990ee125c85c3151a4e965b619fde068d220e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588048"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="3d329-102">Como pesquisar dados em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="3d329-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="3d329-103">Quando você estiver usando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle que contém muitos registros, talvez você queira permitir que os usuários de pesquisa para um registro específico.</span><span class="sxs-lookup"><span data-stu-id="3d329-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="3d329-104">Em vez de pesquisar os dados no controle em si, você pode implementar uma pesquisa por meio de consulta subjacente <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="3d329-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="3d329-105">Se o item for encontrado, você pode usar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> propriedade para selecionar o item e rolá-lo no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="3d329-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="3d329-106">Para implementar a pesquisa</span><span class="sxs-lookup"><span data-stu-id="3d329-106">To implement search</span></span>  
  
1.  <span data-ttu-id="3d329-107">Arraste um <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="3d329-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="3d329-108">Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="3d329-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="3d329-109">Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="3d329-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="3d329-110">Na janela Propriedades, altere o **nome** propriedade **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="3d329-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="3d329-111">Alterar o **texto** propriedade **pesquisa**.</span><span class="sxs-lookup"><span data-stu-id="3d329-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="3d329-112">Clique duas vezes o <xref:System.Windows.Forms.Button> de controle para abrir o Editor de código e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3d329-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="3d329-113">Substituir *ProductsBindingSource* com o nome do <xref:System.Windows.Forms.BindingSource> para sua <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e substitua *ProductID* com o nome do campo que você deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="3d329-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d329-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d329-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="3d329-115">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="3d329-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="3d329-116">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="3d329-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="3d329-117">Como alterar a aparência de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="3d329-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
