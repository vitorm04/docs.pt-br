---
title: Navegar pelos dados com o controle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736003"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="54c6c-102">Como navegar em dados com o controle BindingNavigator dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54c6c-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="54c6c-103">O advento do controle de <xref:System.Windows.Forms.BindingNavigator> no Windows Forms permite aos desenvolvedores fornecer aos usuários finais uma interface de usuário de navegação e manipulação de dados simples nos formulários que criam.</span><span class="sxs-lookup"><span data-stu-id="54c6c-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="54c6c-104">O controle de <xref:System.Windows.Forms.BindingNavigator> é um controle de <xref:System.Windows.Forms.ToolStrip> com botões pré-configurados para navegação no primeiro, último, próximo e registro anterior em um conjunto de dados, bem como botões para adicionar e excluir registros.</span><span class="sxs-lookup"><span data-stu-id="54c6c-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="54c6c-105">Adicionar botões ao controle de <xref:System.Windows.Forms.BindingNavigator> é fácil, pois é um controle de <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="54c6c-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="54c6c-106">Para obter exemplos, consulte [como: adicionar botões carregar, salvar e cancelar ao controle do Windows Forms BindingNavigator](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="54c6c-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="54c6c-107">Para cada botão no controle de <xref:System.Windows.Forms.BindingNavigator>, há um membro correspondente do componente <xref:System.Windows.Forms.BindingSource> que permite programaticamente a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="54c6c-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="54c6c-108">Por exemplo, o botão de <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> corresponde ao método <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> do componente <xref:System.Windows.Forms.BindingSource>, o botão <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> corresponde ao método <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="54c6c-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="54c6c-109">Como resultado, a habilitação do controle de <xref:System.Windows.Forms.BindingNavigator> para navegar pelos registros de dados é simples como definir sua propriedade <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> para o componente de <xref:System.Windows.Forms.BindingSource> apropriado no formulário.</span><span class="sxs-lookup"><span data-stu-id="54c6c-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="54c6c-110">Configurar o controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="54c6c-110">To set up the BindingNavigator control</span></span>  
  
1. <span data-ttu-id="54c6c-111">Adicione um componente de <xref:System.Windows.Forms.BindingSource> chamado `bindingSource1` e dois controles de <xref:System.Windows.Forms.TextBox> chamados `textBox1` e `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="54c6c-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2. <span data-ttu-id="54c6c-112">Associe `bindingSource1` a dados e os controles da caixa de texto a `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="54c6c-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="54c6c-113">Para fazer isso, Cole o código a seguir em seu formulário e chame `LoadData` no construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="54c6c-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="54c6c-114">Adicione um controle de <xref:System.Windows.Forms.BindingNavigator> chamado `bindingNavigator1` ao formulário.</span><span class="sxs-lookup"><span data-stu-id="54c6c-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4. <span data-ttu-id="54c6c-115">Defina a propriedade <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> para `bindingNavigator1` como `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="54c6c-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="54c6c-116">É possível fazer isso com o designer ou em código.</span><span class="sxs-lookup"><span data-stu-id="54c6c-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="54c6c-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54c6c-117">Example</span></span>  
 <span data-ttu-id="54c6c-118">O exemplo de código a seguir é o exemplo completo para as etapas listadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="54c6c-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54c6c-119">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="54c6c-119">Compiling the Code</span></span>  
 <span data-ttu-id="54c6c-120">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="54c6c-120">This example requires:</span></span>  
  
- <span data-ttu-id="54c6c-121">Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="54c6c-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c6c-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="54c6c-122">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="54c6c-123">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="54c6c-123">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="54c6c-124">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="54c6c-124">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
