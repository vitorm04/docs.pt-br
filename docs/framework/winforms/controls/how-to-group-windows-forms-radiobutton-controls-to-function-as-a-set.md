---
title: Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c92048374941f735568bcd758ed475eba78b81e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="7c6d6-102">Como agrupar controles RadioButton dos Windows Forms para funcionarem como um conjunto</span><span class="sxs-lookup"><span data-stu-id="7c6d6-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="7c6d6-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controles são projetados para dar aos usuários uma opção entre dois ou mais configurações, dos quais apenas um pode ser atribuído a um objeto ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="7c6d6-104">Por exemplo, um grupo de <xref:System.Windows.Forms.RadioButton> controles podem exibir uma escolha de operadoras de pacote para um pedido, mas apenas um dos carros será usado.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="7c6d6-105">Portanto, apenas um <xref:System.Windows.Forms.RadioButton> por vez pode ser selecionado, mesmo que ele faz parte de um grupo funcional.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="7c6d6-106">Grupo de botões de opção ao desenhar dentro de um contêiner, como um <xref:System.Windows.Forms.Panel> controle, um <xref:System.Windows.Forms.GroupBox> controle ou um formulário.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="7c6d6-107">Todos os botões de opção que forem adicionados diretamente a um formulário se tornam um grupo.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="7c6d6-108">Para adicionar grupos separados, você deve inseri-los em painéis ou caixas de grupo.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="7c6d6-109">Para obter mais informações sobre painéis ou caixas de grupo, consulte [Visão geral do controle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) ou [Visão geral do controle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7c6d6-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="7c6d6-110">Para agrupar controles RadioButton como um conjunto para funcionar independentemente dos outros conjuntos</span><span class="sxs-lookup"><span data-stu-id="7c6d6-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="7c6d6-111">Arraste um <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> controlar do **Windows Forms** guia o **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="7c6d6-112">Desenhar <xref:System.Windows.Forms.RadioButton> controles de <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> controle.</span><span class="sxs-lookup"><span data-stu-id="7c6d6-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c6d6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c6d6-113">See Also</span></span>  
 <xref:System.Windows.Forms.RadioButton>  
 [<span data-ttu-id="7c6d6-114">Visão geral do controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="7c6d6-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [<span data-ttu-id="7c6d6-115">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="7c6d6-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="7c6d6-116">Visão geral do controle GroupBox</span><span class="sxs-lookup"><span data-stu-id="7c6d6-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="7c6d6-117">Visão geral do controle CheckBox</span><span class="sxs-lookup"><span data-stu-id="7c6d6-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="7c6d6-118">Controle RadioButton</span><span class="sxs-lookup"><span data-stu-id="7c6d6-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
