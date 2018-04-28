---
title: Como associar controles dos Windows Forms a valores de banco de dados DBNull
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
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45bfed3020f0fe148e9f7d33b9ec7dc243eb5c29
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="87fd3-102">Como associar controles dos Windows Forms a valores de banco de dados DBNull</span><span class="sxs-lookup"><span data-stu-id="87fd3-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="87fd3-103">Quando você associa os controles de formulários do Windows para uma fonte de dados e a fonte de dados retorna um <xref:System.DBNull> valor, você pode substituir um valor apropriado sem tratamento, formatação ou eventos de análise.</span><span class="sxs-lookup"><span data-stu-id="87fd3-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="87fd3-104">O <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade converterá <xref:System.DBNull> ao objeto especificado quando formatação ou os valores de fonte de dados de análise.</span><span class="sxs-lookup"><span data-stu-id="87fd3-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87fd3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87fd3-105">Example</span></span>  
 <span data-ttu-id="87fd3-106">O exemplo a seguir demonstra como vincular um <xref:System.DBNull> valor em duas situações diferentes.</span><span class="sxs-lookup"><span data-stu-id="87fd3-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="87fd3-107">A primeira demonstra como definir a <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de cadeia de caracteres; o segundo demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de imagem.</span><span class="sxs-lookup"><span data-stu-id="87fd3-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="87fd3-108">Os tipos de propriedade associada e o <xref:System.Windows.Forms.Binding.NullValue%2A> propriedade deve ser o mesmo ou ocorrerá um erro e nenhuma outra <xref:System.Windows.Forms.Binding.NullValue%2A> valores serão processados.</span><span class="sxs-lookup"><span data-stu-id="87fd3-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="87fd3-109">Nessa situação, uma exceção não será gerada.</span><span class="sxs-lookup"><span data-stu-id="87fd3-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87fd3-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="87fd3-110">Compiling the Code</span></span>  
 <span data-ttu-id="87fd3-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="87fd3-111">This example requires:</span></span>  
  
-   <span data-ttu-id="87fd3-112">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="87fd3-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="87fd3-113">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="87fd3-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="87fd3-114">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="87fd3-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="87fd3-115">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="87fd3-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fd3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87fd3-116">See Also</span></span>  
 [<span data-ttu-id="87fd3-117">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="87fd3-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="87fd3-118">Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="87fd3-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [<span data-ttu-id="87fd3-119">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="87fd3-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
