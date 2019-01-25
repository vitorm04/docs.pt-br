---
title: 'Como: Associar controles dos Windows Forms a valores de banco de dados DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: b2a5c7234d2815da734ee291fef223f20744b81e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658124"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="942e0-102">Como: Associar controles dos Windows Forms a valores de banco de dados DBNull</span><span class="sxs-lookup"><span data-stu-id="942e0-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="942e0-103">Quando você associa os controles dos Windows Forms a uma fonte de dados e a fonte de dados retorna um <xref:System.DBNull> valor, você pode substituir um valor apropriado sem tratamento, formatação ou análise de eventos.</span><span class="sxs-lookup"><span data-stu-id="942e0-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="942e0-104">O <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade converterá <xref:System.DBNull> a um objeto especificado ao formatar ou analisar os valores de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="942e0-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="942e0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="942e0-105">Example</span></span>  
 <span data-ttu-id="942e0-106">O exemplo a seguir demonstra como associar um <xref:System.DBNull> valor em duas situações diferentes.</span><span class="sxs-lookup"><span data-stu-id="942e0-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="942e0-107">O primeiro demonstra como definir a <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de cadeia de caracteres; o segundo demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de imagem.</span><span class="sxs-lookup"><span data-stu-id="942e0-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="942e0-108">Os tipos de propriedade associada e o <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade deve ser iguais ou ocorrerá um erro e nenhuma outra <xref:System.Windows.Forms.Binding.NullValue%2A> valores serão processados.</span><span class="sxs-lookup"><span data-stu-id="942e0-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="942e0-109">Nessa situação, uma exceção não será gerada.</span><span class="sxs-lookup"><span data-stu-id="942e0-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="942e0-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="942e0-110">Compiling the Code</span></span>  
 <span data-ttu-id="942e0-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="942e0-111">This example requires:</span></span>  
  
-   <span data-ttu-id="942e0-112">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="942e0-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="942e0-113">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="942e0-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="942e0-114">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="942e0-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="942e0-115">Consulte também [como: Compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="942e0-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="942e0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="942e0-116">See also</span></span>
- [<span data-ttu-id="942e0-117">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="942e0-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="942e0-118">Como: Tratar erros e exceções que ocorrem na associação de dados</span><span class="sxs-lookup"><span data-stu-id="942e0-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="942e0-119">Como: Associar um controle dos Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="942e0-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
