---
title: Tipo de dados de objeto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835564"
---
# <a name="object-data-type"></a><span data-ttu-id="02c65-102">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="02c65-102">Object Data Type</span></span>
<span data-ttu-id="02c65-103">Contém os endereços que se referem a objetos.</span><span class="sxs-lookup"><span data-stu-id="02c65-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="02c65-104">Você pode atribuir qualquer tipo de referência (cadeia de caracteres, matriz, classe ou interface) para um `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="02c65-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="02c65-105">Uma `Object` variável também pode consultar dados de qualquer tipo de valor (numérico, `Boolean`, `Char`, `Date`, estrutura, ou enumeração).</span><span class="sxs-lookup"><span data-stu-id="02c65-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02c65-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="02c65-106">Remarks</span></span>  
 <span data-ttu-id="02c65-107">O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância do objeto que seu aplicativo reconheça.</span><span class="sxs-lookup"><span data-stu-id="02c65-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="02c65-108">Use `Object` quando você não souber em tempo de compilação qual tipo de dados a variável pode apontar.</span><span class="sxs-lookup"><span data-stu-id="02c65-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="02c65-109">O valor padrão de `Object` é `Nothing` (uma referência nula).</span><span class="sxs-lookup"><span data-stu-id="02c65-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="02c65-110">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="02c65-110">Data Types</span></span>  
 <span data-ttu-id="02c65-111">Você pode atribuir uma variável, constante ou expressão de qualquer tipo de dados para um `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="02c65-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="02c65-112">Para determinar o tipo de dados uma `Object` variável atualmente se refere, você pode usar o <xref:System.Type.GetTypeCode%2A> método o <xref:System.Type?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="02c65-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="02c65-113">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="02c65-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="02c65-114">O `Object` tipo de dados é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="02c65-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="02c65-115">No entanto, o Visual Basic trata um `Object` variável como um tipo de valor quando ele se refere a dados de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="02c65-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="02c65-116">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="02c65-116">Storage</span></span>  
 <span data-ttu-id="02c65-117">Qualquer tipo de dados que ele se refere, um `Object` variável não contém o valor dos dados em si, mas em vez disso, um ponteiro para o valor.</span><span class="sxs-lookup"><span data-stu-id="02c65-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="02c65-118">Ela sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento de dados que representa o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="02c65-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="02c65-119">Por causa do código que usa o ponteiro para localizar os dados, `Object` variáveis mantendo os tipos de valor são um pouco mais lentas do que acessar explicitamente as variáveis digitadas.</span><span class="sxs-lookup"><span data-stu-id="02c65-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="02c65-120">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="02c65-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="02c65-121">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="02c65-121">**Interop Considerations.**</span></span> <span data-ttu-id="02c65-122">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que os tipos de ponteiro em outros ambientes não são compatíveis com o Visual Basic `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="02c65-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="02c65-123">**Desempenho.**</span><span class="sxs-lookup"><span data-stu-id="02c65-123">**Performance.**</span></span> <span data-ttu-id="02c65-124">Uma variável declarada com o `Object` tipo é flexível o suficiente para conter uma referência a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="02c65-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="02c65-125">No entanto, quando você invoca um método ou propriedade nesse tipo de variável, você sempre provoca *ligação tardia* (no tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="02c65-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="02c65-126">Para forçar *vinculação inicial* (no tempo de compilação) e um melhor desempenho, declare a variável com um nome de classe específica ou convertê-lo para o tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="02c65-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="02c65-127">Quando você declara uma variável de objeto, tente usar um tipo de classe específica, por exemplo <xref:System.OperatingSystem>, em vez do generalizado `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="02c65-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="02c65-128">Você também deve usar a classe mais específica disponível, como <xref:System.Windows.Forms.TextBox> em vez de <xref:System.Windows.Forms.Control>, de modo que você pode acessar suas propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="02c65-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="02c65-129">Normalmente, você pode usar o **Classes** lista o **Pesquisador de objetos** para localizar nomes de classe disponíveis.</span><span class="sxs-lookup"><span data-stu-id="02c65-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="02c65-130">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="02c65-130">**Widening.**</span></span> <span data-ttu-id="02c65-131">Todos os tipos de dados e todos os tipos de referência são ampliados com o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="02c65-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="02c65-132">Isso significa que você pode converter qualquer tipo de `Object` sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="02c65-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="02c65-133">No entanto, se você converter entre tipos de valor e `Object`, Visual Basic executa operações denominadas *boxing* e *unboxing*, que tornam a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="02c65-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="02c65-134">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="02c65-134">**Type Characters.**</span></span> <span data-ttu-id="02c65-135">`Object` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="02c65-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="02c65-136">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="02c65-136">**Framework Type.**</span></span> <span data-ttu-id="02c65-137">O tipo correspondente no .NET Framework é o <xref:System.Object?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="02c65-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02c65-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02c65-138">Example</span></span>  
 <span data-ttu-id="02c65-139">O exemplo a seguir ilustra um `Object` variável que aponta para uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="02c65-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="02c65-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02c65-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="02c65-141">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="02c65-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="02c65-142">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="02c65-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="02c65-143">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="02c65-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="02c65-144">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="02c65-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="02c65-145">Como: Determinar se dois objetos estão relacionados</span><span class="sxs-lookup"><span data-stu-id="02c65-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="02c65-146">Como: Determinar se dois objetos são idênticos</span><span class="sxs-lookup"><span data-stu-id="02c65-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
