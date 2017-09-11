---
title: "O tipo da variável &quot;&lt;variablename&gt;&quot; não será inferido porque está associado a um campo em um escopo delimitador | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 0f954fda84c9fd1a4af5315be2329de117e6d169
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="87c6f-102">O tipo da variável '&lt;variablename&gt;' não será inferido porque está associado a um campo em um escopo delimitador</span><span class="sxs-lookup"><span data-stu-id="87c6f-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="87c6f-103">O tipo da variável '\<NOMEDAVARIÁVEL >' não será inferido porque está associado a um campo em um escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="87c6f-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="87c6f-104">Altere o nome de '\<NOMEDAVARIÁVEL >', ou use o nome totalmente qualificado (por exemplo, 'Me.variablename' ou 'MyBase.variablename').</span><span class="sxs-lookup"><span data-stu-id="87c6f-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="87c6f-105">Uma variável de controle de loop em seu código tem o mesmo nome como um campo de classe ou em outro escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="87c6f-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="87c6f-106">Como a variável de controle é usada sem um `As` cláusula, ele é associado ao campo no escopo delimitador e o compilador não cria uma nova variável para ele ou inferir o tipo.</span><span class="sxs-lookup"><span data-stu-id="87c6f-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="87c6f-107">No exemplo a seguir, `Index`, a variável de controle no `For` instrução, está vinculado ao `Index` campo o `Customer` classe.</span><span class="sxs-lookup"><span data-stu-id="87c6f-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="87c6f-108">O compilador não cria uma nova variável para a variável de controle `Index` ou inferir o tipo.</span><span class="sxs-lookup"><span data-stu-id="87c6f-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="87c6f-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="87c6f-109">By default, this message is a warning.</span></span> <span data-ttu-id="87c6f-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="87c6f-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="87c6f-111">**ID do erro:** BC42110</span><span class="sxs-lookup"><span data-stu-id="87c6f-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="87c6f-112">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="87c6f-112">To address this warning</span></span>  
  
-   <span data-ttu-id="87c6f-113">Verifique a variável de controle de loop local alterando seu nome para um identificador que também não é o nome de um campo da classe.</span><span class="sxs-lookup"><span data-stu-id="87c6f-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="87c6f-114">Esclarecer o que a variável de controle de loop associa ao campo classe prefixando `Me.` para o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="87c6f-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="87c6f-115">Em vez de contar com a inferência de tipo local, use um `As` cláusula para especificar um tipo para a variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="87c6f-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="87c6f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87c6f-116">Example</span></span>  
 <span data-ttu-id="87c6f-117">O código a seguir mostra o exemplo anterior com a primeira correção no lugar.</span><span class="sxs-lookup"><span data-stu-id="87c6f-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="87c6f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87c6f-118">See Also</span></span>  
 <span data-ttu-id="87c6f-119">[Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="87c6f-119">[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="87c6f-120"> [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="87c6f-120"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="87c6f-121"> [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="87c6f-121"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="87c6f-122"> [Como: fazer referência à instância atual de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="87c6f-122"> [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="87c6f-123"> [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="87c6f-123"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="87c6f-124"> [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="87c6f-124"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

