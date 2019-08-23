---
title: 'Como: Criar chaves de acesso com controles de rótulo do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950534"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="7b47e-102">Como: Criar chaves de acesso com controles de rótulo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b47e-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="7b47e-103">Windows Forms <xref:System.Windows.Forms.Label> controles podem ser usados para definir chaves de acesso para outros controles.</span><span class="sxs-lookup"><span data-stu-id="7b47e-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="7b47e-104">Ao definir uma tecla de acesso em um controle de rótulo, o usuário pode pressionar a tecla ALT mais o caractere designado para mover o foco para o controle seguinte na ordem de tabulação.</span><span class="sxs-lookup"><span data-stu-id="7b47e-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="7b47e-105">Como os rótulos não podem receber o foco, este é movido automaticamente para o próximo controle na ordem de tabulação.</span><span class="sxs-lookup"><span data-stu-id="7b47e-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="7b47e-106">Use essa técnica para atribuir teclas de acesso a caixas de texto, caixas de combinação, caixas de listagem e grades de dados.</span><span class="sxs-lookup"><span data-stu-id="7b47e-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="7b47e-107">Atribuir uma tecla de acesso a um controle com um rótulo</span><span class="sxs-lookup"><span data-stu-id="7b47e-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="7b47e-108">Desenhe o rótulo primeiro e, em seguida, desenhe o outro controle.</span><span class="sxs-lookup"><span data-stu-id="7b47e-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="7b47e-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="7b47e-109">-or-</span></span>  
  
     <span data-ttu-id="7b47e-110">Desenhe os controles em qualquer ordem e defina a <xref:System.Windows.Forms.Control.TabIndex%2A> Propriedade do rótulo para um menor que o outro controle.</span><span class="sxs-lookup"><span data-stu-id="7b47e-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="7b47e-111">Defina a propriedade do <xref:System.Windows.Forms.Label.UseMnemonic%2A> rótulo como `true`.</span><span class="sxs-lookup"><span data-stu-id="7b47e-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="7b47e-112">Use um e comercial (&) na Propriedade do <xref:System.Windows.Forms.Label.Text%2A> rótulo para atribuir a chave de acesso para o rótulo.</span><span class="sxs-lookup"><span data-stu-id="7b47e-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="7b47e-113">Para obter mais informações, consulte [Criando teclas de acesso para controles dos Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7b47e-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b47e-114">Pode ser útil exibir o E comercial em um controle de rótulo, em vez de usá-lo para criar teclas de acesso.</span><span class="sxs-lookup"><span data-stu-id="7b47e-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="7b47e-115">Isso poderá ocorrer se você associar um controle de rótulo a um campo em um conjunto de registros em que os dados incluem o E comercial.</span><span class="sxs-lookup"><span data-stu-id="7b47e-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="7b47e-116">Para exibir o e comercial em um controle rótulo, <xref:System.Windows.Forms.Label.UseMnemonic%2A> defina a `false`Propriedade como.</span><span class="sxs-lookup"><span data-stu-id="7b47e-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="7b47e-117">Se você quiser exibir e comercial e também tiver uma chave de acesso, defina <xref:System.Windows.Forms.Label.UseMnemonic%2A> a propriedade `true` como e indique a tecla de acesso com um e comercial (&) e o e comercial para exibir com dois e comercial.</span><span class="sxs-lookup"><span data-stu-id="7b47e-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7b47e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b47e-118">See also</span></span>

- [<span data-ttu-id="7b47e-119">Como: Dimensionar um controle de rótulo Windows Forms para ajustar seu conteúdo</span><span class="sxs-lookup"><span data-stu-id="7b47e-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="7b47e-120">Visão geral do controle Label</span><span class="sxs-lookup"><span data-stu-id="7b47e-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="7b47e-121">Controle de rótulo</span><span class="sxs-lookup"><span data-stu-id="7b47e-121">Label Control</span></span>](label-control-windows-forms.md)
