---
title: "Propriedades (Guia de Programação em C#)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.properties
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
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
ms.openlocfilehash: 127299a617cacee15f87964a12bb3877a2586204
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="properties-c-programming-guide"></a><span data-ttu-id="62614-102">Propriedades (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="62614-102">Properties (C# Programming Guide)</span></span>

<span data-ttu-id="62614-103">Uma propriedade é um membro que oferece um mecanismo flexível para ler, gravar ou calcular o valor de um campo particular.</span><span class="sxs-lookup"><span data-stu-id="62614-103">A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.</span></span> <span data-ttu-id="62614-104">As propriedades podem ser usadas como se fossem membros de dados públicos, mas na verdade elas são métodos realmente especiais chamados *acessadores*.</span><span class="sxs-lookup"><span data-stu-id="62614-104">Properties can be used as if they are public data members, but they are actually special methods called *accessors*.</span></span> <span data-ttu-id="62614-105">Isso permite que os dados sejam acessados facilmente e ainda ajuda a promover a segurança e a flexibilidade dos métodos.</span><span class="sxs-lookup"><span data-stu-id="62614-105">This enables data to be accessed easily and still helps promote the safety and flexibility of methods.</span></span>  

## <a name="properties-overview"></a><span data-ttu-id="62614-106">Visão geral das propriedades</span><span class="sxs-lookup"><span data-stu-id="62614-106">Properties overview</span></span>  
  
- <span data-ttu-id="62614-107">As propriedades permitem que uma classe exponha uma forma pública de obter e definir valores, enquanto oculta o código de implementação ou de verificação.</span><span class="sxs-lookup"><span data-stu-id="62614-107">Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.</span></span>  
  
- <span data-ttu-id="62614-108">Um acessador de propriedade [get](../../../csharp/language-reference/keywords/get.md) é usado para retornar o valor da propriedade e um acessador de propriedade [set](../../../csharp/language-reference/keywords/set.md) é usado para atribuir um novo valor.</span><span class="sxs-lookup"><span data-stu-id="62614-108">A [get](../../../csharp/language-reference/keywords/get.md) property accessor is used to return the property value, and a [set](../../../csharp/language-reference/keywords/set.md) property accessor is used to assign a new value.</span></span> <span data-ttu-id="62614-109">Esses acessadores podem ter diferentes níveis de acesso.</span><span class="sxs-lookup"><span data-stu-id="62614-109">These accessors can have different access levels.</span></span> <span data-ttu-id="62614-110">Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="62614-110">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
- <span data-ttu-id="62614-111">A palavra-chave [value](../../../csharp/language-reference/keywords/value.md) é usada para definir o valor que está sendo atribuído pelo acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="62614-111">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
- <span data-ttu-id="62614-112">As propriedades podem ser de *leitura/gravação* (elas têm um acessador `get` e `set`), *somente leitura* (elas têm um acessador `get`, mas nenhum `set`) ou *somente gravação* (elas têm um acessador `set`, mas nenhum `get`).</span><span class="sxs-lookup"><span data-stu-id="62614-112">Properties can be *read-write* (they have both a `get` and a `set` accessor), *read-only* (they have a `get` accessor but no `set` accessor), or *write-only* (they have a `set` accessor, but no `get` accessor).</span></span> <span data-ttu-id="62614-113">As propriedades somente gravação são raras e são mais comumente usadas para restringir o acesso a dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="62614-113">Write-only properties are rare and are most commonly used to restrict access to sensitive data.</span></span>

- <span data-ttu-id="62614-114">As propriedades simples que não exigem nenhum código de acessador personalizado podem ser implementadas como definições de corpo da expressão ou como [propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="62614-114">Simple properties that require no custom accessor code can be implemented either as expression body definitions or as [auto-implemented properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>
 
## <a name="properties-with-backing-fields"></a><span data-ttu-id="62614-115">Propriedades com campos de suporte</span><span class="sxs-lookup"><span data-stu-id="62614-115">Properties with backing fields</span></span>

<span data-ttu-id="62614-116">Um padrão básico para implementar uma propriedade envolve o uso de um campo de suporte particular da propriedade para definir e recuperar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="62614-116">One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value.</span></span> <span data-ttu-id="62614-117">O acessador `get` retorna o valor do campo particular e o acessador `set` pode realizar alguma validação de dados antes de atribuir um valor ao campo particular.</span><span class="sxs-lookup"><span data-stu-id="62614-117">The `get` accessor returns the value of the private field, and the `set` accessor may perform some data validation before assigning a value to the private field.</span></span> <span data-ttu-id="62614-118">Os dois acessadores também podem realizar alguma conversão ou cálculo nos dados antes de eles serem armazenados ou retornados.</span><span class="sxs-lookup"><span data-stu-id="62614-118">Both accessors may also perform some conversion or computation on the data before it is stored or returned.</span></span>

<span data-ttu-id="62614-119">O exemplo a seguir ilustra esse padrão.</span><span class="sxs-lookup"><span data-stu-id="62614-119">The following example illustrates this pattern.</span></span> <span data-ttu-id="62614-120">Neste exemplo, a classe `TimePeriod` representa um intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="62614-120">In this example, the `TimePeriod` class represents an interval of time.</span></span> <span data-ttu-id="62614-121">Internamente, a classe armazena o intervalo de tempo em segundos em um campo particular chamado `seconds`.</span><span class="sxs-lookup"><span data-stu-id="62614-121">Internally, the class stores the time interval in seconds in a private field named `seconds`.</span></span> <span data-ttu-id="62614-122">Uma propriedade de leitura/gravação chamada `Hours` permite que o cliente especifique o intervalo de tempo em horas.</span><span class="sxs-lookup"><span data-stu-id="62614-122">A read-write property named `Hours` allows the customer to specify the time interval in hours.</span></span> <span data-ttu-id="62614-123">Tanto o acessador `get` quanto o `set` executam a conversão necessária entre horas e segundos.</span><span class="sxs-lookup"><span data-stu-id="62614-123">Both the `get` and the `set` accessors perform the necessary conversion between hours and seconds.</span></span> <span data-ttu-id="62614-124">Além disso, o acessador `set` valida os dados e gera um @System.ArgumentOutOfRangeException se o número de horas é inválido.</span><span class="sxs-lookup"><span data-stu-id="62614-124">In addition, the `set` accessor validates the data and throws an @System.ArgumentOutOfRangeException if the number of hours is invalid.</span></span> 
   
 <span data-ttu-id="62614-125">[!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="62614-125">[!code-cs[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="62614-126">Definições de corpo de expressão</span><span class="sxs-lookup"><span data-stu-id="62614-126">Expression body definitions</span></span>  

 <span data-ttu-id="62614-127">Os acessadores de propriedade geralmente consistem em instruções de linha única que simplesmente atribuem ou retornam o resultado de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="62614-127">Property accessors often consist of single-line statements that just assign or return the result of an expression.</span></span> <span data-ttu-id="62614-128">Você pode implementar essas propriedades como membros aptos para expressão.</span><span class="sxs-lookup"><span data-stu-id="62614-128">You can implement these properties as expression-bodied members.</span></span> <span data-ttu-id="62614-129">As definições de corpo da expressão consistem no símbolo `=>` seguido pela expressão à qual atribuir ou recuperar da propriedade.</span><span class="sxs-lookup"><span data-stu-id="62614-129">Expression body definitions consist of the `=>` symbol followed by the expression to assign to or retrieve from the property.</span></span>

 <span data-ttu-id="62614-130">A partir do C#6, as propriedades somente leitura podem implementar o acessador `get` como um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="62614-130">Starting with C# 6, read-only properties can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="62614-131">Nesse caso, nem a palavra-chave do acessador `get` nem a palavra-chave `return` é usada.</span><span class="sxs-lookup"><span data-stu-id="62614-131">In this case, neither the `get` accessor keyword nor the `return` keyword is used.</span></span> <span data-ttu-id="62614-132">O exemplo a seguir implementa a propriedade `Name` somente leitura como um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="62614-132">The following example implements the read-only `Name` property as an expression-bodied member.</span></span>

 <span data-ttu-id="62614-133">[!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="62614-133">[!code-cs[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]</span></span>  

 <span data-ttu-id="62614-134">A partir do C# 7, os acessadores `get` e `set` podem ser implementados como membros aptos para expressão.</span><span class="sxs-lookup"><span data-stu-id="62614-134">Starting with C# 7, both the `get` and the `set` accessor can be implemented as expression-bodied members.</span></span> <span data-ttu-id="62614-135">Nesse caso, as palavras-chave `get` e `set` devem estar presentes.</span><span class="sxs-lookup"><span data-stu-id="62614-135">In this case, the `get` and `set` keywords must be present.</span></span> <span data-ttu-id="62614-136">O exemplo a seguir ilustra o uso de definições de corpo de expressão para ambos os acessadores.</span><span class="sxs-lookup"><span data-stu-id="62614-136">The following example illustrates the use of expression body definitions for both accessors.</span></span> <span data-ttu-id="62614-137">Observe que a palavra-chave `return` não é usada com o acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="62614-137">Note that the `return` keyword is not used with the `get` accessor.</span></span>
 
  <span data-ttu-id="62614-138">[!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="62614-138">[!code-cs[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]</span></span>  

## <a name="auto-implemented-properties"></a><span data-ttu-id="62614-139">Propriedades autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="62614-139">Auto-implemented properties</span></span>

<span data-ttu-id="62614-140">Em alguns casos, os acessadores `get` e `set` da propriedade apenas atribuem um valor ou recuperam um valor de um campo de suporte sem incluir nenhuma lógica adicional.</span><span class="sxs-lookup"><span data-stu-id="62614-140">In some cases, property `get` and `set` accessors just assign a value to or retrieve a value from a backing field without including any additional logic.</span></span> <span data-ttu-id="62614-141">Usando propriedades autoimplementadas, você pode simplificar o código enquanto o compilador C# fornece de forma transparente o campo de suporte para você.</span><span class="sxs-lookup"><span data-stu-id="62614-141">By using auto-implemented properties, you can simplify your code while having the C# compiler transparently provide the backing field for you.</span></span> 

<span data-ttu-id="62614-142">Se uma propriedade tiver tanto um acessador `get` quanto um `set`, ambos deverão ser autoimplementados.</span><span class="sxs-lookup"><span data-stu-id="62614-142">If a property has both a `get` and a `set` accessor, both must be auto-implemented.</span></span> <span data-ttu-id="62614-143">Você define uma propriedade autoimplementada usando as palavras-chave `get` e `set` sem fornecer qualquer implementação.</span><span class="sxs-lookup"><span data-stu-id="62614-143">You define an auto-implemented property by using the `get` and `set` keywords without providing any implementation.</span></span> <span data-ttu-id="62614-144">O exemplo a seguir repete o anterior, exceto que `Name` e `Price` são propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="62614-144">The following example repeats the previous one, except that `Name` and `Price` are auto-implemented properties.</span></span> <span data-ttu-id="62614-145">Observe que o exemplo também remove o construtor parametrizado, para que os objetos `SaleItem` agora sejam inicializados com uma chamada para o construtor padrão e um [inicializador de objeto](object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="62614-145">Note that the example also removes the parameterized constructor, so that `SaleItem` objects are now initialized with a call to the default constructor and an [object initializer](object-and-collection-initializers.md).</span></span>

  <span data-ttu-id="62614-146">[!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="62614-146">[!code-cs[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]</span></span>  

## <a name="related-sections"></a><span data-ttu-id="62614-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="62614-147">Related sections</span></span>  
  
-   [<span data-ttu-id="62614-148">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="62614-148">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="62614-149">Propriedades de interface</span><span class="sxs-lookup"><span data-stu-id="62614-149">Interface Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [<span data-ttu-id="62614-150">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="62614-150">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="62614-151">Restringindo a acessibilidade ao acessador</span><span class="sxs-lookup"><span data-stu-id="62614-151">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [<span data-ttu-id="62614-152">Propriedades Autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="62614-152">Auto-Implemented Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="62614-153">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="62614-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62614-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62614-154">See also</span></span>
 <span data-ttu-id="62614-155">[Guia de programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="62614-155">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="62614-156">[Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="62614-156">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="62614-157">[Indexadores](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="62614-157">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="62614-158">[Palavra-chave get](../../../csharp/language-reference/keywords/get.md)  </span><span class="sxs-lookup"><span data-stu-id="62614-158">[get keyword](../../../csharp/language-reference/keywords/get.md)  </span></span>  
 [<span data-ttu-id="62614-159">Palavra-chave set</span><span class="sxs-lookup"><span data-stu-id="62614-159">set keyword</span></span>](../../../csharp/language-reference/keywords/set.md)    

