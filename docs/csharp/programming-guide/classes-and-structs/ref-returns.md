---
title: Valores ref return e ref local (Guia de C#)
description: Saiba como definir e usar os valores ref return e ref local
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: a74563c0d24b6cd2a2fa8534787f078f3cc92674
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="71720-103">Ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="71720-103">Ref returns and ref locals</span></span>

<span data-ttu-id="71720-104">Começando com o C# 7, o C# dá suporte a valores retornados por referência (ref returns).</span><span class="sxs-lookup"><span data-stu-id="71720-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="71720-105">Um valor retornado por referência permite que um método retorne uma referência a uma variável, em vez de um valor, de volta para um chamador.</span><span class="sxs-lookup"><span data-stu-id="71720-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="71720-106">O chamador pode optar por tratar a variável retornada como se tivesse sido retornada por valor ou referência.</span><span class="sxs-lookup"><span data-stu-id="71720-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="71720-107">O chamador pode criar uma nova variável que seja uma referência ao valor retornado, chamado de ref local.</span><span class="sxs-lookup"><span data-stu-id="71720-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="71720-108">O que é um valor retornado por referência?</span><span class="sxs-lookup"><span data-stu-id="71720-108">What is a reference return value?</span></span>

<span data-ttu-id="71720-109">A maioria dos desenvolvedores estão familiarizados com passar um argumento para um método chamado *por referência*.</span><span class="sxs-lookup"><span data-stu-id="71720-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="71720-110">A lista de argumentos de um método chamado inclui uma variável passada por referência, e todas as alterações no valor dela pelo método chamado são observadas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="71720-110">A called method's argument list includes a variable passed by reference, and any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="71720-111">Um *valor retornado de referência* significa que um método retorna uma *referência* (ou um alias) para alguma variável cujo escopo inclui o método e cujo tempo de vida deve ultrapassar o retorno do método.</span><span class="sxs-lookup"><span data-stu-id="71720-111">A *reference return value* means that a method returns a *reference* (or an alias) to some variable whose scope includes the method and whose lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="71720-112">As modificações no valor retornado do método pelo chamador são feitas na variável que é retornada pelo método.</span><span class="sxs-lookup"><span data-stu-id="71720-112">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="71720-113">Declarar que um método retorna um *valor retornado de referência* indica que o método retorna um alias para uma variável.</span><span class="sxs-lookup"><span data-stu-id="71720-113">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="71720-114">A intenção de design muitas vezes é que o código de chamada deve ter acesso a essa variável por meio do alias, inclusive para modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="71720-114">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="71720-115">Por conseguinte, métodos retornados por referência não podem ter o tipo de retorno `void`.</span><span class="sxs-lookup"><span data-stu-id="71720-115">It follows that methods returning by reference cannot have the return type `void`.</span></span>

<span data-ttu-id="71720-116">Há algumas restrições quanto à expressão que um método pode retornar como um valor retornado por referência.</span><span class="sxs-lookup"><span data-stu-id="71720-116">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="71720-117">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="71720-117">These include:</span></span>

- <span data-ttu-id="71720-118">O valor retornado deve ter um tempo de vida que ultrapasse a execução do método.</span><span class="sxs-lookup"><span data-stu-id="71720-118">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="71720-119">Em outras palavras, não pode ser uma variável local no método que o retorna.</span><span class="sxs-lookup"><span data-stu-id="71720-119">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="71720-120">Ele pode ser uma instância ou um campo estático de uma classe ou pode ser um argumento passado para o método.</span><span class="sxs-lookup"><span data-stu-id="71720-120">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="71720-121">Tentar retornar a uma variável local gera o erro do compilador CS8168, "não é possível retornar o 'obj' local por referência porque ele não é um ref local".</span><span class="sxs-lookup"><span data-stu-id="71720-121">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="71720-122">O valor retornado não pode ser um `null` literal.</span><span class="sxs-lookup"><span data-stu-id="71720-122">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="71720-123">A tentativa de retornar `null` gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."</span><span class="sxs-lookup"><span data-stu-id="71720-123">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="71720-124">Um método com um retorno de referência pode retornar um alias para uma variável cujo valor é atualmente o valor nulo (não instanciado) ou um [tipo anulável](../nullable-types/index.md) para um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="71720-124">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="71720-125">O valor retornado não pode ser uma constante, um membro de enumeração, o valor retornado por valor de uma propriedade ou um método `class` ou `struct`.</span><span class="sxs-lookup"><span data-stu-id="71720-125">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="71720-126">A tentativa de retornar um deles gera o erro do compilador CS8156, "Uma expressão não pode ser usada neste contexto porque ela não pode ser retornada por referência."</span><span class="sxs-lookup"><span data-stu-id="71720-126">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="71720-127">Além disso, como um método assíncrono pode ser retornado antes de sua execução ser concluída, embora seu valor retornado ainda seja desconhecido, os valores retornados de referência não são permitidos em métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="71720-127">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="71720-128">Definindo um valor retornado ref</span><span class="sxs-lookup"><span data-stu-id="71720-128">Defining a ref return value</span></span>

<span data-ttu-id="71720-129">Você define um valor retornado ref adicionando a palavra-chave [ref](../../language-reference/keywords/ref.md) ao tipo de retorno da assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="71720-129">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="71720-130">Por exemplo, a assinatura a seguir indica que a propriedade `GetContactInformation` retorna uma referência a um objeto `Person` ao chamador:</span><span class="sxs-lookup"><span data-stu-id="71720-130">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="71720-131">Além disso, o nome do objeto retornado por cada instrução [return](../../language-reference/keywords/return.md) no corpo do método deve ser precedida pela palavra-chave [ref](../../language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="71720-131">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="71720-132">Por exemplo, a instrução `return` a seguir retorna uma referência a um objeto `Person` chamado `p`:</span><span class="sxs-lookup"><span data-stu-id="71720-132">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="71720-133">Consumindo um valor retornado ref</span><span class="sxs-lookup"><span data-stu-id="71720-133">Consuming a ref return value</span></span>

<span data-ttu-id="71720-134">O valor retornado de ref é um alias para outra variável no escopo do método chamado.</span><span class="sxs-lookup"><span data-stu-id="71720-134">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="71720-135">Você pode interpretar qualquer uso do retorno de ref como usando a variável da qual ele é um alias:</span><span class="sxs-lookup"><span data-stu-id="71720-135">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="71720-136">Ao atribuir o valor, você atribui um valor à variável da qual ele é um alias.</span><span class="sxs-lookup"><span data-stu-id="71720-136">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="71720-137">Ao ler o valor, você lê o valor da variável da qual ele é um alias.</span><span class="sxs-lookup"><span data-stu-id="71720-137">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="71720-138">Se o retornar *por referência*, você retornará um alias para a mesma variável.</span><span class="sxs-lookup"><span data-stu-id="71720-138">If you return it *by reference* you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="71720-139">Se você o passar para outro método *por referência*, passará uma referência à variável da qual ele é um alias.</span><span class="sxs-lookup"><span data-stu-id="71720-139">If you pass it to another method *by reference* you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="71720-140">Ao criar um alias de [referência local](#ref-local), você cria um novo alias para a mesma variável.</span><span class="sxs-lookup"><span data-stu-id="71720-140">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="71720-141">Ref locals</span><span class="sxs-lookup"><span data-stu-id="71720-141">Ref locals</span></span>

<span data-ttu-id="71720-142">Suponha que o método `GetContactInformation` seja declarado como uma referência de retorno:</span><span class="sxs-lookup"><span data-stu-id="71720-142">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="71720-143">Uma atribuição por valor lê o valor de uma variável e o atribui a uma nova variável:</span><span class="sxs-lookup"><span data-stu-id="71720-143">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="71720-144">A atribuição anterior declara `p` como uma variável local.</span><span class="sxs-lookup"><span data-stu-id="71720-144">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="71720-145">O valor inicial é copiado da leitura do valor retornado por `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="71720-145">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="71720-146">As atribuições futuras para `p` não alterarão o valor da variável retornado por `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="71720-146">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="71720-147">A variável `p` não é um alias para a variável retornada.</span><span class="sxs-lookup"><span data-stu-id="71720-147">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="71720-148">Você declara uma variável *ref local* para copiar o alias para o valor original.</span><span class="sxs-lookup"><span data-stu-id="71720-148">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="71720-149">Na atribuição de seguir, `p` é um alias para a variável retornada de `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="71720-149">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="71720-150">O uso subsequente de `p` é o mesmo que usar a variável retornada pelo `GetContactInformation` porque `p` é um alias dessa variável.</span><span class="sxs-lookup"><span data-stu-id="71720-150">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="71720-151">As alterações em `p` também alteram a variável retornada de `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="71720-151">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="71720-152">Observe que a palavra-chave `ref` é usada antes da declaração de variável local *e* antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="71720-152">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> <span data-ttu-id="71720-153">Falha ao incluir palavras-chave `ref` na declaração da variável e resultados de atribuição no erro do compilador CS8172, "Não é possível inicializar uma variável por referência com um valor."</span><span class="sxs-lookup"><span data-stu-id="71720-153">Failure to include both `ref` keywords in the variable declaration and assignment results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="71720-154">Ref returns e ref locals: um exemplo</span><span class="sxs-lookup"><span data-stu-id="71720-154">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="71720-155">O exemplo a seguir define uma classe `NumberStore` que armazena uma matriz de valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="71720-155">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="71720-156">O método `FindNumber` retorna por referência o primeiro número maior ou igual ao número passado como um argumento.</span><span class="sxs-lookup"><span data-stu-id="71720-156">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="71720-157">Se nenhum número for maior ou igual ao argumento, o método retornará o número no índice 0.</span><span class="sxs-lookup"><span data-stu-id="71720-157">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="71720-158">A exemplo a seguir chama o método `NumberStore.FindNumber` para recuperar o primeiro valor maior ou igual a 16.</span><span class="sxs-lookup"><span data-stu-id="71720-158">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="71720-159">O chamador então dobra o valor retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="71720-159">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="71720-160">Assim como mostra a saída do exemplo, essa alteração é refletida no valor dos elementos de matriz da instância `NumberStore`.</span><span class="sxs-lookup"><span data-stu-id="71720-160">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="71720-161">Sem suporte para valores retornados por referência, essa operação normalmente é executada retornando-se o índice do elemento de matriz, juntamente com o respectivo valor.</span><span class="sxs-lookup"><span data-stu-id="71720-161">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="71720-162">O chamador pode usar esse índice para modificar o valor em uma chamada de método separada.</span><span class="sxs-lookup"><span data-stu-id="71720-162">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="71720-163">No entanto, o chamador também pode modificar o índice para acessar e possivelmente modificar outros valores de matriz.</span><span class="sxs-lookup"><span data-stu-id="71720-163">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="71720-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71720-164">See also</span></span>

[<span data-ttu-id="71720-165">ref keyword</span><span class="sxs-lookup"><span data-stu-id="71720-165">ref keyword</span></span>](../../language-reference/keywords/ref.md)
