---
title: 'Como: Alterar o tipo de cursor'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 5c9e6931f6addb62a51e44b06a159d4e7b1e5f8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141200"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="7f780-102">Como: Alterar o tipo de cursor</span><span class="sxs-lookup"><span data-stu-id="7f780-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="7f780-103">Este exemplo mostra como alterar o <xref:System.Windows.Input.Cursor> do ponteiro do mouse para um elemento específico e para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7f780-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="7f780-104">Esse exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="7f780-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f780-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f780-105">Example</span></span>  
 <span data-ttu-id="7f780-106">A interface do usuário é criada, que consiste em uma <xref:System.Windows.Controls.ComboBox> para selecionar o desejado <xref:System.Windows.Input.Cursor>, um par de <xref:System.Windows.Controls.RadioButton> objetos para determinar se a mudança de cursor se aplica a apenas um único elemento ou se aplica a todo o aplicativo e um <xref:System.Windows.Controls.Border> qual é o elemento que o novo cursor é aplicado ao.</span><span class="sxs-lookup"><span data-stu-id="7f780-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="7f780-107">O código a seguir cria uma <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> manipulador de eventos que é chamado quando o tipo de cursor é alterado no <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="7f780-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="7f780-108">Uma instrução switch filtra o nome de cursor e define a <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade em de <xref:System.Windows.Controls.Border> que é denominado *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="7f780-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="7f780-109">Se a mudança de cursor for definida como "Aplicativo inteiro", o <xref:System.Windows.Input.Mouse.OverrideCursor%2A> estiver definida como o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade do <xref:System.Windows.Controls.Border> controle.</span><span class="sxs-lookup"><span data-stu-id="7f780-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="7f780-110">Isso força o cursor a mudar para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="7f780-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="7f780-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f780-111">See also</span></span>

- [<span data-ttu-id="7f780-112">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="7f780-112">Input Overview</span></span>](input-overview.md)
