---
title: "Passando parâmetros de tipo de valor (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: 17
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
ms.openlocfilehash: a3377630fc4294831f6b9d66a69377aa42d973f1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="passing-value-type-parameters-c-programming-guide"></a><span data-ttu-id="c859a-102">Passando parâmetros de tipo de valor (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c859a-102">Passing Value-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="c859a-103">Uma variável de [tipo de valor](../../../csharp/language-reference/keywords/value-types.md) contém seus dados diretamente, o que não acontece com uma variável de [tipo de referência](../../../csharp/language-reference/keywords/reference-types.md), que contém uma referência a seus dados.</span><span class="sxs-lookup"><span data-stu-id="c859a-103">A [value-type](../../../csharp/language-reference/keywords/value-types.md) variable contains its data directly as opposed to a [reference-type](../../../csharp/language-reference/keywords/reference-types.md) variable, which contains a reference to its data.</span></span> <span data-ttu-id="c859a-104">Passar uma variável de tipo de valor para um método por valor significa passar uma cópia da variável para o método.</span><span class="sxs-lookup"><span data-stu-id="c859a-104">Passing a value-type variable to a method by value means passing a copy of the variable to the method.</span></span> <span data-ttu-id="c859a-105">Quaisquer alterações no parâmetro que ocorrem dentro do método não afetam os dados originais armazenados na variável de argumento.</span><span class="sxs-lookup"><span data-stu-id="c859a-105">Any changes to the parameter that take place inside the method have no affect on the original data stored in the argument variable.</span></span> <span data-ttu-id="c859a-106">Se desejar que o método chamado altere o valor do parâmetro, é necessário passá-lo por referência, usando a palavra-chave [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="c859a-106">If you want the called method to change the value of the parameter, you must pass it by reference, using the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) keyword.</span></span> <span data-ttu-id="c859a-107">Para simplificar, os exemplos a seguir usam `ref`.</span><span class="sxs-lookup"><span data-stu-id="c859a-107">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-value-types-by-value"></a><span data-ttu-id="c859a-108">Passando tipos de valor por valor</span><span class="sxs-lookup"><span data-stu-id="c859a-108">Passing Value Types by Value</span></span>  
 <span data-ttu-id="c859a-109">O exemplo a seguir demonstra a passagem de parâmetros de tipo de valor por valor.</span><span class="sxs-lookup"><span data-stu-id="c859a-109">The following example demonstrates passing value-type parameters by value.</span></span> <span data-ttu-id="c859a-110">A variável `n` é passada por valor para o método `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="c859a-110">The variable `n` is passed by value to the method `SquareIt`.</span></span> <span data-ttu-id="c859a-111">Quaisquer alterações que ocorrem dentro do método não afetam o valor original da variável.</span><span class="sxs-lookup"><span data-stu-id="c859a-111">Any changes that take place inside the method have no affect on the original value of the variable.</span></span>  
  
 <span data-ttu-id="c859a-112">[!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c859a-112">[!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="c859a-113">A variável `n` é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c859a-113">The variable `n` is a value type.</span></span> <span data-ttu-id="c859a-114">Ela contém seus dados, o valor `5`.</span><span class="sxs-lookup"><span data-stu-id="c859a-114">It contains its data, the value `5`.</span></span> <span data-ttu-id="c859a-115">Quando `SquareIt` é invocado, o conteúdo de `n` é copiado para o parâmetro `x`, que é elevado ao quadrado dentro do método.</span><span class="sxs-lookup"><span data-stu-id="c859a-115">When `SquareIt` is invoked, the contents of `n` are copied into the parameter `x`, which is squared inside the method.</span></span> <span data-ttu-id="c859a-116">No entanto, em `Main`, o valor de `n` é o mesmo depois de chamar o método `SquareIt` como era antes.</span><span class="sxs-lookup"><span data-stu-id="c859a-116">In `Main`, however, the value of `n` is the same after calling the `SquareIt` method as it was before.</span></span> <span data-ttu-id="c859a-117">A alteração que ocorre dentro do método afeta apenas a variável local `x`.</span><span class="sxs-lookup"><span data-stu-id="c859a-117">The change that takes place inside the method only affects the local variable `x`.</span></span>  
  
## <a name="passing-value-types-by-reference"></a><span data-ttu-id="c859a-118">Passando tipos de valor por referência</span><span class="sxs-lookup"><span data-stu-id="c859a-118">Passing Value Types by Reference</span></span>  
 <span data-ttu-id="c859a-119">O exemplo a seguir é o mesmo que o exemplo anterior, exceto que o argumento é passado como um parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="c859a-119">The following example is the same as the previous example, except that the argument is passed as a `ref` parameter.</span></span> <span data-ttu-id="c859a-120">O valor do argumento subjacente, `n`, é alterado quando `x` é alterado no método.</span><span class="sxs-lookup"><span data-stu-id="c859a-120">The value of the underlying argument, `n`, is changed when `x` is changed in the method.</span></span>  
  
 <span data-ttu-id="c859a-121">[!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c859a-121">[!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]</span></span>  
  
 <span data-ttu-id="c859a-122">Neste exemplo, não é o valor de `n` que é passado; em vez disso, é passada uma referência a `n`.</span><span class="sxs-lookup"><span data-stu-id="c859a-122">In this example, it is not the value of `n` that is passed; rather, a reference to `n` is passed.</span></span> <span data-ttu-id="c859a-123">O parâmetro `x` não é um [int](../../../csharp/language-reference/keywords/int.md); é uma referência a um `int`, nesse caso, uma referência a `n`.</span><span class="sxs-lookup"><span data-stu-id="c859a-123">The parameter `x` is not an [int](../../../csharp/language-reference/keywords/int.md); it is a reference to an `int`, in this case, a reference to `n`.</span></span> <span data-ttu-id="c859a-124">Portanto, quando `x` é elevado ao quadrado dentro do método, o que é realmente é elevado ao quadrado é aquilo a que `x` se refere, `n`.</span><span class="sxs-lookup"><span data-stu-id="c859a-124">Therefore, when `x` is squared inside the method, what actually is squared is what `x` refers to, `n`.</span></span>  
  
## <a name="swapping-value-types"></a><span data-ttu-id="c859a-125">Trocar valores de tipo</span><span class="sxs-lookup"><span data-stu-id="c859a-125">Swapping Value Types</span></span>  
 <span data-ttu-id="c859a-126">Um exemplo comum de alteração dos valores de argumentos é um método de troca, em que você passa duas variáveis para o método e o método troca seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c859a-126">A common example of changing the values of arguments is a swap method, where you pass two variables to the method, and the method swaps their contents.</span></span> <span data-ttu-id="c859a-127">É necessário passar os argumentos para o método de troca por referência.</span><span class="sxs-lookup"><span data-stu-id="c859a-127">You must pass the arguments to the swap method by reference.</span></span> <span data-ttu-id="c859a-128">Caso contrário, você troca cópias locais dos parâmetros dentro do método e nenhuma alteração ocorre no método de chamada.</span><span class="sxs-lookup"><span data-stu-id="c859a-128">Otherwise, you swap local copies of the parameters inside the method, and no change occurs in the calling method.</span></span> <span data-ttu-id="c859a-129">O exemplo a seguir troca valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="c859a-129">The following example swaps integer values.</span></span>  
  
 <span data-ttu-id="c859a-130">[!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c859a-130">[!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]</span></span>  
  
 <span data-ttu-id="c859a-131">Quando você chama o método `SwapByRef`, use a palavra-chave `ref` na chamada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c859a-131">When you call the `SwapByRef` method, use the `ref` keyword in the call, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c859a-132">[!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c859a-132">[!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c859a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c859a-133">See Also</span></span>  
 <span data-ttu-id="c859a-134">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c859a-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c859a-135">[Passando Parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="c859a-135">[Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
 [<span data-ttu-id="c859a-136">Passando parâmetros de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="c859a-136">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)

