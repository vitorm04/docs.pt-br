---
title: 'Como: Detectar quando o texto em um TextBox foi alterado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855612"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="fcf00-102">Como: Detectar quando o texto em um TextBox foi alterado</span><span class="sxs-lookup"><span data-stu-id="fcf00-102">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="fcf00-103">Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento para executar um método sempre que o texto em <xref:System.Windows.Controls.TextBox> um controle for alterado.</span><span class="sxs-lookup"><span data-stu-id="fcf00-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="fcf00-104">Na classe code-behind para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar para as alterações, insira um método a ser chamado sempre que <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento for disparado.</span><span class="sxs-lookup"><span data-stu-id="fcf00-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="fcf00-105">Esse método deve ter uma assinatura que corresponda ao que é esperado pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegado.</span><span class="sxs-lookup"><span data-stu-id="fcf00-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="fcf00-106">O manipulador de eventos é chamado sempre que o conteúdo <xref:System.Windows.Controls.TextBox> do controle é alterado, seja por um usuário ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="fcf00-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="fcf00-107">Esse evento é acionado <xref:System.Windows.Controls.TextBox> quando o controle é criado e preenchido inicialmente com texto.</span><span class="sxs-lookup"><span data-stu-id="fcf00-107">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="fcf00-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcf00-108">Example</span></span>

<span data-ttu-id="fcf00-109">No que define seu <xref:System.Windows.Controls.TextBox> controle, especifique o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributo com um valor que corresponda ao nome do método do manipulador de eventos. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf00-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="fcf00-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcf00-110">Example</span></span>

<span data-ttu-id="fcf00-111">Na classe code-behind para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar para as alterações, insira um método a ser chamado sempre que <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento for disparado.</span><span class="sxs-lookup"><span data-stu-id="fcf00-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="fcf00-112">Esse método deve ter uma assinatura que corresponda ao que é esperado pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegado.</span><span class="sxs-lookup"><span data-stu-id="fcf00-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="fcf00-113">O manipulador de eventos é chamado sempre que o conteúdo <xref:System.Windows.Controls.TextBox> do controle é alterado, seja por um usuário ou programaticamente.</span><span class="sxs-lookup"><span data-stu-id="fcf00-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="fcf00-114">Esse evento é acionado <xref:System.Windows.Controls.TextBox> quando o controle é criado e preenchido inicialmente com texto.</span><span class="sxs-lookup"><span data-stu-id="fcf00-114">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="fcf00-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcf00-115">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="fcf00-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcf00-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="fcf00-117">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="fcf00-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="fcf00-118">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fcf00-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
