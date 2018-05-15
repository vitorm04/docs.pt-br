---
title: O tipo de variável &#39; &lt;variablename&gt; &#39; não será inferido porque está associado a um campo em um escopo delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="633a8-102">O tipo de variável &#39; &lt;variablename&gt; &#39; não será inferido porque está associado a um campo em um escopo delimitador</span><span class="sxs-lookup"><span data-stu-id="633a8-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="633a8-103">O tipo de variável '\<variablename >' não será inferido porque está associado a um campo em um escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="633a8-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="633a8-104">Altere o nome de '\<variablename >', ou use o nome totalmente qualificado (por exemplo, 'Me.variablename' ou 'MyBase.variablename').</span><span class="sxs-lookup"><span data-stu-id="633a8-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="633a8-105">Uma variável de controle de loop no seu código tem o mesmo nome como um campo da classe ou a outro escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="633a8-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="633a8-106">Como a variável de controle é usada sem um `As` cláusula, está associado ao campo no escopo delimitador e o compilador não cria uma nova variável para ele ou inferir o tipo.</span><span class="sxs-lookup"><span data-stu-id="633a8-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="633a8-107">No exemplo a seguir, `Index`, a variável de controle no `For` instrução, está associado ao `Index` campo o `Customer` classe.</span><span class="sxs-lookup"><span data-stu-id="633a8-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="633a8-108">O compilador não cria uma nova variável para a variável de controle `Index` ou inferir o tipo.</span><span class="sxs-lookup"><span data-stu-id="633a8-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="633a8-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="633a8-109">By default, this message is a warning.</span></span> <span data-ttu-id="633a8-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="633a8-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="633a8-111">**ID do erro:** BC42110</span><span class="sxs-lookup"><span data-stu-id="633a8-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="633a8-112">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="633a8-112">To address this warning</span></span>  
  
-   <span data-ttu-id="633a8-113">Verifique a variável de controle de loop local alterando seu nome para um identificador que também não é o nome de um campo da classe.</span><span class="sxs-lookup"><span data-stu-id="633a8-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="633a8-114">Esclarecer que a variável de controle de loop estará associado ao campo de classe, prefixando `Me.` para o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="633a8-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="633a8-115">Em vez de depender de inferência de tipo local, use um `As` cláusula para especificar um tipo para a variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="633a8-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="633a8-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="633a8-116">Example</span></span>  
 <span data-ttu-id="633a8-117">O código a seguir mostra o exemplo anterior, com a primeira correção em vigor.</span><span class="sxs-lookup"><span data-stu-id="633a8-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="633a8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="633a8-118">See Also</span></span>  
 [<span data-ttu-id="633a8-119">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="633a8-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="633a8-120">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="633a8-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="633a8-121">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="633a8-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="633a8-122">Como fazer referência à instância atual de um objeto</span><span class="sxs-lookup"><span data-stu-id="633a8-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="633a8-123">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="633a8-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="633a8-124">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="633a8-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
