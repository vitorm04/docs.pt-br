---
title: Como chamar um método de extensão
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 38d6e8534283f475be2409f4b7c74ef48f1f248b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91074986"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="bd1c1-102">Como chamar um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd1c1-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="bd1c1-103">Os métodos de extensão permitem adicionar métodos a uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="bd1c1-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="bd1c1-104">Depois que um método de extensão é declarado e colocado no escopo, você pode chamá-lo como um método de instância do tipo que ele estende.</span><span class="sxs-lookup"><span data-stu-id="bd1c1-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="bd1c1-105">Para obter mais informações sobre como escrever um método de extensão, consulte [How to: Write a Extension Method](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="bd1c1-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="bd1c1-106">As instruções a seguir se referem ao método `PrintAndPunctuate` de extensão, que exibirá a instância de cadeia de caracteres que a invoca, seguida por qualquer valor enviado para o segundo parâmetro, `punc` .</span><span class="sxs-lookup"><span data-stu-id="bd1c1-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

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

<span data-ttu-id="bd1c1-107">O método deve estar no escopo quando for chamado.</span><span class="sxs-lookup"><span data-stu-id="bd1c1-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="bd1c1-108">Para chamar um método de extensão</span><span class="sxs-lookup"><span data-stu-id="bd1c1-108">To call an extension method</span></span>

1. <span data-ttu-id="bd1c1-109">Declare uma variável que tenha o tipo de dados do primeiro parâmetro do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="bd1c1-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="bd1c1-110">Para `PrintAndPunctuate` , você precisa de uma <xref:System.String> variável:</span><span class="sxs-lookup"><span data-stu-id="bd1c1-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="bd1c1-111">Essa variável invocará o método de extensão e seu valor será associado ao primeiro parâmetro, `aString` .</span><span class="sxs-lookup"><span data-stu-id="bd1c1-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="bd1c1-112">A seguinte instrução de chamada será exibida `Ready?` .</span><span class="sxs-lookup"><span data-stu-id="bd1c1-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="bd1c1-113">Observe que a chamada para esse método de extensão é semelhante a uma chamada para qualquer um dos <xref:System.String> métodos de instância que exigem um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="bd1c1-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="bd1c1-114">Declare outra variável de cadeia de caracteres e chame o método novamente para ver que ele funciona com qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bd1c1-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="bd1c1-115">O resultado desta vez é: `or not!!!` .</span><span class="sxs-lookup"><span data-stu-id="bd1c1-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="bd1c1-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd1c1-116">Example</span></span>

 <span data-ttu-id="bd1c1-117">O código a seguir é um exemplo completo da criação e uso de um método de extensão simples.</span><span class="sxs-lookup"><span data-stu-id="bd1c1-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bd1c1-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="bd1c1-118">See also</span></span>

- [<span data-ttu-id="bd1c1-119">Como escrever um método de extensão</span><span class="sxs-lookup"><span data-stu-id="bd1c1-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="bd1c1-120">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="bd1c1-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="bd1c1-121">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd1c1-121">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
