---
title: Operadores nulos condicionais – referência do C#
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348837"
---
# <a name="-and--null-conditional-operators-c-reference"></a><span data-ttu-id="462a8-102">?.</span><span class="sxs-lookup"><span data-stu-id="462a8-102">?.</span></span> <span data-ttu-id="462a8-103">Operadores nulos condicionais and ?[] (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="462a8-103">and ?[] null-conditional operators (C# Reference)</span></span>

<span data-ttu-id="462a8-104">Testa o valor do operando esquerdo para nulo antes de executar um acesso de membro (`?.`) ou uma operação de índice (`?[]`); retorna `null` se o operando esquerdo é avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="462a8-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="462a8-105">Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="462a8-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

<span data-ttu-id="462a8-106">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="462a8-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="462a8-107">Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar nulo, o restante da execução da cadeia será interrompido.</span><span class="sxs-lookup"><span data-stu-id="462a8-107">If one operation in a chain of conditional member access and index operations returns null, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="462a8-108">No exemplo a seguir, `E` não será executado se `A`, `B` ou `C` for avaliado como nulo.</span><span class="sxs-lookup"><span data-stu-id="462a8-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

<span data-ttu-id="462a8-109">Outro uso para o acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.</span><span class="sxs-lookup"><span data-stu-id="462a8-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="462a8-110">A maneira antiga requer código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="462a8-110">The old way requires code like the following:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

<span data-ttu-id="462a8-111">A nova maneira é muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="462a8-111">The new way is much simpler:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="462a8-112">A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária.</span><span class="sxs-lookup"><span data-stu-id="462a8-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="462a8-113">Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="462a8-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="462a8-114">Especificações da linguagem</span><span class="sxs-lookup"><span data-stu-id="462a8-114">Language specifications</span></span>

<span data-ttu-id="462a8-115">Para saber mais, confira [Operador condicional nulo](~/_csharplang/spec/expressions.md#null-conditional-operator) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="462a8-115">For more information, see [Null-conditional operator](~/_csharplang/spec/expressions.md#null-conditional-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="462a8-116">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="462a8-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="462a8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="462a8-117">See also</span></span>

- [<span data-ttu-id="462a8-118">?? (operador de união nula)</span><span class="sxs-lookup"><span data-stu-id="462a8-118">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="462a8-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="462a8-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="462a8-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="462a8-120">C# Programming Guide</span></span>](../../programming-guide/index.md)