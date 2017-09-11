---
title: "Como: gravar um método de extensão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- writing extension methods
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fb263e1e87dedc6dcf3ffa9e1e0d64235024c87d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="9ff7a-102">Como escrever um método de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ff7a-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="9ff7a-103">Métodos de extensão permitem adicionar métodos a uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="9ff7a-104">O método de extensão pode ser chamado como se fosse uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="9ff7a-105">Para definir um método de extensão</span><span class="sxs-lookup"><span data-stu-id="9ff7a-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="9ff7a-106">Abra um aplicativo novo ou existente do Visual Basic no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="9ff7a-107">Na parte superior do arquivo no qual você deseja definir um método de extensão, inclua a seguinte instrução import:</span><span class="sxs-lookup"><span data-stu-id="9ff7a-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="9ff7a-108">Dentro de um módulo em seu aplicativo novo ou existente, começar a definição do método com o atributo de extensão:</span><span class="sxs-lookup"><span data-stu-id="9ff7a-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="9ff7a-109">Declare o método da maneira normal, exceto que o tipo do primeiro parâmetro deve ser do tipo de dados que você deseja estender.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="9ff7a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ff7a-110">Example</span></span>  
 <span data-ttu-id="9ff7a-111">O exemplo a seguir declara um método de extensão no módulo `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="9ff7a-112">Um segundo módulo, `Module1`, importa `StringExtensions` e chama o método.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="9ff7a-113">O método de extensão deve estar no escopo quando ela é chamada.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="9ff7a-114">Método de extensão `PrintAndPunctuate` estende o <xref:System.String>classe com um método que exibe a instância de cadeia de caracteres, seguido por uma cadeia de caracteres de símbolos de pontuação enviados em como um parâmetro.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="9ff7a-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="9ff7a-115">Observe que o método é definido com dois parâmetros e chamado com apenas um.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="9ff7a-116">O primeiro parâmetro, `aString`, no método definição está associada a `example`, a instância de `String` que chama o método.</span><span class="sxs-lookup"><span data-stu-id="9ff7a-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="9ff7a-117">A saída do exemplo é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9ff7a-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="9ff7a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ff7a-118">See Also</span></span>  
 <span data-ttu-id="9ff7a-119"><xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="9ff7a-119"><xref:System.Runtime.CompilerServices.ExtensionAttribute></span></span>   
<span data-ttu-id="9ff7a-120"> [Métodos de extensão](./extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="9ff7a-120"> [Extension Methods](./extension-methods.md) </span></span>  
<span data-ttu-id="9ff7a-121"> [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9ff7a-121"> [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="9ff7a-122"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9ff7a-122"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9ff7a-123"> [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span><span class="sxs-lookup"><span data-stu-id="9ff7a-123"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span></span>
