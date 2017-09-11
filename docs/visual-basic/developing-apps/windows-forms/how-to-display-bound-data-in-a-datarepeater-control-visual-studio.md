---
title: 'Como: exibir dados associados em um controle DataRepeater (Visual Studio) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 677c964ee9ebbad6ec712a29c8b9c8920aa7e7ec
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="3f4af-102">Como exibir dados associados em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="3f4af-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="3f4af-103">O uso mais comum de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle é exibir dados associados de um banco de dados ou outra fonte de dados.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="3f4af-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="3f4af-104">Além de controles associados, você talvez queira adicionar outros controles, como um rótulo estático ou uma imagem que é repetida em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="3f4af-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="3f4af-105">Para obter mais informações, consulte [como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3f4af-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="3f4af-106">Você também pode vincular a uma fonte de dados em tempo de execução, definindo o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriedade `True` e atribuindo a uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>propriedade.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A></span><span class="sxs-lookup"><span data-stu-id="3f4af-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="3f4af-107">Nesse caso, você precisará gerenciar toda a interação com a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3f4af-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="3f4af-108">Para obter mais informações, consulte [modo Virtual no controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3f4af-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="3f4af-109">Para criar um DataRepeater ligados a dados</span><span class="sxs-lookup"><span data-stu-id="3f4af-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="3f4af-110">Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>de controle do **Visual Basic PowerPacks** guia o **Toolbox** a um controle de formulário ou contêiner.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="3f4af-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="3f4af-111">Arraste as alças de dimensionamento e a posição para tamanho e posição do controle.</span><span class="sxs-lookup"><span data-stu-id="3f4af-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="3f4af-112">Observe que o controle tem duas regiões retangulares.</span><span class="sxs-lookup"><span data-stu-id="3f4af-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="3f4af-113">Região superior é o *modelo de item*; controles adicionados ao modelo serão repetidos em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="3f4af-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="3f4af-114">A região inferior é o *visor*, onde os itens serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="3f4af-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="3f4af-115">Você também pode redimensionar e posicionar o controle ou o modelo de item, alterando o **tamanho** e **posição** propriedades na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="3f4af-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="3f4af-116">Sobre o **dados** menu, clique em **Show Data Sources**.</span><span class="sxs-lookup"><span data-stu-id="3f4af-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3f4af-117">Se o **fontes de dados** janela estiver vazia, adicionar uma fonte de dados a ele.</span><span class="sxs-lookup"><span data-stu-id="3f4af-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="3f4af-118">Para obter mais informações, consulte [adicionar novas fontes de dados](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="3f4af-118">For more information, see [Add new data sources](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="3f4af-119">No **fontes de dados** janela, selecione o nó de nível superior para a tabela que contém os dados que você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="3f4af-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="3f4af-120">Altere o tipo subjacente da tabela para `Details` clicando `Details` na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="3f4af-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="3f4af-121">Selecione o nó de tabela e arraste-o para a região de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="3f4af-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="3f4af-122">Você pode especificar quais tipos de controles são exibidos para cada campo.</span><span class="sxs-lookup"><span data-stu-id="3f4af-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="3f4af-123">Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span><span class="sxs-lookup"><span data-stu-id="3f4af-123">For more information, see [Set the control to be created when dragging from the Data Sources window](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4af-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f4af-124">See Also</span></span>  
 <span data-ttu-id="3f4af-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="3f4af-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="3f4af-126"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3f4af-126"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="3f4af-127"> [Como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3f4af-127"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="3f4af-128"> [Como: criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span><span class="sxs-lookup"><span data-stu-id="3f4af-128"> [How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span></span>  
<span data-ttu-id="3f4af-129"> [Como: alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3f4af-129"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="3f4af-130"> [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="3f4af-130"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
