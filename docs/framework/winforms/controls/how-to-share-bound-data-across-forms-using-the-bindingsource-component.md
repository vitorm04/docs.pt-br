---
title: 'Como: Compartilhar dados associados entre formulários usando o componente BindingSource'
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
ms.openlocfilehash: 19505c690728147d2a67c26371e1cea4c281ab08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154863"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="83f64-102">Como: Compartilhar dados associados entre formulários usando o componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="83f64-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="83f64-103">Você pode compartilhar facilmente dados entre formulários usando o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="83f64-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="83f64-104">Por exemplo, talvez você queira exibir um formulário de somente leitura que resume os dados de origem de dados e outro formulário editável que contém informações detalhadas sobre o item atualmente selecionado na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="83f64-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="83f64-105">Este exemplo demonstra esse cenário.</span><span class="sxs-lookup"><span data-stu-id="83f64-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f64-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83f64-106">Example</span></span>  
 <span data-ttu-id="83f64-107">O exemplo de código a seguir demonstra como compartilhar um <xref:System.Windows.Forms.BindingSource> e seus dados associados entre formulários.</span><span class="sxs-lookup"><span data-stu-id="83f64-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="83f64-108">Neste exemplo, o compartilhado <xref:System.Windows.Forms.BindingSource> é passado para o construtor do formulário filho.</span><span class="sxs-lookup"><span data-stu-id="83f64-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="83f64-109">O formulário filho permite que o usuário edite os dados para o atualmente item selecionado no formulário principal.</span><span class="sxs-lookup"><span data-stu-id="83f64-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83f64-110">O <xref:System.Windows.Forms.BindingSource.BindingComplete> evento para o <xref:System.Windows.Forms.BindingSource> componente é tratado no exemplo para garantir que os dois formulários permaneçam sincronizados.</span><span class="sxs-lookup"><span data-stu-id="83f64-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="83f64-111">Para obter mais informações sobre por que isso é feito, consulte [como: Certifique-se de vários controles associados à mesma fonte de dados permaneçam sincronizados](../multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="83f64-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83f64-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="83f64-112">Compiling the Code</span></span>  
 <span data-ttu-id="83f64-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="83f64-113">This example requires:</span></span>  
  
-   <span data-ttu-id="83f64-114">Referências aos assemblies System, System.Windows.Forms, System.Drawing, System.Data e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="83f64-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="83f64-115">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="83f64-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="83f64-116">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="83f64-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f64-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83f64-117">See also</span></span>

- [<span data-ttu-id="83f64-118">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="83f64-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="83f64-119">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83f64-119">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="83f64-120">Como: Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="83f64-120">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
