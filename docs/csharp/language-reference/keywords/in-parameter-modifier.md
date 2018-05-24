---
title: Modificador de parâmetro in (referência do C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 58500cf2caa1446af6b663f1b765c0be92309f1d
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="534e5-102">Modificador de parâmetro in (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="534e5-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="534e5-103">A palavra-chave `in` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="534e5-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="534e5-104">É como as palavras-chave [ref](ref.md) ou [out](out-parameter-modifier.md), exceto que os argumentos `in` não podem ser modificados pelo método chamado.</span><span class="sxs-lookup"><span data-stu-id="534e5-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="534e5-105">Enquanto os argumentos `ref` podem ser modificados, os argumentos `out` devem ser modificados pelo chamador, e será possível observar essas modificações no contexto da chamada.</span><span class="sxs-lookup"><span data-stu-id="534e5-105">Whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="534e5-106">O exemplo anterior demonstra que o modificador `in` é geralmente desnecessário no site de chamada.</span><span class="sxs-lookup"><span data-stu-id="534e5-106">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="534e5-107">Ele apenas é necessário na declaração do método.</span><span class="sxs-lookup"><span data-stu-id="534e5-107">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="534e5-108">A palavra-chave `in` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é contravariante, como parte de uma instrução `foreach` ou como parte de uma cláusula `join` em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="534e5-108">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="534e5-109">Para obter mais informações sobre o uso da palavra-chave `in` nesses contextos, confira [in](in.md) que fornece links para todos esses usos.</span><span class="sxs-lookup"><span data-stu-id="534e5-109">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="534e5-110">As variáveis passadas como argumentos `in` precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="534e5-110">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="534e5-111">No entanto, o método chamado não pode atribuir um valor nem modificar o argumento.</span><span class="sxs-lookup"><span data-stu-id="534e5-111">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="534e5-112">Embora as palavras-chave `in`, `ref` e `out` causem um comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="534e5-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="534e5-113">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="534e5-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="534e5-114">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="534e5-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="534e5-115">A sobrecarga com base na presença de `in` é permitida:</span><span class="sxs-lookup"><span data-stu-id="534e5-115">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="534e5-116">Regras de resolução de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="534e5-116">Overload resolution rules</span></span>

<span data-ttu-id="534e5-117">Você pode entender as regras de resolução de sobrecarga para métodos por valor versus argumentos `in`, compreendendo a motivação dos argumentos `in`.</span><span class="sxs-lookup"><span data-stu-id="534e5-117">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="534e5-118">A definição de métodos usando parâmetros `in` é uma possível otimização de desempenho.</span><span class="sxs-lookup"><span data-stu-id="534e5-118">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="534e5-119">Alguns argumentos de tipo `struct` podem ser grandes em tamanho e, quando os métodos são chamados em loops rígidos ou caminhos de código críticos, o custo da cópia dessas estruturas é crítico.</span><span class="sxs-lookup"><span data-stu-id="534e5-119">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="534e5-120">Os métodos declaram parâmetros `in` para especificar que argumentos podem ser passados por referência com segurança porque o método chamado não modifica o estado desse argumento.</span><span class="sxs-lookup"><span data-stu-id="534e5-120">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="534e5-121">A passagem desses argumentos por referência evita a cópia (possivelmente) dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="534e5-121">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="534e5-122">A especificação de `in` em argumentos no site de chamada é normalmente opcional.</span><span class="sxs-lookup"><span data-stu-id="534e5-122">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="534e5-123">Não há diferença semântica entre passar argumentos por valor e transmiti-los por meio de referência usando o modificador `in`.</span><span class="sxs-lookup"><span data-stu-id="534e5-123">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="534e5-124">O modificador `in` no site de chamada é opcional, pois não é necessário indicar que o valor do argumento pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="534e5-124">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="534e5-125">Você adiciona explicitamente o modificador `in` no site de chamada para garantir que o argumento seja passado por referência, e não por valor.</span><span class="sxs-lookup"><span data-stu-id="534e5-125">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="534e5-126">O uso explícito de `in` tem dois efeitos:</span><span class="sxs-lookup"><span data-stu-id="534e5-126">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="534e5-127">Primeiro: especificar `in` no site de chamada força o compilador a selecionar um método definido com um parâmetro `in` correspondente.</span><span class="sxs-lookup"><span data-stu-id="534e5-127">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="534e5-128">Caso contrário, quando dois métodos diferem apenas na presença de `in`, a sobrecarga por valor é uma correspondência melhor.</span><span class="sxs-lookup"><span data-stu-id="534e5-128">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="534e5-129">Segundo: especificar `in` declara sua intenção de passar um argumento por referência.</span><span class="sxs-lookup"><span data-stu-id="534e5-129">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="534e5-130">O argumento usado com `in` deve representar um local ao qual se possa fazer referência diretamente.</span><span class="sxs-lookup"><span data-stu-id="534e5-130">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="534e5-131">As mesmas regras gerais para argumentos `out` e `ref` se aplicam: você não pode usar constantes, propriedades comuns ou outras expressões que produzem valores.</span><span class="sxs-lookup"><span data-stu-id="534e5-131">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="534e5-132">Caso contrário, a omissão de `in` no site de chamada informa ao compilador que você permitirá a criação de uma variável temporária para passar por referência de somente leitura para o método.</span><span class="sxs-lookup"><span data-stu-id="534e5-132">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="534e5-133">O compilador cria uma variável temporária para superar várias restrições com argumentos `in`:</span><span class="sxs-lookup"><span data-stu-id="534e5-133">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="534e5-134">Uma variável temporária permite constantes de tempo de compilação como parâmetros `in`.</span><span class="sxs-lookup"><span data-stu-id="534e5-134">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="534e5-135">Uma variável temporária permite propriedades ou outras expressões para parâmetros `in`.</span><span class="sxs-lookup"><span data-stu-id="534e5-135">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="534e5-136">Uma variável temporária permite argumentos em que há uma conversão implícita do tipo de argumento para o tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="534e5-136">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="534e5-137">Em todas as instâncias anteriores, o compilador cria uma variável temporária que armazena o valor da constante, da propriedade ou de outra expressão.</span><span class="sxs-lookup"><span data-stu-id="534e5-137">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="534e5-138">O código a seguir ilustra essas regras:</span><span class="sxs-lookup"><span data-stu-id="534e5-138">The following code illustrates these rules:</span></span>

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="534e5-139">Agora, vamos supor que outro método usando argumentos por valor estivesse disponível.</span><span class="sxs-lookup"><span data-stu-id="534e5-139">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="534e5-140">Os resultados são alterados conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="534e5-140">The results change as shown in the following code:</span></span>

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="534e5-141">A única chamada de método em que o argumento é passado por referência é a chamada final.</span><span class="sxs-lookup"><span data-stu-id="534e5-141">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="534e5-142">O código anterior usa `int` como o tipo de argumento por questão de simplicidade.</span><span class="sxs-lookup"><span data-stu-id="534e5-142">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="534e5-143">Como `int` não é maior que uma referência na maioria dos computadores modernos, não há nenhum benefício em passar um único `int` como uma referência readonly.</span><span class="sxs-lookup"><span data-stu-id="534e5-143">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="534e5-144">Limitações em parâmetros `in`</span><span class="sxs-lookup"><span data-stu-id="534e5-144">Limitations on `in` parameters</span></span>

<span data-ttu-id="534e5-145">Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="534e5-145">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="534e5-146">Métodos assíncronos, que você define usando o modificador [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="534e5-146">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="534e5-147">Métodos de iterador, que incluem uma instrução [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="534e5-147">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="534e5-148">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="534e5-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="534e5-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="534e5-149">See Also</span></span>  
 [<span data-ttu-id="534e5-150">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="534e5-150">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="534e5-151">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="534e5-151">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="534e5-152">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="534e5-152">C# Keywords</span></span>](index.md)  
 <span data-ttu-id="534e5-153">[Parâmetros de método](method-parameters.md) [Semântica de referência com Tipos de valor](../../reference-semantics-with-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="534e5-153">[Method Parameters](method-parameters.md) [Reference Semantics with Value Types](../../reference-semantics-with-value-types.md)</span></span>
