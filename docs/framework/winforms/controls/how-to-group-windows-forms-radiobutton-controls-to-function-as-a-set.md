---
title: Agrupar controles de botão de opção para funcionar como um conjunto
description: Saiba como agrupar Windows Forms controles RadioButton para funcionar independentemente de outros conjuntos.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325917"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="aaf1a-103">Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto</span><span class="sxs-lookup"><span data-stu-id="aaf1a-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="aaf1a-104"><xref:System.Windows.Forms.RadioButton>Os controles de Windows Forms são projetados para fornecer aos usuários uma opção entre duas ou mais configurações, das quais apenas uma pode ser atribuída a um procedimento ou objeto.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="aaf1a-105">Por exemplo, um grupo de <xref:System.Windows.Forms.RadioButton> controles pode exibir uma opção de operadoras de pacote para um pedido, mas apenas uma das operadoras será usada.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="aaf1a-106">Portanto, somente um de <xref:System.Windows.Forms.RadioButton> cada vez pode ser selecionado, mesmo que ele faça parte de um grupo funcional.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="aaf1a-107">Agrupe os botões de opção desenhando-os dentro de um contêiner, como um <xref:System.Windows.Forms.Panel> controle, um <xref:System.Windows.Forms.GroupBox> controle ou um formulário.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="aaf1a-108">Todos os botões de opção que forem adicionados diretamente a um formulário se tornam um grupo.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="aaf1a-109">Para adicionar grupos separados, você deve inseri-los em painéis ou caixas de grupo.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="aaf1a-110">Para obter mais informações sobre painéis ou caixas de grupo, consulte [Visão geral do controle Panel](panel-control-overview-windows-forms.md) ou [Visão geral do controle GroupBox](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="aaf1a-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="aaf1a-111">Para agrupar controles RadioButton como um conjunto para funcionar independentemente dos outros conjuntos</span><span class="sxs-lookup"><span data-stu-id="aaf1a-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="aaf1a-112">Arraste um <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> controle ou da guia **Windows Forms** na caixa de **ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="aaf1a-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="aaf1a-113">Desenhe <xref:System.Windows.Forms.RadioButton> controles no <xref:System.Windows.Forms.GroupBox> controle ou <xref:System.Windows.Forms.Panel> .</span><span class="sxs-lookup"><span data-stu-id="aaf1a-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf1a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="aaf1a-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="aaf1a-115">Visão geral do controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="aaf1a-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="aaf1a-116">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="aaf1a-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="aaf1a-117">Visão geral do controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="aaf1a-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="aaf1a-118">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="aaf1a-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="aaf1a-119">Controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="aaf1a-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
