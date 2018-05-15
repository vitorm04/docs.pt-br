---
title: Como exibir controles não associados em um controle DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: 698e518a4ed10ed6cf14ccafc6833b1acf8752db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="f7f1e-102">Como exibir controles não associados em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="f7f1e-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="f7f1e-103">Além de controles associados, você talvez queira adicionar outros controles para um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, como um rótulo estático ou uma imagem que é repetida em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7f1e-104">Você também deve ter pelo menos um controle associado no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou nada será exibido em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="f7f1e-105">Para adicionar controles não associados a um DataRepeater</span><span class="sxs-lookup"><span data-stu-id="f7f1e-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="f7f1e-106">Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** a um controle de formulário ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="f7f1e-107">Arraste as alças de dimensionamento e a posição para o tamanho e posição do controle.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="f7f1e-108">Você também pode dimensionar e posicionar o controle alterando o **tamanho** e **posição** propriedades na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="f7f1e-109">Adicione pelo menos um controle associado a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="f7f1e-110">Para obter mais informações, consulte [como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f7f1e-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="f7f1e-111">Arraste um controle do **caixa de ferramentas** para a área de modelo de item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="f7f1e-112">Observe que o controle tem duas regiões retangulares.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="f7f1e-113">A região interna é o *modelo de item*; controles adicionados para o modelo serão repetidos em cada item a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="f7f1e-114">A região externa é o *visor*, onde os itens serão exibidos; controles que são adicionados a esta região não serão exibidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f7f1e-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f1e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7f1e-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="f7f1e-116">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="f7f1e-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="f7f1e-117">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="f7f1e-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="f7f1e-118">Como exibir dados associados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="f7f1e-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="f7f1e-119">Como: criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="f7f1e-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="f7f1e-120">Como alterar a aparência de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="f7f1e-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
