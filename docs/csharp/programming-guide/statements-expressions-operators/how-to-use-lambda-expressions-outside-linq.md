---
title: 'Como: usar expressões lambda fora do LINQ – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: d4dc0375552ef1fe00f629c22b5296399b4cc99d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243927"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="ba264-102">Como: usar expressões lambda fora do LINQ (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ba264-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="ba264-103">Expressões lambda não estão limitadas a consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba264-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="ba264-104">Você pode usá-las em qualquer lugar em que um valor de delegado é esperado, ou seja, sempre que um método anônimo puder ser usado.</span><span class="sxs-lookup"><span data-stu-id="ba264-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="ba264-105">O exemplo a seguir mostra como usar uma expressão lambda em um manipulador de eventos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ba264-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="ba264-106">Observe que os tipos das entradas (<xref:System.Object> e <xref:System.Windows.Forms.MouseEventArgs>) são inferidos pelo compilador e não precisam ser explicitamente fornecidos nos parâmetros de entrada lambda.</span><span class="sxs-lookup"><span data-stu-id="ba264-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba264-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba264-107">Example</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba264-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba264-108">See Also</span></span>

- [<span data-ttu-id="ba264-109">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="ba264-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [<span data-ttu-id="ba264-110">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="ba264-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [<span data-ttu-id="ba264-111">LINQ (Consulta integrada à linguagem)</span><span class="sxs-lookup"><span data-stu-id="ba264-111">Language Integrated Query (LINQ))</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
