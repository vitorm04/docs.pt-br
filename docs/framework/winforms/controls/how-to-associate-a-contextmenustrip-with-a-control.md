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
ms.openlocfilehash: 70617f73293c62cdf29ca47ee060e023b66cb454
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612793"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="bd040-102">Como: Associar um ContextMenuStrip a um controle</span><span class="sxs-lookup"><span data-stu-id="bd040-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="bd040-103">Depois de criar os seus controles e menus de atalho, use os procedimentos a seguir para exibir um menu de atalho fornecido quando o usuário clica no controle.</span><span class="sxs-lookup"><span data-stu-id="bd040-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="bd040-104">Esses procedimentos associar uma <xref:System.Windows.Forms.ContextMenuStrip> com um formulário do Windows e com um <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="bd040-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="bd040-105">Para associar um ContextMenuStrip um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="bd040-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1. <span data-ttu-id="bd040-106">Defina as <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="bd040-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="bd040-107">Para associar um ContextMenuStrip um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bd040-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1. <span data-ttu-id="bd040-108">Defina o controle <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para o nome do associado <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="bd040-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd040-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd040-109">Example</span></span>  
 <span data-ttu-id="bd040-110">O exemplo de código a seguir cria um formulário do Windows e um <xref:System.Windows.Forms.ToolStrip>e a associa outro <xref:System.Windows.Forms.ContextMenuStrip> controle com cada um deles.</span><span class="sxs-lookup"><span data-stu-id="bd040-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd040-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bd040-111">Compiling the Code</span></span>  
 <span data-ttu-id="bd040-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="bd040-112">This example requires:</span></span>  
  
- <span data-ttu-id="bd040-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="bd040-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bd040-114">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bd040-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bd040-115">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="bd040-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd040-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd040-116">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="bd040-117">Como: Adicionar itens de Menu a um ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="bd040-117">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="bd040-118">Controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="bd040-118">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
