---
title: 'Como: Colocar objetos em camadas nos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 818f36633575b248d92da475c462cc0f211fe969
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966532"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="d9e36-102">Como: Colocar objetos em camadas nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9e36-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="d9e36-103">Ao criar uma interface do usuário complexa ou trabalhar com um formulário MDI (interface de múltiplos documentos), geralmente se deseja dispor em camadas controles e formulários filho para criar interfaces do usuário (UI) mais complexas.</span><span class="sxs-lookup"><span data-stu-id="d9e36-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="d9e36-104">Para mover e acompanhar os controles e janelas no contexto de um grupo, manipule a ordem z.</span><span class="sxs-lookup"><span data-stu-id="d9e36-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="d9e36-105">A *ordem z* consiste na disposição em camadas visuais de controles em um formulário ao longo do eixo z do formulário (profundidade).</span><span class="sxs-lookup"><span data-stu-id="d9e36-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="d9e36-106">A janela na parte superior da ordem z se sobrepõe a todas as outras janelas.</span><span class="sxs-lookup"><span data-stu-id="d9e36-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="d9e36-107">Todas as outras janelas se sobrepõe a janela na parte inferior da ordem z.</span><span class="sxs-lookup"><span data-stu-id="d9e36-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="d9e36-108">Dispondo controles em camadas no design time</span><span class="sxs-lookup"><span data-stu-id="d9e36-108">To layer controls at design time</span></span>

1. <span data-ttu-id="d9e36-109">Selecione o controle que deseja dispor em camadas.</span><span class="sxs-lookup"><span data-stu-id="d9e36-109">Select a control that you want to layer.</span></span>

2. <span data-ttu-id="d9e36-110">No menu **Formato**, aponte para **Pedido** e depois clique em **Trazer para frente** ou **Enviar para trás**.</span><span class="sxs-lookup"><span data-stu-id="d9e36-110">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="d9e36-111">Dispondo controles em camadas de forma programática</span><span class="sxs-lookup"><span data-stu-id="d9e36-111">To layer controls programmatically</span></span>

- <span data-ttu-id="d9e36-112">Use os <xref:System.Windows.Forms.Control.BringToFront%2A> métodos <xref:System.Windows.Forms.Control.SendToBack%2A> e para manipular a ordem z dos controles.</span><span class="sxs-lookup"><span data-stu-id="d9e36-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

     <span data-ttu-id="d9e36-113">Por exemplo, se um <xref:System.Windows.Forms.TextBox> controle, `txtFirstName`, estiver abaixo de outro controle e você quiser tê-lo na parte superior, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d9e36-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
> <span data-ttu-id="d9e36-114">Windows Forms dá suporte a *Contenção de controle*.</span><span class="sxs-lookup"><span data-stu-id="d9e36-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="d9e36-115">A contenção de controle envolve colocar um número de controles dentro de um controle recipiente, como um <xref:System.Windows.Forms.RadioButton> número de controles <xref:System.Windows.Forms.GroupBox> dentro de um controle.</span><span class="sxs-lookup"><span data-stu-id="d9e36-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="d9e36-116">Em seguida, é possível dispor os controles em camadas no controle de contenção.</span><span class="sxs-lookup"><span data-stu-id="d9e36-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="d9e36-117">Mover a caixa de grupo move também os controles, já que estes estão contidos dentro dela.</span><span class="sxs-lookup"><span data-stu-id="d9e36-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9e36-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9e36-118">See also</span></span>

- [<span data-ttu-id="d9e36-119">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9e36-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="d9e36-120">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9e36-120">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d9e36-121">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="d9e36-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="d9e36-122">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9e36-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="d9e36-123">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="d9e36-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
