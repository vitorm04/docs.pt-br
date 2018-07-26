---
title: 'Como: criar um formulário mestre / detalhes usando dois controles DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245513"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="d9404-102">Como criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="d9404-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="d9404-103">Você pode exibir dados relacionados usando dois ou mais <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controles para criar um formulário mestre/detalhes.</span><span class="sxs-lookup"><span data-stu-id="d9404-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="d9404-104">Por exemplo, você talvez queira exibir uma lista de clientes em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e quando o usuário seleciona um cliente, exibir uma lista de pedidos do cliente em um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="d9404-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="d9404-105">Você pode exibir dados relacionados, arrastando os itens de detalhe que compartilham o mesmo nó da tabela mestre do **fontes de dados** window para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="d9404-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="d9404-106">Por exemplo, se você tiver uma fonte de dados que tem uma tabela de clientes e uma tabela Pedidos relacionada, você ver ambas as tabelas como nós de nível superior na exibição de árvore na **fontes de dados** janela.</span><span class="sxs-lookup"><span data-stu-id="d9404-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="d9404-107">Expanda o nó de clientes para que você possa ver as colunas.</span><span class="sxs-lookup"><span data-stu-id="d9404-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="d9404-108">Observe que a última coluna na lista é um nó expansível que representa a tabela de pedidos.</span><span class="sxs-lookup"><span data-stu-id="d9404-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="d9404-109">Este nó representa os pedidos relacionados para um cliente.</span><span class="sxs-lookup"><span data-stu-id="d9404-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="d9404-110">Para exibir dados relacionados em dois controles DataRepeater</span><span class="sxs-lookup"><span data-stu-id="d9404-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="d9404-111">Arraste duas <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controles do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="d9404-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="d9404-112">Arraste as alças de dimensionamento e a posição para dimensionar os controles e posicioná-los lado a lado.</span><span class="sxs-lookup"><span data-stu-id="d9404-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="d9404-113">Sobre o **dados** menu, clique em **Show Data Sources**.</span><span class="sxs-lookup"><span data-stu-id="d9404-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9404-114">Se o **fontes de dados** janela estiver vazia, adicione uma fonte de dados a ele.</span><span class="sxs-lookup"><span data-stu-id="d9404-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="d9404-115">Para obter mais informações, consulte [Adicionar novas fontes de dados](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="d9404-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="d9404-116">No **fontes de dados** janela, selecione o nó de nível superior para a tabela mestre.</span><span class="sxs-lookup"><span data-stu-id="d9404-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="d9404-117">Alterar o tipo subjacente da tabela mestra de detalhes clicando **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="d9404-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="d9404-118">Arraste o nó de tabela mestre para a região de modelo de item do primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="d9404-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="d9404-119">Expanda o nó mestre de tabela e selecione o nó de detalhe para a tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="d9404-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="d9404-120">Alterar o tipo subjacente da tabela de detalhes para obter detalhes clicando **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="d9404-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="d9404-121">Selecione este nó de tabela e arraste-o para a região de modelo de item do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="d9404-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9404-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9404-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="d9404-123">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="d9404-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d9404-124">Como exibir dados associados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="d9404-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d9404-125">Como exibir dados relacionados em um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9404-125">How to: Display Related Data in a Windows Forms Application</span></span>](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [<span data-ttu-id="d9404-126">Como alterar a aparência de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="d9404-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d9404-127">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="d9404-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
