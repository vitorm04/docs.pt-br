---
title: "Como: criar um formulário mestre-detalhes usando dois controles DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 4ed0b1fa0e7fac96cef3bde61efac66681f2507b
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="eb0fc-102">Como criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="eb0fc-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="eb0fc-103">Você pode exibir dados relacionados usando dois ou mais <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controles para criar um formulário mestre/detalhes.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="eb0fc-104">Por exemplo, você talvez queira exibir uma lista de clientes em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>e quando o usuário seleciona um cliente, exibir uma lista de pedidos do cliente em um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="eb0fc-105">Você pode exibir dados relacionados, arrastando os itens de detalhe que compartilham o mesmo nó da tabela principal do **fontes de dados** janela para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="eb0fc-106">Por exemplo, se você tiver uma fonte de dados que tenha uma tabela clientes e uma tabela relacionada Orders, você ver ambas as tabelas como nós superiores na exibição de árvore no **fontes de dados** janela.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="eb0fc-107">Expanda o nó Customers para que você possa ver as colunas.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="eb0fc-108">Observe que a última coluna da lista é um nó expansível que representa a tabela Orders.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="eb0fc-109">Este nó representa os pedidos relacionados para um cliente.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="eb0fc-110">Para exibir dados relacionados em dois controles DataRepeater</span><span class="sxs-lookup"><span data-stu-id="eb0fc-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="eb0fc-111">Arraste dois <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controles do **Visual Basic PowerPacks** guia de **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="eb0fc-112">Arraste as alças de dimensionamento e a posição para dimensionar os controles e posicioná-los lado a lado.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="eb0fc-113">Sobre o **dados** menu, clique em **Show Data Sources**.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb0fc-114">Se o **fontes de dados** janela estiver vazia, adicionar uma fonte de dados a ele.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="eb0fc-115">Para obter mais informações, consulte [adicionar novas fontes de dados](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="eb0fc-115">For more information, see [Add new data sources](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="eb0fc-116">No **fontes de dados** janela, selecione o nó de nível superior para a tabela principal.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="eb0fc-117">Altere o tipo subjacente da tabela mestra de detalhes clicando em **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="eb0fc-118">Arraste o nó tabela mestre para a região de modelo de item do primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="eb0fc-119">Expanda o nó de tabela mestre e selecione o nó de detalhes para a tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="eb0fc-120">Alterar o tipo subjacente da tabela de detalhes para obter detalhes, clicando em **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="eb0fc-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="eb0fc-121">Selecione este nó de tabela e arraste-o para a região de modelo de item da segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0fc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb0fc-122">See Also</span></span>  
 <span data-ttu-id="eb0fc-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="eb0fc-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="eb0fc-124"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="eb0fc-124"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="eb0fc-125"> [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="eb0fc-125"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="eb0fc-126"> [Como: Exibir relacionados a dados em um Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd) </span><span class="sxs-lookup"><span data-stu-id="eb0fc-126"> [How to: Display Related Data in a Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd) </span></span>  
<span data-ttu-id="eb0fc-127"> [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="eb0fc-127"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="eb0fc-128"> [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="eb0fc-128"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
