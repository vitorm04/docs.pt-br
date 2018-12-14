---
title: Operador -&gt; (Referência de C#)
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 178724ede105d809bd812461121a38d5a0e90517
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144124"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="3917b-102">Operador -&gt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3917b-102">-&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="3917b-103">O operador de acesso de membro de ponteiro `->` combina a indireção do ponteiro e o acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="3917b-103">The pointer member access operator `->` combines pointer indirection and member access.</span></span>

<span data-ttu-id="3917b-104">Se `x` é um ponteiro do tipo `T*` e `y` é um membro acessível de `T`, uma expressão do formulário</span><span class="sxs-lookup"><span data-stu-id="3917b-104">If `x` is a pointer of the type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="3917b-105">equivale a</span><span class="sxs-lookup"><span data-stu-id="3917b-105">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="3917b-106">O operador `->` requer contexto [não seguro](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="3917b-106">The `->` operator requires [unsafe](../keywords/unsafe.md) context.</span></span>

<span data-ttu-id="3917b-107">Para saber mais, confira [Como acessar um membro com um ponteiro](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="3917b-107">For more information, see [How to: access a member with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3917b-108">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="3917b-108">Operator overloadability</span></span>

<span data-ttu-id="3917b-109">O operador `->` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="3917b-109">The `->` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3917b-110">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3917b-110">C# language specification</span></span>

<span data-ttu-id="3917b-111">Para saber mais, confira a seção [Acesso de membro de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-member-access) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3917b-111">For more information, see the [Pointer member access](~/_csharplang/spec/unsafe-code.md#pointer-member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3917b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3917b-112">See also</span></span>

- [<span data-ttu-id="3917b-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3917b-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3917b-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3917b-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3917b-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3917b-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3917b-116">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3917b-116">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
