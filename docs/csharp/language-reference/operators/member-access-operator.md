---
title: . Operador – referência do C#
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836455"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3deea-103">.</span><span class="sxs-lookup"><span data-stu-id="3deea-103">.</span></span> <span data-ttu-id="3deea-104">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3deea-104">operator (C# Reference)</span></span>

<span data-ttu-id="3deea-105">O ponto, `.`, normalmente é usado para acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="3deea-105">The dot, `.`, is typically used for member access.</span></span>

<span data-ttu-id="3deea-106">Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="3deea-106">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="3deea-107">Use `.` para acessar um namespace aninhado dentro de um namespace, como mostra o exemplo a seguir de uma [diretiva `using`](../keywords/using-directive.md):</span><span class="sxs-lookup"><span data-stu-id="3deea-107">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- <span data-ttu-id="3deea-108">Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3deea-108">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  <span data-ttu-id="3deea-109">Use a [diretiva `using`](../keywords/using-directive.md) para tornar opcional o uso de nomes qualificados.</span><span class="sxs-lookup"><span data-stu-id="3deea-109">Use the [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="3deea-110">Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3deea-110">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

<span data-ttu-id="3deea-111">Também pode-se usar `.` para invocar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="3deea-111">You can also use `.` to invoke an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3deea-112">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="3deea-112">Operator overloadability</span></span>

<span data-ttu-id="3deea-113">O operador `.` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="3deea-113">The operator `.` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3deea-114">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3deea-114">C# language specification</span></span>

<span data-ttu-id="3deea-115">Saiva mais na seção [Acesso de membro](~/_csharplang/spec/expressions.md#member-access) na [especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3deea-115">For more information, see the [Member access](~/_csharplang/spec/expressions.md#member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3deea-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3deea-116">See also</span></span>

- [<span data-ttu-id="3deea-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3deea-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3deea-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3deea-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3deea-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3deea-119">C# Operators</span></span>](index.md)
- <span data-ttu-id="3deea-120">[Operadores ?. e ?[]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="3deea-120">[?. and ?[] operators](null-conditional-operators.md)</span></span>