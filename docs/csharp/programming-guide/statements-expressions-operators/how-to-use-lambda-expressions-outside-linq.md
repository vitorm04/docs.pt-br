---
title: Como usar expressões lambda fora do LINQ (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
ms.openlocfilehash: 6ba6c6f50b4d2f717de4325b5cd21434066b2899
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43389178"
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a><span data-ttu-id="d115e-102">Como usar expressões lambda fora do LINQ (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d115e-102">How to: Use Lambda Expressions Outside LINQ (C# Programming Guide)</span></span>
<span data-ttu-id="d115e-103">Expressões lambda não estão limitadas a consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d115e-103">Lambda expressions are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="d115e-104">Você pode usá-las em qualquer lugar em que um valor de delegado é esperado, ou seja, sempre que um método anônimo puder ser usado.</span><span class="sxs-lookup"><span data-stu-id="d115e-104">You can use them anywhere a delegate value is expected, that is, wherever an anonymous method can be used.</span></span> <span data-ttu-id="d115e-105">O exemplo a seguir mostra como usar uma expressão lambda em um manipulador de eventos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d115e-105">The following example shows how to use a lambda expression in a Windows Forms event handler.</span></span> <span data-ttu-id="d115e-106">Observe que os tipos das entradas (<xref:System.Object> e <xref:System.Windows.Forms.MouseEventArgs>) são inferidos pelo compilador e não precisam ser explicitamente fornecidos nos parâmetros de entrada lambda.</span><span class="sxs-lookup"><span data-stu-id="d115e-106">Notice that the types of the inputs (<xref:System.Object> and <xref:System.Windows.Forms.MouseEventArgs>) are inferred by the compiler and do not have to be explicitly given in the lambda input parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d115e-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d115e-107">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="d115e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d115e-108">See Also</span></span>  
 [<span data-ttu-id="d115e-109">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="d115e-109">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="d115e-110">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="d115e-110">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="d115e-111">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="d115e-111">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
