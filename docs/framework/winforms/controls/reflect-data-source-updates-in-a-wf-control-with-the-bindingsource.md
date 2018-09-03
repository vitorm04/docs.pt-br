---
title: Como refletir atualizações feitas na fonte de dados em um controle dos Windows Forms com o BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: 95e17675011b7e4d628b980fc0cbf15a50ce3932
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465636"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="0acea-102">Como refletir atualizações feitas na fonte de dados em um controle dos Windows Forms com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="0acea-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="0acea-103">Quando você usa controles ligados a dados, às vezes, você precisa responder a alterações na fonte de dados quando a fonte de dados não gera eventos de alteração de lista.</span><span class="sxs-lookup"><span data-stu-id="0acea-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="0acea-104">Quando você usa o <xref:System.Windows.Forms.BindingSource> componente para associar a fonte de dados a um controle Windows Forms, você pode notificar o controle que sua fonte de dados foi alterado, chamando o <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0acea-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0acea-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0acea-105">Example</span></span>  
 <span data-ttu-id="0acea-106">O exemplo de código a seguir demonstra como usar o <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> método para notificar um controle associado sobre uma atualização na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0acea-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0acea-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0acea-107">Compiling the Code</span></span>  
 <span data-ttu-id="0acea-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="0acea-108">This example requires:</span></span>  
  
-   <span data-ttu-id="0acea-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0acea-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0acea-110">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0acea-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0acea-111">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="0acea-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0acea-112">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0acea-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acea-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0acea-113">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="0acea-114">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="0acea-114">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="0acea-115">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="0acea-115">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
