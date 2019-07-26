---
title: O tipo da variável '<variablename>' não será inferido porque está associado a um campo em um escopo delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512717"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="be7de-102">O tipo da variável '\<VariableName > ' não será inferido porque está associado a um campo em um escopo delimitador</span><span class="sxs-lookup"><span data-stu-id="be7de-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="be7de-103">O tipo da variável '\<VariableName > ' não será inferido porque está associado a um campo em um escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="be7de-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="be7de-104">Altere o nome de '\<VariableName > ' ou use o nome totalmente qualificado (por exemplo, ' me. VariableName ' ou ' MyBase. VariableName ').</span><span class="sxs-lookup"><span data-stu-id="be7de-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="be7de-105">Uma variável de controle de loop em seu código tem o mesmo nome que um campo da classe ou outro escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="be7de-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="be7de-106">Como a variável de controle é usada sem `As` uma cláusula, ela é associada ao campo no escopo delimitador, e o compilador não cria uma nova variável para ela ou infere seu tipo.</span><span class="sxs-lookup"><span data-stu-id="be7de-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="be7de-107">No exemplo a seguir, `Index`, a variável de controle `For` na instrução é associada `Customer` ao `Index` campo na classe.</span><span class="sxs-lookup"><span data-stu-id="be7de-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="be7de-108">O compilador não cria uma nova variável para a variável `Index` de controle ou infere seu tipo.</span><span class="sxs-lookup"><span data-stu-id="be7de-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
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

<span data-ttu-id="be7de-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="be7de-109">By default, this message is a warning.</span></span> <span data-ttu-id="be7de-110">Para obter informações sobre como ocultar avisos ou como tratar avisos como erros, consulte Configurando [avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="be7de-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="be7de-111">**ID do erro:** BC42110</span><span class="sxs-lookup"><span data-stu-id="be7de-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="be7de-112">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="be7de-112">To address this warning</span></span>

- <span data-ttu-id="be7de-113">Torne a variável de controle de loop local alterando seu nome para um identificador que não seja também o nome de um campo da classe.</span><span class="sxs-lookup"><span data-stu-id="be7de-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="be7de-114">Esclareça que a variável de controle de loop é vinculada ao campo de classe `Me.` prefixando para o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="be7de-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="be7de-115">Em vez de depender da inferência de tipo local, `As` use uma cláusula para especificar um tipo para a variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="be7de-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="be7de-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be7de-116">Example</span></span>
 <span data-ttu-id="be7de-117">O código a seguir mostra o exemplo anterior com a primeira correção em vigor.</span><span class="sxs-lookup"><span data-stu-id="be7de-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="be7de-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be7de-118">See also</span></span>

- [<span data-ttu-id="be7de-119">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="be7de-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="be7de-120">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="be7de-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="be7de-121">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="be7de-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="be7de-122">Como: Consulte a instância atual de um objeto</span><span class="sxs-lookup"><span data-stu-id="be7de-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="be7de-123">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="be7de-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="be7de-124">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="be7de-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
