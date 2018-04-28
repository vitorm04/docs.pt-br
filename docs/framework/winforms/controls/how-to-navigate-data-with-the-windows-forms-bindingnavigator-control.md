---
title: Como navegar em dados com o controle BindingNavigator dos Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99ed6b7232dd80733fea3c9f36722b0722dc1525
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="45dfd-102">Como navegar em dados com o controle BindingNavigator dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45dfd-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="45dfd-103">O surgimento do <xref:System.Windows.Forms.BindingNavigator> controle em formulários do Windows permite que os desenvolvedores fornecer aos usuários finais com dados simples navegação e manipulação de interface do usuário em formulários de criar.</span><span class="sxs-lookup"><span data-stu-id="45dfd-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="45dfd-104">O <xref:System.Windows.Forms.BindingNavigator> controle é um <xref:System.Windows.Forms.ToolStrip> controle com botões pré-configurado para a navegação para a primeira, última, registro próximo e anterior em um conjunto de dados, bem como os botões para adicionar e excluir registros.</span><span class="sxs-lookup"><span data-stu-id="45dfd-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="45dfd-105">Adicionando botões para o <xref:System.Windows.Forms.BindingNavigator> controle é fácil, porque é um <xref:System.Windows.Forms.ToolStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="45dfd-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="45dfd-106">Consulte também [Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="45dfd-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="45dfd-107">Para cada botão de <xref:System.Windows.Forms.BindingNavigator> controlar, existe um membro correspondente do <xref:System.Windows.Forms.BindingSource> componente que programaticamente permite que a mesma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="45dfd-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="45dfd-108">Por exemplo, o <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> método do <xref:System.Windows.Forms.BindingSource> componente, o <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> método e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="45dfd-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="45dfd-109">Como resultado, habilitando o <xref:System.Windows.Forms.BindingNavigator> controle para navegar pelos registros de dados é um simples como configuração de seu <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade apropriada <xref:System.Windows.Forms.BindingSource> componente no formulário.</span><span class="sxs-lookup"><span data-stu-id="45dfd-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="45dfd-110">Configurar o controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="45dfd-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="45dfd-111">Adicionar um <xref:System.Windows.Forms.BindingSource> componente denominado `bindingSource1` e dois <xref:System.Windows.Forms.TextBox> controles denominados `textBox1` e `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="45dfd-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="45dfd-112">Associe `bindingSource1` a dados e os controles da caixa de texto a `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="45dfd-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="45dfd-113">Para fazer isso, cole o código a seguir no seu formulário e chamada `LoadData` do construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="45dfd-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="45dfd-114">Adicionar um <xref:System.Windows.Forms.BindingNavigator> controle chamado `bindingNavigator1` ao formulário.</span><span class="sxs-lookup"><span data-stu-id="45dfd-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="45dfd-115">Definir o <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade `bindingNavigator1` para `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="45dfd-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="45dfd-116">É possível fazer isso com o designer ou em código.</span><span class="sxs-lookup"><span data-stu-id="45dfd-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="45dfd-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45dfd-117">Example</span></span>  
 <span data-ttu-id="45dfd-118">O exemplo de código a seguir é o exemplo completo para as etapas listadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="45dfd-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45dfd-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="45dfd-119">Compiling the Code</span></span>  
 <span data-ttu-id="45dfd-120">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="45dfd-120">This example requires:</span></span>  
  
-   <span data-ttu-id="45dfd-121">Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="45dfd-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="45dfd-122">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="45dfd-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="45dfd-123">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="45dfd-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="45dfd-124">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="45dfd-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45dfd-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45dfd-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="45dfd-126">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="45dfd-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="45dfd-127">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="45dfd-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
