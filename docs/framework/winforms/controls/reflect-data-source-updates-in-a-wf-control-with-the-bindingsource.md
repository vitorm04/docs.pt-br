---
title: 'Como: Refletir atualizações feitas na fonte de dados em um controle do Windows Forms com o BindingSource'
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
ms.openlocfilehash: 16dbe4da1efecd120d4da4d66c3d79ec907b92a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947986"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="c6dfe-102">Como: Refletir atualizações feitas na fonte de dados em um controle do Windows Forms com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="c6dfe-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="c6dfe-103">Quando você usa controles ligados a dados, às vezes, você precisa responder a alterações na fonte de dados quando a fonte de dados não gera eventos de alteração de lista.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="c6dfe-104">Quando você usa o <xref:System.Windows.Forms.BindingSource> componente para associar a fonte de dados a um controle Windows Forms, você pode notificar o controle que sua fonte de dados foi alterado, chamando o <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6dfe-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6dfe-105">Example</span></span>  
 <span data-ttu-id="c6dfe-106">O exemplo de código a seguir demonstra como usar o <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> método para notificar um controle associado sobre uma atualização na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6dfe-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c6dfe-107">Compiling the Code</span></span>  
 <span data-ttu-id="c6dfe-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c6dfe-108">This example requires:</span></span>  
  
- <span data-ttu-id="c6dfe-109">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c6dfe-110">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c6dfe-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c6dfe-111">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c6dfe-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6dfe-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6dfe-112">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="c6dfe-113">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="c6dfe-113">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="c6dfe-114">Como: Associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="c6dfe-114">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
