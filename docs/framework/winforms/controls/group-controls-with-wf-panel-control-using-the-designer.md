---
title: 'Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040382"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="a8e28-102">Como: Agrupar controles com o controle de painel do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="a8e28-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="a8e28-103">Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para agrupar outros controles.</span><span class="sxs-lookup"><span data-stu-id="a8e28-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="a8e28-104">Há três razões para agrupar controles.</span><span class="sxs-lookup"><span data-stu-id="a8e28-104">There are three reasons to group controls.</span></span> <span data-ttu-id="a8e28-105">Uma delas é o agrupamento visual de elementos de formulários relacionados para uma interface do usuário clara; a outra é o agrupamento programático dos botões de opção, por exemplo; a última é para mover os controles como uma unidade em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="a8e28-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="a8e28-106">Para criar um grupo de controles</span><span class="sxs-lookup"><span data-stu-id="a8e28-106">To create a group of controls</span></span>

1. <span data-ttu-id="a8e28-107">Arraste um <xref:System.Windows.Forms.Panel> controle da guia **Windows Forms** da caixa de ferramentas para um formulário.</span><span class="sxs-lookup"><span data-stu-id="a8e28-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="a8e28-108">Adicione outros controles ao painel desenhando cada um deles dentro do painel.</span><span class="sxs-lookup"><span data-stu-id="a8e28-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="a8e28-109">Se você tiver controles existentes que deseja incluir em um painel, poderá selecionar todos os controles, recortá-los para a área de transferência, selecionar <xref:System.Windows.Forms.Panel> o controle e, em seguida, colá-los no painel.</span><span class="sxs-lookup"><span data-stu-id="a8e28-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="a8e28-110">Você também pode arrastá-los para o painel.</span><span class="sxs-lookup"><span data-stu-id="a8e28-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="a8e28-111">Adicional Se você quiser adicionar uma borda a um painel, defina sua <xref:System.Windows.Forms.BorderStyle> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8e28-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="a8e28-112">Há três opções: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>e <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="a8e28-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8e28-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8e28-113">See also</span></span>

- [<span data-ttu-id="a8e28-114">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="a8e28-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="a8e28-115">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="a8e28-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="a8e28-116">Como: Definir o plano de fundo de um painel</span><span class="sxs-lookup"><span data-stu-id="a8e28-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
