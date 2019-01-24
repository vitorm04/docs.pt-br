---
title: 'Como: Controles de botão de opção do grupo Windows Forms para funcionarem como um conjunto'
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 2758ff2380431668b2c908dbddd5dbe2094ccd0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569330"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="77deb-102">Como: Controles de botão de opção do grupo Windows Forms para funcionarem como um conjunto</span><span class="sxs-lookup"><span data-stu-id="77deb-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="77deb-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controles são projetados para dar aos usuários uma opção entre dois ou mais configurações, dos quais apenas um pode ser atribuído a um procedimento ou objeto.</span><span class="sxs-lookup"><span data-stu-id="77deb-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="77deb-104">Por exemplo, um grupo de <xref:System.Windows.Forms.RadioButton> controles podem exibir das operadoras de pacote para um pedido, mas apenas uma das operadoras será usada.</span><span class="sxs-lookup"><span data-stu-id="77deb-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="77deb-105">Portanto, apenas um <xref:System.Windows.Forms.RadioButton> por vez pode ser selecionado, mesmo que ele faz parte de um grupo funcional.</span><span class="sxs-lookup"><span data-stu-id="77deb-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="77deb-106">Grupo de botões de opção ao desenhar dentro de um contêiner, como um <xref:System.Windows.Forms.Panel> controle, um <xref:System.Windows.Forms.GroupBox> controle ou formulário.</span><span class="sxs-lookup"><span data-stu-id="77deb-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="77deb-107">Todos os botões de opção que forem adicionados diretamente a um formulário se tornam um grupo.</span><span class="sxs-lookup"><span data-stu-id="77deb-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="77deb-108">Para adicionar grupos separados, você deve inseri-los em painéis ou caixas de grupo.</span><span class="sxs-lookup"><span data-stu-id="77deb-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="77deb-109">Para obter mais informações sobre painéis ou caixas de grupo, consulte [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) ou [Visão geral do controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="77deb-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="77deb-110">Para agrupar controles RadioButton como um conjunto para funcionar independentemente dos outros conjuntos</span><span class="sxs-lookup"><span data-stu-id="77deb-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="77deb-111">Arraste uma <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> controlar da **Windows Forms** guia o **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="77deb-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="77deb-112">Desenhar <xref:System.Windows.Forms.RadioButton> controles em de <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> controle.</span><span class="sxs-lookup"><span data-stu-id="77deb-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77deb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77deb-113">See also</span></span>
- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="77deb-114">Visão geral do controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="77deb-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="77deb-115">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="77deb-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [<span data-ttu-id="77deb-116">Visão geral do controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="77deb-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="77deb-117">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="77deb-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="77deb-118">Controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="77deb-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
