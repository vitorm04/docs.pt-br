---
title: 'Como: Como associar controles do Windows Forms a valores de banco de dados DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: cc3dde0db3dad6faff548951ff06a39d23248d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137755"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="f56f9-102">Como: Como associar controles do Windows Forms a valores de banco de dados DBNull</span><span class="sxs-lookup"><span data-stu-id="f56f9-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="f56f9-103">Quando você associa os controles dos Windows Forms a uma fonte de dados e a fonte de dados retorna um <xref:System.DBNull> valor, você pode substituir um valor apropriado sem tratamento, formatação ou análise de eventos.</span><span class="sxs-lookup"><span data-stu-id="f56f9-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="f56f9-104">O <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade converterá <xref:System.DBNull> a um objeto especificado ao formatar ou analisar os valores de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="f56f9-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f56f9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f56f9-105">Example</span></span>  
 <span data-ttu-id="f56f9-106">O exemplo a seguir demonstra como associar um <xref:System.DBNull> valor em duas situações diferentes.</span><span class="sxs-lookup"><span data-stu-id="f56f9-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="f56f9-107">O primeiro demonstra como definir a <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de cadeia de caracteres; o segundo demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de imagem.</span><span class="sxs-lookup"><span data-stu-id="f56f9-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="f56f9-108">Os tipos de propriedade associada e o <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade deve ser iguais ou ocorrerá um erro e nenhuma outra <xref:System.Windows.Forms.Binding.NullValue%2A> valores serão processados.</span><span class="sxs-lookup"><span data-stu-id="f56f9-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="f56f9-109">Nessa situação, uma exceção não será gerada.</span><span class="sxs-lookup"><span data-stu-id="f56f9-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f56f9-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f56f9-110">Compiling the Code</span></span>  
 <span data-ttu-id="f56f9-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f56f9-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f56f9-112">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f56f9-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f56f9-113">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f56f9-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f56f9-114">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="f56f9-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f56f9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f56f9-115">See also</span></span>

- [<span data-ttu-id="f56f9-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="f56f9-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="f56f9-117">Como: Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="f56f9-117">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="f56f9-118">Como: Associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="f56f9-118">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
