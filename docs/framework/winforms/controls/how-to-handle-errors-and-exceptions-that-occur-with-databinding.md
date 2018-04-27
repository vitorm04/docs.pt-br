---
title: Como identificar erros e exceções que ocorram na associação de dados
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
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 464ceb42416c91ae84c20c65fba2629479b1a0cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="aee14-102">Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="aee14-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="aee14-103">Muitas vezes, erros e exceções ocorrem nos objetos de negócios subjacentes quando você os associa aos controles.</span><span class="sxs-lookup"><span data-stu-id="aee14-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="aee14-104">Você pode interceptar esses erros e exceções e, em seguida, recuperar ou passar as informações de erro para o usuário manipulando o <xref:System.Windows.Forms.Binding.BindingComplete> eventos para um determinado <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, ou <xref:System.Windows.Forms.CurrencyManager> componente.</span><span class="sxs-lookup"><span data-stu-id="aee14-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aee14-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aee14-105">Example</span></span>  
 <span data-ttu-id="aee14-106">Este exemplo de código demonstra como tratar erros e exceções que ocorrem durante uma operação de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="aee14-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="aee14-107">Demonstra como interceptar erros manipulando o <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> evento o <xref:System.Windows.Forms.Binding> objetos.</span><span class="sxs-lookup"><span data-stu-id="aee14-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="aee14-108">Para interceptar erros e exceções ao manipular esse evento, você deve habilitar a formatação para a associação.</span><span class="sxs-lookup"><span data-stu-id="aee14-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="aee14-109">Você pode habilitar a formatação quando a associação é construída ou adicionada à coleção de associação, ou definindo o <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="aee14-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="aee14-110">Quando o código está em execução e uma cadeia de caracteres vazia é inserida para o nome da peça ou um valor menor que 100 é inserido para o número de peça, uma caixa de mensagem será exibida.</span><span class="sxs-lookup"><span data-stu-id="aee14-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="aee14-111">Este é um resultado de tratamento de <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> evento para essas associações de caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="aee14-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aee14-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="aee14-112">Compiling the Code</span></span>  
 <span data-ttu-id="aee14-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="aee14-113">This example requires:</span></span>  
  
-   <span data-ttu-id="aee14-114">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="aee14-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="aee14-115">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aee14-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="aee14-116">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="aee14-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="aee14-117">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="aee14-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee14-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aee14-118">See Also</span></span>  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [<span data-ttu-id="aee14-119">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="aee14-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
