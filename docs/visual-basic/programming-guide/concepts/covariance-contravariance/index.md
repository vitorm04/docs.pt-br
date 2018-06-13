---
title: Covariância e contravariância (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 322cb452e0a3391812e58b68406657651f7a430f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644037"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="b4e0d-102">Covariância e contravariância (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-102">Covariance and Contravariance (Visual Basic)</span></span>
<span data-ttu-id="b4e0d-103">No Visual Basic, a covariância e a contravariância habilitam a conversão de referência implícita para tipos de matriz, tipos delegados e argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="b4e0d-104">A covariância preserva a compatibilidade de atribuição, e a contravariância reverte.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="b4e0d-105">O código a seguir demonstra a diferença entre a compatibilidade da atribuição, a covariância e a contravariância.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 <span data-ttu-id="b4e0d-106">A covariância para matrizes permite a conversão implícita de uma matriz de um tipo mais derivado para uma matriz de um tipo menos derivado.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="b4e0d-107">Mas essa operação não é fortemente tipada, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 <span data-ttu-id="b4e0d-108">O suporte de covariância e contravariância aos grupos de método permite a correspondência de assinaturas de método com tipos de delegados.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="b4e0d-109">Isso permite atribuir a delegados não apenas os métodos que têm correspondência de assinaturas, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="b4e0d-110">Para obter mais informações, consulte [Variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-110">For more information, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="b4e0d-111">O exemplo de código a seguir mostra o suporte da covariância e da contravariância para grupos de método.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 <span data-ttu-id="b4e0d-112">No .NET Framework 4 ou mais recente, o Visual Basic dá suporte à covariância e à contravariância em interfaces e delegados genéricos e permite a conversão implícita de parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-112">In .NET Framework 4 or later Visual Basic support covariance and contravariance in generic interfaces and delegates and allow for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="b4e0d-113">Para obter mais informações, consulte [Variação em interfaces genéricas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) e [Variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="b4e0d-114">O exemplo de código a seguir mostra a conversão de referência implícita para interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="b4e0d-115">Uma interface ou delegado genérico será chamado *variante* se seus parâmetros genéricos forem declarados covariantes ou contravariantes.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="b4e0d-116">O Visual Basic permite que você crie suas próprias interfaces variantes e delegados.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="b4e0d-117">Para obter mais informações, consulte [Criando interfaces genéricas variantes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) e [Variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b4e0d-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="b4e0d-118">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="b4e0d-118">Related Topics</span></span>  
  
|<span data-ttu-id="b4e0d-119">Título</span><span class="sxs-lookup"><span data-stu-id="b4e0d-119">Title</span></span>|<span data-ttu-id="b4e0d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4e0d-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b4e0d-121">Variação em interfaces genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-121">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="b4e0d-122">Discute a covariância e a contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="b4e0d-123">Criando interfaces genéricas variantes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="b4e0d-124">Mostra como criar interfaces variantes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="b4e0d-125">Usando variação em interfaces para coleções genéricas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="b4e0d-126">Mostra como o suporte de covariância e contravariância nas interfaces <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601> pode ajudar na reutilização do código.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="b4e0d-127">Variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-127">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="b4e0d-128">Discute a covariância e a contravariância em interfaces genéricas e não genéricas e fornece uma lista de interfaces genéricas variáveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="b4e0d-129">Usando variação em delegados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-129">Using Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="b4e0d-130">Mostra como usar o suporte de covariância e contravariância em delegados não genéricos para corresponder às assinaturas de método com tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="b4e0d-131">Usando variação para delegados genéricos Func e Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e0d-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="b4e0d-132">Mostra como o suporte de covariância e contravariância nos delegados `Func` e `Action` pode ajudar na reutilização do código.</span><span class="sxs-lookup"><span data-stu-id="b4e0d-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
