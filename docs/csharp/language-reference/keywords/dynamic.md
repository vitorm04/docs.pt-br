---
title: "dynamic (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- dynamic_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b68a6ef4dc3dda01638b9bb84db58ba77214f490
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="dynamic-c-reference"></a><span data-ttu-id="51c2c-102">dynamic (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="51c2c-102">dynamic (C# Reference)</span></span>
<span data-ttu-id="51c2c-103">O tipo `dynamic` habilita operações nas quais ele ocorre para ignorar a verificação de tipo em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="51c2c-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="51c2c-104">Em vez disso, essas operações são resolvidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="51c2c-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="51c2c-105">O tipo `dynamic` simplifica o acesso a APIs COM, como as APIs de Automação do Office e também às APIs dinâmicas, como bibliotecas do IronPython e ao Modelo de Objeto do Documento (DOM) do HTML.</span><span class="sxs-lookup"><span data-stu-id="51c2c-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="51c2c-106">O tipo `dynamic` se comporta como o tipo `object` na maioria das circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="51c2c-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="51c2c-107">No entanto, as operações que contêm expressões do tipo `dynamic` não são resolvidas ou verificadas pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="51c2c-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="51c2c-108">O compilador junta as informações sobre a operação em pacotes e, posteriormente, essas informações são usadas para avaliar a operação em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="51c2c-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="51c2c-109">Como parte do processo, as variáveis do tipo `dynamic` são compiladas em variáveis do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="51c2c-110">Portanto, o tipo `dynamic` existe somente em tempo de compilação e não em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="51c2c-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>  
  
 <span data-ttu-id="51c2c-111">O exemplo a seguir compara uma variável do tipo `dynamic` a uma variável do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="51c2c-112">Para verificar o tipo de cada variável no tempo de compilação, coloque o ponteiro do mouse sobre `dyn` ou `obj` nas instruções `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="51c2c-113">O IntelliSense mostra **dinâmico** para `dyn` e **objeto** para `obj`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>  
  
 <span data-ttu-id="51c2c-114">[!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="51c2c-114">[!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]</span></span>  
  
 <span data-ttu-id="51c2c-115">As instruções `WriteLine` exibem os tipos de tempo de execução de `dyn` e `obj`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-115">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="51c2c-116">Nesse ponto, ambos têm o mesmo tipo, inteiro.</span><span class="sxs-lookup"><span data-stu-id="51c2c-116">At that point, both have the same type, integer.</span></span> <span data-ttu-id="51c2c-117">A saída a seguir será produzida:</span><span class="sxs-lookup"><span data-stu-id="51c2c-117">The following output is produced:</span></span>  
  
 `System.Int32`  
  
 `System.Int32`  
  
 <span data-ttu-id="51c2c-118">Para ver a diferença entre `dyn` e `obj` em tempo de compilação, adicione as duas linhas a seguir entre as declarações e as instruções `WriteLine` no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="51c2c-118">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 <span data-ttu-id="51c2c-119">Um erro de compilador será relatado em virtude da tentativa de adição de um inteiro e um objeto à expressão `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-119">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="51c2c-120">No entanto, nenhum erro será relatado para `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-120">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="51c2c-121">A expressão contém `dyn` não é verificada em tempo de compilação, pois o tipo de `dyn` é `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="51c2c-121">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>  
  
## <a name="context"></a><span data-ttu-id="51c2c-122">Contexto</span><span class="sxs-lookup"><span data-stu-id="51c2c-122">Context</span></span>  
 <span data-ttu-id="51c2c-123">A palavra-chave `dynamic` pode aparecer diretamente ou como um componente de um tipo construído nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="51c2c-123">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>  
  
-   <span data-ttu-id="51c2c-124">Em declarações, como o tipo de uma propriedade, campo, indexador, parâmetro, valor retornado, variável local ou restrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="51c2c-124">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="51c2c-125">A definição de classe a seguir usa `dynamic` em várias declarações diferentes.</span><span class="sxs-lookup"><span data-stu-id="51c2c-125">The following class definition uses `dynamic` in several different declarations.</span></span>  
  
     <span data-ttu-id="51c2c-126">[!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="51c2c-126">[!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]</span></span>  
  
-   <span data-ttu-id="51c2c-127">Em conversões explícitas de tipo, como o tipo de destino de uma conversão.</span><span class="sxs-lookup"><span data-stu-id="51c2c-127">In explicit type conversions, as the target type of a conversion.</span></span>  
  
     <span data-ttu-id="51c2c-128">[!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="51c2c-128">[!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]</span></span>  
  
-   <span data-ttu-id="51c2c-129">Em qualquer contexto em que tipos sirvam como valores, como no lado direito de um operador `is` ou um operador `as` ou como o argumento para `typeof` como parte de um tipo construído.</span><span class="sxs-lookup"><span data-stu-id="51c2c-129">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="51c2c-130">Por exemplo, `dynamic` pode ser usado nas expressões a seguir.</span><span class="sxs-lookup"><span data-stu-id="51c2c-130">For example, `dynamic` can be used in the following expressions.</span></span>  
  
     <span data-ttu-id="51c2c-131">[!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="51c2c-131">[!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="51c2c-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51c2c-132">Example</span></span>  
 <span data-ttu-id="51c2c-133">O exemplo a seguir usa `dynamic` em várias declarações.</span><span class="sxs-lookup"><span data-stu-id="51c2c-133">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="51c2c-134">O método `Main` também compara a verificação de tipo em tempo de compilação com a verificação de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="51c2c-134">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>  
  
 <span data-ttu-id="51c2c-135">[!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="51c2c-135">[!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]</span></span>  
  
 <span data-ttu-id="51c2c-136">Para obter mais informações e exemplos, consulte [Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="51c2c-136">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c2c-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51c2c-137">See Also</span></span>  
 <span data-ttu-id="51c2c-138"><xref:System.Dynamic.ExpandoObject?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="51c2c-138"><xref:System.Dynamic.ExpandoObject?displayProperty=fullName></span></span>   
 <span data-ttu-id="51c2c-139"><xref:System.Dynamic.DynamicObject?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="51c2c-139"><xref:System.Dynamic.DynamicObject?displayProperty=fullName></span></span>   
 <span data-ttu-id="51c2c-140">[Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="51c2c-140">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="51c2c-141">[object](../../../csharp/language-reference/keywords/object.md) </span><span class="sxs-lookup"><span data-stu-id="51c2c-141">[object](../../../csharp/language-reference/keywords/object.md) </span></span>  
 <span data-ttu-id="51c2c-142">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="51c2c-142">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="51c2c-143">[as](../../../csharp/language-reference/keywords/as.md) </span><span class="sxs-lookup"><span data-stu-id="51c2c-143">[as](../../../csharp/language-reference/keywords/as.md) </span></span>  
 <span data-ttu-id="51c2c-144">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span><span class="sxs-lookup"><span data-stu-id="51c2c-144">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span></span>  
 <span data-ttu-id="51c2c-145">[Como Executar a Conversão com Segurança Usando Operadores as e is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md) </span><span class="sxs-lookup"><span data-stu-id="51c2c-145">[How to: Safely Cast by Using as and is Operators](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md) </span></span>  
 [<span data-ttu-id="51c2c-146">Passo a passo: Criando e usando objetos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="51c2c-146">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)

