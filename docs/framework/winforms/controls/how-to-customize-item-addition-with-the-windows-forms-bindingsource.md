---
title: "Como personalizar a adição de item com o BindingSource dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 807aa16e4d70a105bcd2fb1426a94d6fdcebbf31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="7c60f-102">Como personalizar a adição de item com o BindingSource dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c60f-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="7c60f-103">Quando você usa um <xref:System.Windows.Forms.BindingSource> componente para associar um controle de formulários do Windows a uma fonte de dados, talvez seja necessário personalizar a criação de novos itens.</span><span class="sxs-lookup"><span data-stu-id="7c60f-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="7c60f-104">O <xref:System.Windows.Forms.BindingSource> componente facilita isso fornecendo o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, que normalmente é gerado quando o controle associado precisa criar um novo item.</span><span class="sxs-lookup"><span data-stu-id="7c60f-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="7c60f-105">O manipulador de eventos pode fornecer qualquer comportamento personalizado necessário (por exemplo, chamar um método em um serviço Web ou obter um novo objeto de uma fábrica de classes).</span><span class="sxs-lookup"><span data-stu-id="7c60f-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c60f-106">Quando um item é adicionado ao manipular o <xref:System.Windows.Forms.BindingSource.AddingNew> evento, a adição não pode ser cancelada.</span><span class="sxs-lookup"><span data-stu-id="7c60f-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c60f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7c60f-107">Example</span></span>  
 <span data-ttu-id="7c60f-108">O exemplo a seguir demonstra como vincular um <xref:System.Windows.Forms.DataGridView> controle a uma fábrica de classe usando um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="7c60f-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="7c60f-109">Quando o usuário clica o <xref:System.Windows.Forms.DataGridView> linha nova do controle de <xref:System.Windows.Forms.BindingSource.AddingNew> é gerado.</span><span class="sxs-lookup"><span data-stu-id="7c60f-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="7c60f-110">O manipulador de eventos cria um novo `DemoCustomer` objeto, que é atribuído para o <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7c60f-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7c60f-111">Isso faz com que o novo `DemoCustomer` o objeto a ser adicionado para o <xref:System.Windows.Forms.BindingSource> lista do componente e a serem exibidos na nova linha do <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="7c60f-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c60f-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7c60f-112">Compiling the Code</span></span>  
 <span data-ttu-id="7c60f-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="7c60f-113">This example requires:</span></span>  
  
-   <span data-ttu-id="7c60f-114">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7c60f-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7c60f-115">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7c60f-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7c60f-116">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="7c60f-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="7c60f-117">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7c60f-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c60f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c60f-118">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="7c60f-119">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="7c60f-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="7c60f-120">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="7c60f-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
