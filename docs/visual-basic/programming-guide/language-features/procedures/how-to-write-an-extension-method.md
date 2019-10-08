---
title: 'Como: Gravar um método de extensão (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d01596d50db8ba1078e8ac82caa951418645c977
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004608"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="c3751-102">Como: Gravar um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3751-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="c3751-103">Os métodos de extensão permitem adicionar métodos a uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="c3751-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="c3751-104">O método de extensão pode ser chamado como se fosse uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="c3751-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="c3751-105">Para definir um método de extensão</span><span class="sxs-lookup"><span data-stu-id="c3751-105">To define an extension method</span></span>

1. <span data-ttu-id="c3751-106">Abra um aplicativo Visual Basic novo ou existente no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3751-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="c3751-107">Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução de importação:</span><span class="sxs-lookup"><span data-stu-id="c3751-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="c3751-108">Dentro de um módulo em seu aplicativo novo ou existente, inicie a definição do método com o atributo [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) :</span><span class="sxs-lookup"><span data-stu-id="c3751-108">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```
 
   <span data-ttu-id="c3751-109">Observe que o atributo `Extension` só pode ser aplicado a um método (um procedimento `Sub` ou `Function`) em um [módulo](../../../language-reference/statements/module-statement.md)Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3751-109">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="c3751-110">Se você aplicá-lo a um método em um `Class` ou um `Structure`, o compilador Visual Basic gerará o erro [BC36551](../../../misc/bc36551.md), "os métodos de extensão podem ser definidos somente em módulos."</span><span class="sxs-lookup"><span data-stu-id="c3751-110">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="c3751-111">Declare seu método de forma comum, exceto que o tipo do primeiro parâmetro deve ser o tipo de dados que você deseja estender.</span><span class="sxs-lookup"><span data-stu-id="c3751-111">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="c3751-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3751-112">Example</span></span>

 <span data-ttu-id="c3751-113">O exemplo a seguir declara um método de extensão no módulo `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="c3751-113">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="c3751-114">Um segundo módulo, `Module1`, importa `StringExtensions` e chama o método.</span><span class="sxs-lookup"><span data-stu-id="c3751-114">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="c3751-115">O método de extensão deve estar no escopo quando ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="c3751-115">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="c3751-116">O método de extensão `PrintAndPunctuate` estende a classe <xref:System.String> com um método que exibe a instância de cadeia de caracteres seguida por uma cadeia de caracteres de símbolos de pontuação enviados no como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c3751-116">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1
  
    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub
    
End Module
```
  
 <span data-ttu-id="c3751-117">Observe que o método é definido com dois parâmetros e é chamado com apenas um.</span><span class="sxs-lookup"><span data-stu-id="c3751-117">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="c3751-118">O primeiro parâmetro, `aString`, na definição do método é associado a `example`, a instância de `String` que chama o método.</span><span class="sxs-lookup"><span data-stu-id="c3751-118">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="c3751-119">A saída do exemplo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c3751-119">The output of the example is as follows:</span></span>
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a><span data-ttu-id="c3751-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3751-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="c3751-121">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="c3751-121">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="c3751-122">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="c3751-122">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="c3751-123">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="c3751-123">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c3751-124">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3751-124">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
