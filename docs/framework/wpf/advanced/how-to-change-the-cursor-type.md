---
title: Como alterar o tipo de cursor
description: Alterar o cursor do ponteiro do mouse para um elemento e para um aplicativo em Windows Presentation Foundation. Este exemplo consiste em XAML e um arquivo code-behind.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165966"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="2acaa-104">Como alterar o tipo de cursor</span><span class="sxs-lookup"><span data-stu-id="2acaa-104">How to: Change the Cursor Type</span></span>
<span data-ttu-id="2acaa-105">Este exemplo mostra como alterar o <xref:System.Windows.Input.Cursor> do ponteiro do mouse para um elemento específico e para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2acaa-105">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="2acaa-106">Esse exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="2acaa-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2acaa-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2acaa-107">Example</span></span>  
 <span data-ttu-id="2acaa-108">A interface do usuário é criada, que consiste em um <xref:System.Windows.Controls.ComboBox> para selecionar o desejado <xref:System.Windows.Input.Cursor> , um par de <xref:System.Windows.Controls.RadioButton> objetos para determinar se a alteração do cursor se aplica a apenas um único elemento ou se aplica a todo o aplicativo, e um <xref:System.Windows.Controls.Border> que é o elemento ao qual o novo cursor é aplicado.</span><span class="sxs-lookup"><span data-stu-id="2acaa-108">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="2acaa-109">O code-behind a seguir cria um <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> manipulador de eventos que é chamado quando o tipo de cursor é alterado no <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="2acaa-109">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="2acaa-110">Uma instrução switch filtra o nome do cursor e define a <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade no <xref:System.Windows.Controls.Border> que é chamado de *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="2acaa-110">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="2acaa-111">Se a alteração do cursor estiver definida como "aplicativo inteiro", a <xref:System.Windows.Input.Mouse.OverrideCursor%2A> propriedade será definida como a <xref:System.Windows.FrameworkElement.Cursor%2A> Propriedade do <xref:System.Windows.Controls.Border> controle.</span><span class="sxs-lookup"><span data-stu-id="2acaa-111">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="2acaa-112">Isso força o cursor a mudar para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="2acaa-112">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="2acaa-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2acaa-113">See also</span></span>

- [<span data-ttu-id="2acaa-114">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="2acaa-114">Input Overview</span></span>](input-overview.md)
