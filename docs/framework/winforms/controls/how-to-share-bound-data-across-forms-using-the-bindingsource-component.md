---
title: Como compartilhar dados associados entre formulários usando o componente BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: 765bdb7ee75d7e0c6461311263afe9481830673f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198758"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="539a4-102">Como compartilhar dados associados entre formulários usando o componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="539a4-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="539a4-103">Você pode compartilhar facilmente dados entre formulários usando o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="539a4-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="539a4-104">Por exemplo, talvez você queira exibir um formulário de somente leitura que resume os dados de origem de dados e outro formulário editável que contém informações detalhadas sobre o item atualmente selecionado na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="539a4-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="539a4-105">Este exemplo demonstra esse cenário.</span><span class="sxs-lookup"><span data-stu-id="539a4-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="539a4-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="539a4-106">Example</span></span>  
 <span data-ttu-id="539a4-107">O exemplo de código a seguir demonstra como compartilhar um <xref:System.Windows.Forms.BindingSource> e seus dados associados entre formulários.</span><span class="sxs-lookup"><span data-stu-id="539a4-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="539a4-108">Neste exemplo, o compartilhado <xref:System.Windows.Forms.BindingSource> é passado para o construtor do formulário filho.</span><span class="sxs-lookup"><span data-stu-id="539a4-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="539a4-109">O formulário filho permite que o usuário edite os dados para o atualmente item selecionado no formulário principal.</span><span class="sxs-lookup"><span data-stu-id="539a4-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="539a4-110">O <xref:System.Windows.Forms.BindingSource.BindingComplete> evento para o <xref:System.Windows.Forms.BindingSource> componente é tratado no exemplo para garantir que os dois formulários permaneçam sincronizados.</span><span class="sxs-lookup"><span data-stu-id="539a4-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="539a4-111">Para obter mais informações sobre o motivo de isso ser feito, consulte [Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="539a4-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="539a4-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="539a4-112">Compiling the Code</span></span>  
 <span data-ttu-id="539a4-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="539a4-113">This example requires:</span></span>  
  
-   <span data-ttu-id="539a4-114">Referências aos assemblies System, System.Windows.Forms, System.Drawing, System.Data e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="539a4-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="539a4-115">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="539a4-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="539a4-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="539a4-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="539a4-117">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="539a4-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="539a4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="539a4-118">See Also</span></span>  
 [<span data-ttu-id="539a4-119">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="539a4-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="539a4-120">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="539a4-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="539a4-121">Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="539a4-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
