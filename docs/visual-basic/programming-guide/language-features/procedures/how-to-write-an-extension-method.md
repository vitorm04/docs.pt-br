---
title: 'Como: Escrever um método de extensão (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 00d62d275f7afc06e066a375dc1ffcd74b23c9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665995"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="ca64c-102">Como: Escrever um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca64c-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="ca64c-103">Métodos de extensão permitem adicionar métodos a uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="ca64c-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="ca64c-104">O método de extensão pode ser chamado como se fosse uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ca64c-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="ca64c-105">Para definir um método de extensão</span><span class="sxs-lookup"><span data-stu-id="ca64c-105">To define an extension method</span></span>  
  
1. <span data-ttu-id="ca64c-106">Abra um aplicativo novo ou existente do Visual Basic no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca64c-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2. <span data-ttu-id="ca64c-107">Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução de importação:</span><span class="sxs-lookup"><span data-stu-id="ca64c-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3. <span data-ttu-id="ca64c-108">Dentro de um módulo em seu aplicativo novo ou existente, começar a definição do método com o atributo de extensão:</span><span class="sxs-lookup"><span data-stu-id="ca64c-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4. <span data-ttu-id="ca64c-109">Declare seu método da maneira normal, exceto que o tipo do primeiro parâmetro deve ser o tipo de dados que você deseja estender.</span><span class="sxs-lookup"><span data-stu-id="ca64c-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="ca64c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca64c-110">Example</span></span>  
 <span data-ttu-id="ca64c-111">O exemplo a seguir declara um método de extensão no módulo `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="ca64c-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="ca64c-112">Um módulo de segunda `Module1`, importa `StringExtensions` e chama o método.</span><span class="sxs-lookup"><span data-stu-id="ca64c-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="ca64c-113">O método de extensão deve estar no escopo quando ela é chamada.</span><span class="sxs-lookup"><span data-stu-id="ca64c-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="ca64c-114">Método de extensão `PrintAndPunctuate` estende o <xref:System.String> classe com um método que exibe a instância de cadeia de caracteres seguida por uma cadeia de caracteres de símbolos de pontuação enviado como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ca64c-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
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
  
 <span data-ttu-id="ca64c-115">Observe que o método é definido com dois parâmetros e chamado com apenas um.</span><span class="sxs-lookup"><span data-stu-id="ca64c-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="ca64c-116">O primeiro parâmetro, `aString`, o método de definição é associada a `example`, a instância do `String` que chama o método.</span><span class="sxs-lookup"><span data-stu-id="ca64c-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="ca64c-117">A saída do exemplo é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ca64c-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="ca64c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca64c-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="ca64c-119">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="ca64c-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="ca64c-120">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="ca64c-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="ca64c-121">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="ca64c-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ca64c-122">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca64c-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
