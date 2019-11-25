---
title: Como chamar um método de extensão
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340404"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="5c913-102">Como chamar um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c913-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="5c913-103">Extension methods enable you to add methods to an existing class.</span><span class="sxs-lookup"><span data-stu-id="5c913-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="5c913-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span><span class="sxs-lookup"><span data-stu-id="5c913-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="5c913-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c913-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="5c913-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span><span class="sxs-lookup"><span data-stu-id="5c913-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

<span data-ttu-id="5c913-107">The method must be in scope when it is called.</span><span class="sxs-lookup"><span data-stu-id="5c913-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="5c913-108">To call an extension method</span><span class="sxs-lookup"><span data-stu-id="5c913-108">To call an extension method</span></span>

1. <span data-ttu-id="5c913-109">Declare a variable that has the data type of the first parameter of the extension method.</span><span class="sxs-lookup"><span data-stu-id="5c913-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="5c913-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span><span class="sxs-lookup"><span data-stu-id="5c913-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="5c913-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span><span class="sxs-lookup"><span data-stu-id="5c913-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="5c913-112">The following calling statement will display `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="5c913-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="5c913-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span><span class="sxs-lookup"><span data-stu-id="5c913-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="5c913-114">Declare another string variable and call the method again to see that it works with any string.</span><span class="sxs-lookup"><span data-stu-id="5c913-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="5c913-115">The result this time is: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="5c913-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="5c913-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c913-116">Example</span></span>
 <span data-ttu-id="5c913-117">The following code is a complete example of the creation and use of a simple extension method.</span><span class="sxs-lookup"><span data-stu-id="5c913-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a><span data-ttu-id="5c913-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c913-118">See also</span></span>

- [<span data-ttu-id="5c913-119">Como escrever um método de extensão</span><span class="sxs-lookup"><span data-stu-id="5c913-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="5c913-120">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="5c913-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="5c913-121">Scope in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c913-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
