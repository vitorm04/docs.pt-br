---
title: Valores ref return e ref local (Guia de C#)
description: Saiba como definir e usar os valores ref return e ref local
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 57fa8f52320b30a1cb228b41e3f5e6655c235561
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="8df88-103">Ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="8df88-103">Ref returns and ref locals</span></span>

<span data-ttu-id="8df88-104">Começando com o C# 7, o C# dá suporte a valores retornados por referência (ref returns).</span><span class="sxs-lookup"><span data-stu-id="8df88-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="8df88-105">Um valor retornado por referência permite que um método retorne uma referência a uma variável, em vez de um valor, de volta para um chamador.</span><span class="sxs-lookup"><span data-stu-id="8df88-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="8df88-106">O chamador pode optar por tratar a variável retornada como se tivesse sido retornada por valor ou referência.</span><span class="sxs-lookup"><span data-stu-id="8df88-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="8df88-107">O chamador pode criar uma nova variável que seja uma referência ao valor retornado, chamado de ref local.</span><span class="sxs-lookup"><span data-stu-id="8df88-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="8df88-108">O que é um valor retornado por referência?</span><span class="sxs-lookup"><span data-stu-id="8df88-108">What is a reference return value?</span></span>

<span data-ttu-id="8df88-109">A maioria dos desenvolvedores estão familiarizados com passar um argumento para um método chamado *por referência*.</span><span class="sxs-lookup"><span data-stu-id="8df88-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="8df88-110">A lista de argumentos de um método chamado inclui uma variável passada por referência.</span><span class="sxs-lookup"><span data-stu-id="8df88-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="8df88-111">Todas as alterações feitas pelo método chamado ao valor são observadas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="8df88-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="8df88-112">Um *valor retornado de referência* significa que um método retorna uma *referência* (ou um alias) para alguma variável.</span><span class="sxs-lookup"><span data-stu-id="8df88-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="8df88-113">O escopo da variável deve incluir o método.</span><span class="sxs-lookup"><span data-stu-id="8df88-113">That variable's scope must include the method.</span></span> <span data-ttu-id="8df88-114">O tempo de vida da variável deve ultrapassar o retorno do método.</span><span class="sxs-lookup"><span data-stu-id="8df88-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="8df88-115">As modificações no valor retornado do método pelo chamador são feitas na variável que é retornada pelo método.</span><span class="sxs-lookup"><span data-stu-id="8df88-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="8df88-116">Declarar que um método retorna um *valor retornado de referência* indica que o método retorna um alias para uma variável.</span><span class="sxs-lookup"><span data-stu-id="8df88-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="8df88-117">A intenção de design muitas vezes é que o código de chamada deve ter acesso a essa variável por meio do alias, inclusive para modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="8df88-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="8df88-118">Por conseguinte, métodos retornados por referência não podem ter o tipo de retorno `void`.</span><span class="sxs-lookup"><span data-stu-id="8df88-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="8df88-119">Há algumas restrições quanto à expressão que um método pode retornar como um valor retornado por referência.</span><span class="sxs-lookup"><span data-stu-id="8df88-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="8df88-120">As restrições incluem:</span><span class="sxs-lookup"><span data-stu-id="8df88-120">Restrictions include:</span></span>

- <span data-ttu-id="8df88-121">O valor retornado deve ter um tempo de vida que ultrapasse a execução do método.</span><span class="sxs-lookup"><span data-stu-id="8df88-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="8df88-122">Em outras palavras, não pode ser uma variável local no método que o retorna.</span><span class="sxs-lookup"><span data-stu-id="8df88-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="8df88-123">Ele pode ser uma instância ou um campo estático de uma classe ou pode ser um argumento passado para o método.</span><span class="sxs-lookup"><span data-stu-id="8df88-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="8df88-124">Tentar retornar a uma variável local gera o erro do compilador CS8168, "não é possível retornar o 'obj' local por referência porque ele não é um ref local".</span><span class="sxs-lookup"><span data-stu-id="8df88-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="8df88-125">O valor retornado não pode ser um `null` literal.</span><span class="sxs-lookup"><span data-stu-id="8df88-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="8df88-126">Retornar `null` gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."</span><span class="sxs-lookup"><span data-stu-id="8df88-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="8df88-127">Um método com um retorno de referência pode retornar um alias para uma variável cujo valor é atualmente o valor nulo (não instanciado) ou um [tipo anulável](../nullable-types/index.md) para um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="8df88-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="8df88-128">O valor retornado não pode ser uma constante, um membro de enumeração, o valor retornado por valor de uma propriedade ou um método `class` ou `struct`.</span><span class="sxs-lookup"><span data-stu-id="8df88-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="8df88-129">Violar essa regra gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."</span><span class="sxs-lookup"><span data-stu-id="8df88-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="8df88-130">Além disso, valores retornados de referência não são permitidos em métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="8df88-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="8df88-131">Um método assíncrono pode retornar antes de concluir a execução, enquanto o valor retornado ainda é desconhecido.</span><span class="sxs-lookup"><span data-stu-id="8df88-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="8df88-132">Definindo um valor retornado ref</span><span class="sxs-lookup"><span data-stu-id="8df88-132">Defining a ref return value</span></span>

<span data-ttu-id="8df88-133">Você define um valor retornado ref adicionando a palavra-chave [ref](../../language-reference/keywords/ref.md) ao tipo de retorno da assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="8df88-133">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="8df88-134">Por exemplo, a assinatura a seguir indica que a propriedade `GetContactInformation` retorna uma referência a um objeto `Person` ao chamador:</span><span class="sxs-lookup"><span data-stu-id="8df88-134">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="8df88-135">Além disso, o nome do objeto retornado por cada instrução [return](../../language-reference/keywords/return.md) no corpo do método deve ser precedida pela palavra-chave [ref](../../language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="8df88-135">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="8df88-136">Por exemplo, a instrução `return` a seguir retorna uma referência a um objeto `Person` chamado `p`:</span><span class="sxs-lookup"><span data-stu-id="8df88-136">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="8df88-137">Consumindo um valor retornado ref</span><span class="sxs-lookup"><span data-stu-id="8df88-137">Consuming a ref return value</span></span>

<span data-ttu-id="8df88-138">O valor retornado de ref é um alias para outra variável no escopo do método chamado.</span><span class="sxs-lookup"><span data-stu-id="8df88-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="8df88-139">Você pode interpretar qualquer uso do retorno de ref como usando a variável da qual ele é um alias:</span><span class="sxs-lookup"><span data-stu-id="8df88-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="8df88-140">Ao atribuir o valor, você atribui um valor à variável da qual ele é um alias.</span><span class="sxs-lookup"><span data-stu-id="8df88-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="8df88-141">Ao ler o valor, você lê o valor da variável da qual ele é um alias.</span><span class="sxs-lookup"><span data-stu-id="8df88-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="8df88-142">Se o retornar *por referência*, você retornará um alias para a mesma variável.</span><span class="sxs-lookup"><span data-stu-id="8df88-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="8df88-143">Se o passar para outro método *por referência*, você passará uma referência à variável da qual ele é um alias.</span><span class="sxs-lookup"><span data-stu-id="8df88-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="8df88-144">Ao criar um alias de [referência local](#ref-local), você cria um novo alias para a mesma variável.</span><span class="sxs-lookup"><span data-stu-id="8df88-144">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="8df88-145">Ref locals</span><span class="sxs-lookup"><span data-stu-id="8df88-145">Ref locals</span></span>

<span data-ttu-id="8df88-146">Suponha que o método `GetContactInformation` seja declarado como uma referência de retorno:</span><span class="sxs-lookup"><span data-stu-id="8df88-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="8df88-147">Uma atribuição por valor lê o valor de uma variável e o atribui a uma nova variável:</span><span class="sxs-lookup"><span data-stu-id="8df88-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="8df88-148">A atribuição anterior declara `p` como uma variável local.</span><span class="sxs-lookup"><span data-stu-id="8df88-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="8df88-149">O valor inicial é copiado da leitura do valor retornado por `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="8df88-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="8df88-150">As atribuições futuras para `p` não alterarão o valor da variável retornado por `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="8df88-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="8df88-151">A variável `p` não é um alias para a variável retornada.</span><span class="sxs-lookup"><span data-stu-id="8df88-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="8df88-152">Você declara uma variável *ref local* para copiar o alias para o valor original.</span><span class="sxs-lookup"><span data-stu-id="8df88-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="8df88-153">Na atribuição de seguir, `p` é um alias para a variável retornada de `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="8df88-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="8df88-154">O uso subsequente de `p` é o mesmo que usar a variável retornada pelo `GetContactInformation` porque `p` é um alias dessa variável.</span><span class="sxs-lookup"><span data-stu-id="8df88-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="8df88-155">As alterações em `p` também alteram a variável retornada de `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="8df88-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="8df88-156">A palavra-chave `ref` é usada antes da declaração de variável local *e* antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="8df88-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="8df88-157">Você pode acessar um valor por referência da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="8df88-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="8df88-158">Em alguns casos, acessar um valor por referência aumenta o desempenho, evitando uma operação de cópia potencialmente dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="8df88-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="8df88-159">Por exemplo, a instrução a seguir mostra como é possível definir um valor de local de ref que é usado para fazer referência a um valor.</span><span class="sxs-lookup"><span data-stu-id="8df88-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="8df88-160">A palavra-chave `ref` é usada antes da declaração da variável local *e* antes do valor, no segundo exemplo.</span><span class="sxs-lookup"><span data-stu-id="8df88-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="8df88-161">A falha ao incluir as palavras-chave `ref` na declaração e na atribuição da variável nos dois exemplos resulta no erro do compilador CS8172, "Não é possível inicializar uma variável por referência com um valor."</span><span class="sxs-lookup"><span data-stu-id="8df88-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="8df88-162">Antes do C# 7.3, variáveis locais de referência não podiam ser reatribuídas para se referir a um armazenamento diferente depois de serem inicializadas.</span><span class="sxs-lookup"><span data-stu-id="8df88-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="8df88-163">Essa restrição foi removida.</span><span class="sxs-lookup"><span data-stu-id="8df88-163">That restriction has been removed.</span></span> <span data-ttu-id="8df88-164">O exemplo a seguir mostra uma transferência:</span><span class="sxs-lookup"><span data-stu-id="8df88-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="8df88-165">Variáveis locais de referência ainda devem ser inicializadas quando são declaradas.</span><span class="sxs-lookup"><span data-stu-id="8df88-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="8df88-166">Ref returns e ref locals: um exemplo</span><span class="sxs-lookup"><span data-stu-id="8df88-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="8df88-167">O exemplo a seguir define uma classe `NumberStore` que armazena uma matriz de valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="8df88-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="8df88-168">O método `FindNumber` retorna por referência o primeiro número maior ou igual ao número passado como um argumento.</span><span class="sxs-lookup"><span data-stu-id="8df88-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="8df88-169">Se nenhum número for maior ou igual ao argumento, o método retornará o número no índice 0.</span><span class="sxs-lookup"><span data-stu-id="8df88-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="8df88-170">A exemplo a seguir chama o método `NumberStore.FindNumber` para recuperar o primeiro valor maior ou igual a 16.</span><span class="sxs-lookup"><span data-stu-id="8df88-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="8df88-171">O chamador então dobra o valor retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="8df88-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="8df88-172">A saída do exemplo mostra a alteração refletida no valor dos elementos de matriz da instância `NumberStore`.</span><span class="sxs-lookup"><span data-stu-id="8df88-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="8df88-173">Sem suporte para valores retornados por referência, essa operação é executada retornando-se o índice do elemento de matriz, juntamente com o respectivo valor.</span><span class="sxs-lookup"><span data-stu-id="8df88-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="8df88-174">O chamador pode usar esse índice para modificar o valor em uma chamada de método separada.</span><span class="sxs-lookup"><span data-stu-id="8df88-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="8df88-175">No entanto, o chamador também pode modificar o índice para acessar e possivelmente modificar outros valores de matriz.</span><span class="sxs-lookup"><span data-stu-id="8df88-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="8df88-176">A exemplo a seguir mostra como o método `FindNumber` poderia ser reescrito após o C# 7.3 para usar a transferência de local de referência:</span><span class="sxs-lookup"><span data-stu-id="8df88-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="8df88-177">Essa segunda versão é mais eficiente, com sequências mais longas em cenários em que o número procurado é mais próximo ao final da matriz.</span><span class="sxs-lookup"><span data-stu-id="8df88-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="8df88-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8df88-178">See also</span></span>

[<span data-ttu-id="8df88-179">ref keyword</span><span class="sxs-lookup"><span data-stu-id="8df88-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="8df88-180">Semântica de referência com Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="8df88-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
