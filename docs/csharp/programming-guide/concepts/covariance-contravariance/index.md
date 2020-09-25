---
title: Covariância e contravariância (C#)
description: Saiba mais sobre covariância e contravariância e como eles afetam a compatibilidade de atribuição. Consulte um exemplo de código que demonstra as diferenças entre eles.
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: d0309ec1bb3161412433e1b44e8e35410911b38d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176325"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="9d3cb-104">Covariância e contravariância (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-104">Covariance and Contravariance (C#)</span></span>

<span data-ttu-id="9d3cb-105">No C#, a covariância e a contravariância habilitam a conversão de referência implícita para tipos de matriz, tipos de delegados e argumentos de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-105">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="9d3cb-106">A covariância preserva a compatibilidade de atribuição, e a contravariância reverte.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-106">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="9d3cb-107">O código a seguir demonstra a diferença entre a compatibilidade da atribuição, a covariância e a contravariância.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-107">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="9d3cb-108">A covariância para matrizes permite a conversão implícita de uma matriz de um tipo mais derivado para uma matriz de um tipo menos derivado.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-108">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="9d3cb-109">Mas essa operação não é fortemente tipada, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-109">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="9d3cb-110">O suporte de covariância e contravariância aos grupos de método permite a correspondência de assinaturas de método com tipos de delegados.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-110">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="9d3cb-111">Isso permite atribuir a delegados não apenas os métodos que têm correspondência de assinaturas, mas também métodos que retornam tipos mais derivados (covariância) ou que aceitam parâmetros que têm tipos menos derivados (contravariância) do que o especificado pelo tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-111">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="9d3cb-112">Para obter mais informações, consulte [Variância em delegados (C#)](./variance-in-delegates.md) e [Usando variância em delegados (C#)](./using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9d3cb-112">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="9d3cb-113">O exemplo de código a seguir mostra o suporte da covariância e da contravariância para grupos de método.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-113">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="9d3cb-114">No .NET Framework 4 e versões posteriores, o C# dá suporte à covariância e contravariância em interfaces e delegados genéricos e permite a conversão implícita de parâmetros de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-114">In .NET Framework 4 and later versions, C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="9d3cb-115">Para obter mais informações, consulte [Variação em interfaces genéricas (C#)](./variance-in-generic-interfaces.md) e [Variação em delegados (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9d3cb-115">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="9d3cb-116">O exemplo de código a seguir mostra a conversão de referência implícita para interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-116">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="9d3cb-117">Uma interface ou delegado genérico será chamado *variante* se seus parâmetros genéricos forem declarados covariantes ou contravariantes.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-117">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="9d3cb-118">O C# permite que você crie suas próprias interfaces variantes e delegados.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-118">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="9d3cb-119">Para obter mais informações, consulte [Criando interfaces genéricas variantes (C#)](./creating-variant-generic-interfaces.md) e [Variação em delegados (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9d3cb-119">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="9d3cb-120">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="9d3cb-120">Related Topics</span></span>  
  
|<span data-ttu-id="9d3cb-121">Título</span><span class="sxs-lookup"><span data-stu-id="9d3cb-121">Title</span></span>|<span data-ttu-id="9d3cb-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d3cb-122">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9d3cb-123">Variância em interfaces genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-123">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="9d3cb-124">Discute covariância e contravariância em interfaces genéricas e fornece uma lista de interfaces genéricas variadas no .NET.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-124">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in .NET.</span></span>|  
|[<span data-ttu-id="9d3cb-125">Criando interfaces genéricas variáveis (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-125">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="9d3cb-126">Mostra como criar interfaces variantes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-126">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="9d3cb-127">Usando variação em interfaces para Coleções Genéricas (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-127">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="9d3cb-128">Mostra como o suporte de covariância e contravariância nas interfaces <xref:System.Collections.Generic.IEnumerable%601> e <xref:System.IComparable%601> pode ajudar na reutilização do código.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-128">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="9d3cb-129">Variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-129">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="9d3cb-130">Discute covariância e contravariância em delegados genéricos e não genéricos e fornece uma lista de delegados genéricos de variantes no .NET.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-130">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in .NET.</span></span>|  
|[<span data-ttu-id="9d3cb-131">Usando variação em delegados (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-131">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="9d3cb-132">Mostra como usar o suporte de covariância e contravariância em delegados não genéricos para corresponder às assinaturas de método com tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-132">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="9d3cb-133">Usando variação para delegados genéricos Func e Action (C#)</span><span class="sxs-lookup"><span data-stu-id="9d3cb-133">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="9d3cb-134">Mostra como o suporte de covariância e contravariância nos delegados `Func` e `Action` pode ajudar na reutilização do código.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-134">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
