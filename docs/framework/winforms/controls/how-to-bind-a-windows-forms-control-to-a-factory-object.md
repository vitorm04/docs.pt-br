---
title: Como associar um controle dos Windows Forms a um objeto de alocador
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
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b433beaa67fa3c8d574f7b07e1d2f12af8b3dd00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="ac974-102">Como associar um controle dos Windows Forms a um objeto de alocador</span><span class="sxs-lookup"><span data-stu-id="ac974-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="ac974-103">Quando você estiver criando controles que interagem com os dados, às vezes, será necessário associar um controle a um objeto ou método que gere outros objetos.</span><span class="sxs-lookup"><span data-stu-id="ac974-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="ac974-104">Esse objeto ou método é chamado de alocador.</span><span class="sxs-lookup"><span data-stu-id="ac974-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="ac974-105">A fonte de dados pode ser, por exemplo, o valor retornado de uma chamada de método, em vez de um objeto na memória ou um tipo.</span><span class="sxs-lookup"><span data-stu-id="ac974-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="ac974-106">Você pode associar um controle a esse tipo de fonte de dados desde que a fonte retorne uma coleção.</span><span class="sxs-lookup"><span data-stu-id="ac974-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="ac974-107">Você pode facilmente associar um controle a um objeto de fábrica usando o <xref:System.Windows.Forms.BindingSource> controle.</span><span class="sxs-lookup"><span data-stu-id="ac974-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac974-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac974-108">Example</span></span>  
 <span data-ttu-id="ac974-109">O exemplo a seguir demonstra como vincular um <xref:System.Windows.Forms.DataGridView> controle a um método de fábrica usando um <xref:System.Windows.Forms.BindingSource> controle.</span><span class="sxs-lookup"><span data-stu-id="ac974-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="ac974-110">O método de fábrica chama-se `GetOrdersByCustomerId` e retorna todos os pedidos para determinado cliente no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="ac974-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac974-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ac974-111">Compiling the Code</span></span>  
 <span data-ttu-id="ac974-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="ac974-112">This example requires:</span></span>  
  
-   <span data-ttu-id="ac974-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ac974-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ac974-114">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ac974-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ac974-115">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="ac974-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="ac974-116">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ac974-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac974-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac974-117">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="ac974-118">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="ac974-118">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="ac974-119">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="ac974-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
