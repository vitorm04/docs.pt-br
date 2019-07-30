---
title: 'Como: Determinar a qual tipo uma variável de objeto se refere (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626573"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="2709d-102">Como: Determinar a qual tipo uma variável de objeto se refere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2709d-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="2709d-103">Uma variável de objeto contém um ponteiro para dados que são armazenados em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="2709d-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="2709d-104">O tipo desses dados pode ser alterado durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2709d-104">The type of that data can change during run time.</span></span> <span data-ttu-id="2709d-105">A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A> método para determinar o tipo de tempo de execução atual ou o [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se o tipo de tempo de execução atual é compatível com um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="2709d-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="2709d-106">Para determinar o tipo exato que uma variável de objeto atualmente faz referência</span><span class="sxs-lookup"><span data-stu-id="2709d-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="2709d-107">Na variável de objeto, chame o <xref:System.Object.GetType%2A> método para recuperar um <xref:System.Type?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="2709d-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="2709d-108">Na classe, chame o método <xref:System.Type.GetTypeCode%2A> compartilhado para recuperar o <xref:System.TypeCode> valor de enumeração para o tipo do objeto. <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2709d-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="2709d-109">Você pode testar o <xref:System.TypeCode> valor de enumeração em relação a qualquer membro de enumeração que `Double`seja de interesse, como.</span><span class="sxs-lookup"><span data-stu-id="2709d-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="2709d-110">Para determinar se o tipo de uma variável de objeto é compatível com um tipo especificado</span><span class="sxs-lookup"><span data-stu-id="2709d-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="2709d-111">Use o `TypeOf` operador em combinação com o [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com um `TypeOf`... `Is` expressão.</span><span class="sxs-lookup"><span data-stu-id="2709d-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="2709d-112">A `TypeOf`... `Is` expressão retorna`True` se o tipo de tempo de execução do objeto for compatível com o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="2709d-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="2709d-113">O critério de compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="2709d-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="2709d-114">Em geral, os tipos são compatíveis se o objeto for do mesmo tipo que, herda de ou implementa o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="2709d-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="2709d-115">Para obter mais informações, consulte [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2709d-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="2709d-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2709d-116">Compiling the Code</span></span>

<span data-ttu-id="2709d-117">Observe que o tipo especificado não pode ser uma variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="2709d-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="2709d-118">Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="2709d-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="2709d-119">Isso inclui tipos intrínsecos, `Integer` como `String`e.</span><span class="sxs-lookup"><span data-stu-id="2709d-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2709d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2709d-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="2709d-121">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="2709d-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="2709d-122">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="2709d-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="2709d-123">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="2709d-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
