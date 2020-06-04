---
title: Como determinar a que tipo uma variável de objeto se refere
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: d3224000f5958a8619e38c4d2f6dc5dbb275ad45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410484"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="7562a-102">Como determinar a que tipo uma variável de objeto se refere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7562a-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="7562a-103">Uma variável de objeto contém um ponteiro para dados que são armazenados em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="7562a-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="7562a-104">O tipo desses dados pode ser alterado durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7562a-104">The type of that data can change during run time.</span></span> <span data-ttu-id="7562a-105">A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A> método para determinar o tipo de tempo de execução atual ou o [operador typeof](../../../language-reference/operators/typeof-operator.md) para descobrir se o tipo de tempo de execução atual é compatível com um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7562a-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="7562a-106">Para determinar o tipo exato que uma variável de objeto atualmente faz referência</span><span class="sxs-lookup"><span data-stu-id="7562a-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="7562a-107">Na variável de objeto, chame o <xref:System.Object.GetType%2A> método para recuperar um <xref:System.Type?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="7562a-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="7562a-108">Na <xref:System.Type?displayProperty=nameWithType> classe, chame o método compartilhado <xref:System.Type.GetTypeCode%2A> para recuperar o <xref:System.TypeCode> valor de enumeração para o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="7562a-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="7562a-109">Você pode testar o <xref:System.TypeCode> valor de enumeração em relação a qualquer membro de enumeração que seja de interesse, como `Double` .</span><span class="sxs-lookup"><span data-stu-id="7562a-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="7562a-110">Para determinar se o tipo de uma variável de objeto é compatível com um tipo especificado</span><span class="sxs-lookup"><span data-stu-id="7562a-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="7562a-111">Use o `TypeOf` operador em combinação com o [operador is](../../../language-reference/operators/is-operator.md) para testar o objeto com uma `TypeOf` expressão.... `Is`</span><span class="sxs-lookup"><span data-stu-id="7562a-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="7562a-112">A `TypeOf` expressão... `Is` retorna `True` se o tipo de tempo de execução do objeto for compatível com o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7562a-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="7562a-113">O critério de compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="7562a-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="7562a-114">Em geral, os tipos são compatíveis se o objeto for do mesmo tipo que, herda de ou implementa o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7562a-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="7562a-115">Para obter mais informações, consulte [operador typeof](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7562a-115">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="7562a-116">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="7562a-116">Compile the code</span></span>

<span data-ttu-id="7562a-117">Observe que o tipo especificado não pode ser uma variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="7562a-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="7562a-118">Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="7562a-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="7562a-119">Isso inclui tipos intrínsecos, como `Integer` e `String` .</span><span class="sxs-lookup"><span data-stu-id="7562a-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7562a-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="7562a-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="7562a-121">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="7562a-121">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="7562a-122">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="7562a-122">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="7562a-123">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="7562a-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
