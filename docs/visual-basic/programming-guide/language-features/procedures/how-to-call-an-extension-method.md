---
title: Como chamar um método de extensão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648561"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="358d6-102">Como chamar um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="358d6-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="358d6-103">Métodos de extensão permitem adicionar métodos a uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="358d6-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="358d6-104">Depois que um método de extensão é declarado e colocado no escopo, você pode chamá-lo como um método de instância do tipo que ele estende.</span><span class="sxs-lookup"><span data-stu-id="358d6-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="358d6-105">Para obter mais informações sobre como escrever um método de extensão, consulte [como: gravar um método de extensão](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="358d6-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="358d6-106">Consultem as instruções a seguir para o método de extensão `PrintAndPunctuate`, que exibirá a instância de cadeia de caracteres que o chama, seguido de qualquer valor que será enviada para o segundo parâmetro, `punc`.</span><span class="sxs-lookup"><span data-stu-id="358d6-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
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
  
 <span data-ttu-id="358d6-107">O método deve ser no escopo quando ela é chamada.</span><span class="sxs-lookup"><span data-stu-id="358d6-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="358d6-108">Para chamar um método de extensão</span><span class="sxs-lookup"><span data-stu-id="358d6-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="358d6-109">Declare uma variável que tem o tipo de dados do primeiro parâmetro do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="358d6-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="358d6-110">Para `PrintAndPunctuate`, é necessário um <xref:System.String> variável:</span><span class="sxs-lookup"><span data-stu-id="358d6-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="358d6-111">Que a variável chamará o método de extensão, e seu valor é vinculado ao primeiro parâmetro, `aString`.</span><span class="sxs-lookup"><span data-stu-id="358d6-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="358d6-112">Exibirá a seguinte instrução de chamada `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="358d6-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="358d6-113">Observe que a chamada para esse método de extensão é apenas como uma chamada para qualquer uma da <xref:System.String> métodos que exigem um parâmetro da instância:</span><span class="sxs-lookup"><span data-stu-id="358d6-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="358d6-114">Declarar a outra variável de cadeia de caracteres e chame o método novamente para ver se ele funciona com qualquer cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="358d6-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="358d6-115">Dessa vez, o resultado é: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="358d6-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="358d6-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="358d6-116">Example</span></span>  
 <span data-ttu-id="358d6-117">O código a seguir é um exemplo completo de criação e uso de um método de extensão simples.</span><span class="sxs-lookup"><span data-stu-id="358d6-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="358d6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="358d6-118">See Also</span></span>  
 [<span data-ttu-id="358d6-119">Como escrever um método de extensão</span><span class="sxs-lookup"><span data-stu-id="358d6-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)  
 [<span data-ttu-id="358d6-120">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="358d6-120">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="358d6-121">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="358d6-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
