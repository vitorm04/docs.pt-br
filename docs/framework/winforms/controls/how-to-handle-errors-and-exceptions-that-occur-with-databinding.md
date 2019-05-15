---
title: 'Como: Como identificar erros e exceções que ocorram na associação de dados'
ms.date: 03/30/2017
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
ms.openlocfilehash: 14326d793be3ee71022a7a1e7398b9af469aab10
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592454"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="76c36-102">Como: Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="76c36-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="76c36-103">Muitas vezes, erros e exceções ocorrem nos objetos de negócios subjacentes quando você os associa aos controles.</span><span class="sxs-lookup"><span data-stu-id="76c36-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="76c36-104">Você pode interceptar esses erros e exceções e, em seguida, recuperar ou passar as informações de erro para o usuário manipulando o <xref:System.Windows.Forms.Binding.BindingComplete> eventos para um determinado <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, ou <xref:System.Windows.Forms.CurrencyManager> componente.</span><span class="sxs-lookup"><span data-stu-id="76c36-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76c36-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76c36-105">Example</span></span>  
 <span data-ttu-id="76c36-106">Este exemplo de código demonstra como tratar erros e exceções que ocorrem durante uma operação de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="76c36-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="76c36-107">Ele demonstra como interceptar erros manipulando o <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> eventos do <xref:System.Windows.Forms.Binding> objetos.</span><span class="sxs-lookup"><span data-stu-id="76c36-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="76c36-108">Para interceptar erros e exceções ao manipular esse evento, você deve habilitar a formatação para a associação.</span><span class="sxs-lookup"><span data-stu-id="76c36-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="76c36-109">Você pode habilitar a formatação quando a associação for construída ou adicionada à coleção de associação ou definindo o <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="76c36-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="76c36-110">Quando o código está em execução e uma cadeia de caracteres vazia é inserida para o nome da peça ou um valor menor que 100 é inserido para o número de peça, uma caixa de mensagem será exibida.</span><span class="sxs-lookup"><span data-stu-id="76c36-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="76c36-111">Este é um resultado de tratamento de <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> evento para essas associações de caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="76c36-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76c36-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="76c36-112">Compiling the Code</span></span>  
 <span data-ttu-id="76c36-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="76c36-113">This example requires:</span></span>  
  
- <span data-ttu-id="76c36-114">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="76c36-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c36-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76c36-115">See also</span></span>

- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [<span data-ttu-id="76c36-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="76c36-116">BindingSource Component</span></span>](bindingsource-component.md)
