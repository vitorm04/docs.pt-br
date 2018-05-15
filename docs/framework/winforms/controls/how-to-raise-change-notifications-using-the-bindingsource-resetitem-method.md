---
title: Como acionar notificações de alteração usando o método BindingSource ResetItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 5894e7036126cb5271cea65e6025e9880b0cbe3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="268e7-102">Como acionar notificações de alteração usando o método BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="268e7-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="268e7-103">Algumas fontes de dados para os controles não acionar notificações de alteração quando itens são alterados, adicionados ou excluídos.</span><span class="sxs-lookup"><span data-stu-id="268e7-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="268e7-104">Com o <xref:System.Windows.Forms.BindingSource> componente, você pode associar a essas fontes de dados e gerar uma notificação de alteração de seu código.</span><span class="sxs-lookup"><span data-stu-id="268e7-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268e7-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="268e7-105">Example</span></span>  
 <span data-ttu-id="268e7-106">Este formulário demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para associar uma lista para um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="268e7-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="268e7-107">A lista não gera notificações de alteração, portanto, o <xref:System.Windows.Forms.BindingSource.ResetItem%2A> método no <xref:System.Windows.Forms.BindingSource> é chamado quando um item na lista é alterado.</span><span class="sxs-lookup"><span data-stu-id="268e7-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="268e7-108">.</span><span class="sxs-lookup"><span data-stu-id="268e7-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="268e7-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="268e7-109">Compiling the Code</span></span>  
 <span data-ttu-id="268e7-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="268e7-110">This example requires:</span></span>  
  
-   <span data-ttu-id="268e7-111">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="268e7-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="268e7-112">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="268e7-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="268e7-113">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="268e7-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="268e7-114">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="268e7-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268e7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="268e7-115">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="268e7-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="268e7-116">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="268e7-117">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="268e7-117">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
