---
title: Agrupar controles de botão de opção para funcionar como um conjunto
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732944"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="04cbe-102">Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto</span><span class="sxs-lookup"><span data-stu-id="04cbe-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="04cbe-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controles são projetados para dar aos usuários uma opção entre duas ou mais configurações, das quais apenas uma pode ser atribuída a um procedimento ou objeto.</span><span class="sxs-lookup"><span data-stu-id="04cbe-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="04cbe-104">Por exemplo, um grupo de controles de <xref:System.Windows.Forms.RadioButton> pode exibir uma opção de operadoras de pacote para um pedido, mas apenas uma das operadoras será usada.</span><span class="sxs-lookup"><span data-stu-id="04cbe-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="04cbe-105">Portanto, somente um <xref:System.Windows.Forms.RadioButton> de cada vez pode ser selecionado, mesmo que ele faça parte de um grupo funcional.</span><span class="sxs-lookup"><span data-stu-id="04cbe-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="04cbe-106">Agrupe os botões de opção desenhando-os dentro de um contêiner, como um controle de <xref:System.Windows.Forms.Panel>, um controle de <xref:System.Windows.Forms.GroupBox> ou um formulário.</span><span class="sxs-lookup"><span data-stu-id="04cbe-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="04cbe-107">Todos os botões de opção que forem adicionados diretamente a um formulário se tornam um grupo.</span><span class="sxs-lookup"><span data-stu-id="04cbe-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="04cbe-108">Para adicionar grupos separados, você deve inseri-los em painéis ou caixas de grupo.</span><span class="sxs-lookup"><span data-stu-id="04cbe-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="04cbe-109">Para obter mais informações sobre painéis ou caixas de grupo, consulte [Visão geral do controle Panel](panel-control-overview-windows-forms.md) ou [Visão geral do controle GroupBox](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="04cbe-109">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="04cbe-110">Para agrupar controles RadioButton como um conjunto para funcionar independentemente dos outros conjuntos</span><span class="sxs-lookup"><span data-stu-id="04cbe-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="04cbe-111">Arraste um controle de <xref:System.Windows.Forms.GroupBox> ou de <xref:System.Windows.Forms.Panel> da guia **Windows Forms** na **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="04cbe-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="04cbe-112">Desenhe controles de <xref:System.Windows.Forms.RadioButton> no <xref:System.Windows.Forms.GroupBox> ou no controle de <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="04cbe-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04cbe-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="04cbe-113">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="04cbe-114">Visão geral do controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="04cbe-114">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="04cbe-115">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="04cbe-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="04cbe-116">Visão geral do controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="04cbe-116">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="04cbe-117">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="04cbe-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="04cbe-118">Controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="04cbe-118">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
