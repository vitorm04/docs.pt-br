---
title: 'Como: Associar um ContextMenuStrip a um controle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 5fe880a44afdbd79116541809972d1456aefb9c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323233"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="c4617-102">Como: Associar um ContextMenuStrip a um controle</span><span class="sxs-lookup"><span data-stu-id="c4617-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="c4617-103">Depois de criar os seus controles e menus de atalho, use os procedimentos a seguir para exibir um menu de atalho fornecido quando o usuário clica no controle.</span><span class="sxs-lookup"><span data-stu-id="c4617-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="c4617-104">Esses procedimentos associar uma <xref:System.Windows.Forms.ContextMenuStrip> com um formulário do Windows e com um <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="c4617-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="c4617-105">Para associar um ContextMenuStrip um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="c4617-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1. <span data-ttu-id="c4617-106">Defina as <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="c4617-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="c4617-107">Para associar um ContextMenuStrip um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c4617-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1. <span data-ttu-id="c4617-108">Defina o controle <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="c4617-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4617-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c4617-109">Example</span></span>  
 <span data-ttu-id="c4617-110">O exemplo de código a seguir cria um formulário do Windows e um <xref:System.Windows.Forms.ToolStrip>e a associa outro <xref:System.Windows.Forms.ContextMenuStrip> controle com cada um deles.</span><span class="sxs-lookup"><span data-stu-id="c4617-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4617-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c4617-111">Compiling the Code</span></span>  
 <span data-ttu-id="c4617-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c4617-112">This example requires:</span></span>  
  
-   <span data-ttu-id="c4617-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c4617-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c4617-114">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c4617-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c4617-115">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c4617-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4617-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4617-116">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="c4617-117">Como: Adicionar itens de Menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="c4617-117">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="c4617-118">Controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="c4617-118">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
