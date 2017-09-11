---
title: "Usando indexadores (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 30
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
ms.openlocfilehash: ac8990fa2efb1a2ea24497a3a5de3649795c7b23
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="9ec5e-102">Usando indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9ec5e-102">Using Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="9ec5e-103">Os indexadores são uma conveniência sintática que permitem criar uma [classe](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md) ou [interface](../../../csharp/language-reference/keywords/interface.md) que os aplicativos clientes podem acessar como uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-103">Indexers are a syntactic convenience that enable you to create a [class](../../../csharp/language-reference/keywords/class.md), [struct](../../../csharp/language-reference/keywords/struct.md), or [interface](../../../csharp/language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="9ec5e-104">Os indexadores são implementados em tipos cuja principal finalidade é encapsular uma coleção ou matriz interna.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="9ec5e-105">Por exemplo, suponha que você tem uma classe nomeada TempRecord que representa a temperatura em Farenheit conforme registrada 10 vezes diferentes durante um período de 24 horas.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-105">For example, suppose you have a class named TempRecord that represents the temperature in Farenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="9ec5e-106">A classe contém uma matriz nomeada “temps” de flutuação de tipo para representar as temperaturas e uma <xref:System.DateTime> que representa as datas em que as temperaturas foram registradas.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-106">The class contains an array named "temps" of type float to represent the temperatures, and a <xref:System.DateTime> that represents the date the temperatures were recorded.</span></span> <span data-ttu-id="9ec5e-107">Ao implementar um indexador nessa classe, os clientes podem acessar as temperaturas em uma instância TempRecord como `float temp = tr[4]` em vez de `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-107">By implementing an indexer in this class, clients can access the temperatures in a TempRecord instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="9ec5e-108">A notação do indexador não simplifica somente a sintaxe para aplicativos clientes; ela também torna a classe e sua finalidade mais intuitivas para que os outros desenvolvedores entendam.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
 <span data-ttu-id="9ec5e-109">Para declarar um indexador em uma classe ou struct, use a palavra-chave [this](../../../csharp/language-reference/keywords/this.md), como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="9ec5e-109">To declare an indexer on a class or struct, use the [this](../../../csharp/language-reference/keywords/this.md) keyword, as in this example:</span></span>  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="9ec5e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ec5e-110">Remarks</span></span>  
 <span data-ttu-id="9ec5e-111">O tipo de um indexador e o tipo dos seus parâmetros devem ser pelo menos tão acessíveis quanto o próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="9ec5e-112">Para obter mais informações sobre níveis de acessibilidade, consulte [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9ec5e-112">For more information about accessibility levels, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="9ec5e-113">Para obter mais informações sobre como usar indexadores com uma interface, consulte [Indexadores de Interface](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="9ec5e-113">For more information about how to use indexers with an interface, see [Interface Indexers](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="9ec5e-114">A assinatura de um indexador consiste do número e dos tipos de seus parâmetros formais.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="9ec5e-115">Ela não inclui o tipo de indexador nem os nomes dos parâmetros formais.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-115">It does not include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="9ec5e-116">Se você declarar mais de um indexador na mesma classe, eles terão diferentes assinaturas.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="9ec5e-117">Um valor de indexador não é classificado como uma variável; portanto, não é possível passar um valor de indexador como um parâmetro [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).</span><span class="sxs-lookup"><span data-stu-id="9ec5e-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameter.</span></span>  
  
 <span data-ttu-id="9ec5e-118">Para fornecer ao indexador um nome que outras linguagens possam usar, use um atributo `name` na declaração.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-118">To provide the indexer with a name that other languages can use, use a `name` attribute in the declaration.</span></span> <span data-ttu-id="9ec5e-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9ec5e-119">For example:</span></span>  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 <span data-ttu-id="9ec5e-120">Este indexador terá o nome `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-120">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="9ec5e-121">Não fornecer o atributo de nome tornaria `Item` o nome padrão.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-121">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="9ec5e-122">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="9ec5e-122">Example 1</span></span>  
  
### <a name="description"></a><span data-ttu-id="9ec5e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ec5e-123">Description</span></span>  
 <span data-ttu-id="9ec5e-124">O exemplo a seguir mostra como declarar um campo de matriz privada, `temps` e um indexador.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-124">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="9ec5e-125">O indexador permite acesso direto à instância `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-125">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="9ec5e-126">A alternativa ao uso do indexador é declarar a matriz como um membro [público](../../../csharp/language-reference/keywords/public.md) e acessar seus membros, `tempRecord.temps[i]`, diretamente.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-126">The alternative to using the indexer is to declare the array as a [public](../../../csharp/language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="9ec5e-127">Observe que, quando o acesso de um indexador é avaliado, por exemplo, em uma instrução `Console.Write`, o acessador [get](../../../csharp/language-reference/keywords/get.md) é invocado.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-127">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../../csharp/language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="9ec5e-128">Portanto, se não existir nenhum acessador `get`, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-128">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9ec5e-129">Código</span><span class="sxs-lookup"><span data-stu-id="9ec5e-129">Code</span></span>  
 <span data-ttu-id="9ec5e-130">[!code-cs[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9ec5e-130">[!code-cs[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]</span></span>  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="9ec5e-131">Indexando usando outros valores</span><span class="sxs-lookup"><span data-stu-id="9ec5e-131">Indexing Using Other Values</span></span>  
 <span data-ttu-id="9ec5e-132">O C# não limita o tipo de índice ao inteiro.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-132">C# does not limit the index type to integer.</span></span> <span data-ttu-id="9ec5e-133">Por exemplo, talvez seja útil usar uma cadeia de caracteres com um indexador.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-133">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="9ec5e-134">Esse indexador pode ser implementado pesquisando a cadeia de caracteres na coleção e retornando o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-134">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="9ec5e-135">Como os acessadores podem ser sobrecarregados, as versões do inteiro e da cadeia de caracteres podem coexistir.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-135">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="9ec5e-136">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="9ec5e-136">Example 2</span></span>  
  
### <a name="description"></a><span data-ttu-id="9ec5e-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ec5e-137">Description</span></span>  
 <span data-ttu-id="9ec5e-138">Neste exemplo, uma classe é declarada que armazena os dias da semana.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-138">In this example, a class is declared that stores the days of the week.</span></span> <span data-ttu-id="9ec5e-139">Um acessador `get` é declarado que aceita uma cadeia de caracteres, o nome de um dia e retorna o inteiro correspondente.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-139">A `get` accessor is declared that takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="9ec5e-140">Por exemplo, domingo retornará 0, segunda-feira retornará 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-140">For example, Sunday will return 0, Monday will return 1, and so on.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9ec5e-141">Código</span><span class="sxs-lookup"><span data-stu-id="9ec5e-141">Code</span></span>  
 <span data-ttu-id="9ec5e-142">[!code-cs[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9ec5e-142">[!code-cs[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9ec5e-143">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9ec5e-143">Robust Programming</span></span>  
 <span data-ttu-id="9ec5e-144">Há duas maneiras principais nas quais a segurança e a confiabilidade de indexadores podem ser melhoradas:</span><span class="sxs-lookup"><span data-stu-id="9ec5e-144">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
-   <span data-ttu-id="9ec5e-145">Certifique-se de incorporar algum tipo de estratégia de tratamento de erros para manipular a chance de passagem de código cliente em um valor de índice inválido.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-145">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="9ec5e-146">Anteriormente, no primeiro exemplo neste tópico, a classe TempRecord oferece uma propriedade Length que permite que o código cliente verifique a saída antes de passá-la para o indexador.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-146">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="9ec5e-147">Também é possível colocador o código de tratamento de erro dentro do próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-147">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="9ec5e-148">Certifique-se documentar para os usuários as exceções que você gera dentro de um acessador do indexador.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-148">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
-   <span data-ttu-id="9ec5e-149">Defina a acessibilidade dos acessadores `get` e [set](../../../csharp/language-reference/keywords/set.md) para que ela seja o mais restritiva possível.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-149">Set the accessibility of the `get` and [set](../../../csharp/language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="9ec5e-150">Isso é importante para o acessador `set` em particular.</span><span class="sxs-lookup"><span data-stu-id="9ec5e-150">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="9ec5e-151">Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="9ec5e-151">For more information, see [Restricting Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec5e-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ec5e-152">See Also</span></span>  
 <span data-ttu-id="9ec5e-153">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ec5e-153">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9ec5e-154">[Indexadores](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ec5e-154">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="9ec5e-155">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9ec5e-155">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

