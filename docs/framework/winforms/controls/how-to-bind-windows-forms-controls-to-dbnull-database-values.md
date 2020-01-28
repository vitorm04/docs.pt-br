---
title: Associar controles a valores de banco de dados DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746667"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="d4af3-102">Como associar controles dos Windows Forms a valores de banco de dados DBNull</span><span class="sxs-lookup"><span data-stu-id="d4af3-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="d4af3-103">Quando você associa Windows Forms controles a uma fonte de dados e a fonte de dados retorna um valor de <xref:System.DBNull>, você pode substituir um valor apropriado sem manipular, formatar ou analisar eventos.</span><span class="sxs-lookup"><span data-stu-id="d4af3-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="d4af3-104">A propriedade <xref:System.Windows.Forms.Binding.NullValue%2A> converterá <xref:System.DBNull> em um objeto especificado ao Formatar ou analisar os valores da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d4af3-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4af3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4af3-105">Example</span></span>  
 <span data-ttu-id="d4af3-106">O exemplo a seguir demonstra como associar um valor de <xref:System.DBNull> em duas situações diferentes.</span><span class="sxs-lookup"><span data-stu-id="d4af3-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="d4af3-107">O primeiro demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de cadeia de caracteres; o segundo demonstra como definir o <xref:System.Windows.Forms.Binding.NullValue%2A> para uma propriedade de imagem.</span><span class="sxs-lookup"><span data-stu-id="d4af3-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="d4af3-108">Os tipos da propriedade bound e da propriedade <xref:System.Windows.Forms.Binding.NullValue%2A> devem ser iguais, ou um erro será resultado, e nenhum outro valor de <xref:System.Windows.Forms.Binding.NullValue%2A> será processado.</span><span class="sxs-lookup"><span data-stu-id="d4af3-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="d4af3-109">Nessa situação, uma exceção não será gerada.</span><span class="sxs-lookup"><span data-stu-id="d4af3-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d4af3-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="d4af3-110">Compiling the Code</span></span>  
 <span data-ttu-id="d4af3-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d4af3-111">This example requires:</span></span>  
  
- <span data-ttu-id="d4af3-112">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d4af3-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4af3-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="d4af3-113">See also</span></span>

- [<span data-ttu-id="d4af3-114">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="d4af3-114">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="d4af3-115">Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="d4af3-115">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="d4af3-116">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="d4af3-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
