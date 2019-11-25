---
title: Syntax used by DebugView property
description: Descreve a sintaxe especial usada pela propriedade DebugView para produzir uma representação de cadeia de caracteres de árvores de expressão
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 98ceba37aa226fab68ae1c1028e2a1139b3b8e7e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346878"
---
# <a name="debugview-syntax"></a><span data-ttu-id="c6f8e-103">Sintaxe de `DebugView`</span><span class="sxs-lookup"><span data-stu-id="c6f8e-103">`DebugView` syntax</span></span>

<span data-ttu-id="c6f8e-104">A propriedade `DebugView` (disponível apenas durante a depuração) fornece uma renderização de cadeia de caracteres de árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="c6f8e-105">A maior parte da sintaxe é bastante simples de entender; os casos especiais são descritos nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="c6f8e-106">Each example is followed by a comment block containing the `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-106">Each example is followed by a comment block containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="c6f8e-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="c6f8e-107">ParameterExpression</span></span>

<span data-ttu-id="c6f8e-108">Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> são exibidos com o símbolo "$" no início.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="c6f8e-109">Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="c6f8e-110">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6f8e-110">Examples</span></span>

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a><span data-ttu-id="c6f8e-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="c6f8e-111">ConstantExpressions</span></span>

<span data-ttu-id="c6f8e-112">Para objetos <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="c6f8e-113">For some numeric types, a suffix is added to the value:</span><span class="sxs-lookup"><span data-stu-id="c6f8e-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="c6f8e-114">Digite</span><span class="sxs-lookup"><span data-stu-id="c6f8e-114">Type</span></span> | <span data-ttu-id="c6f8e-115">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="c6f8e-115">Keyword</span></span> | <span data-ttu-id="c6f8e-116">Sufixo</span><span class="sxs-lookup"><span data-stu-id="c6f8e-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="c6f8e-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="c6f8e-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="c6f8e-118">U</span><span class="sxs-lookup"><span data-stu-id="c6f8e-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="c6f8e-119">Long</span><span class="sxs-lookup"><span data-stu-id="c6f8e-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="c6f8e-120">L</span><span class="sxs-lookup"><span data-stu-id="c6f8e-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="c6f8e-121">ULong</span><span class="sxs-lookup"><span data-stu-id="c6f8e-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="c6f8e-122">UL</span><span class="sxs-lookup"><span data-stu-id="c6f8e-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="c6f8e-123">Duplo</span><span class="sxs-lookup"><span data-stu-id="c6f8e-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="c6f8e-124">D</span><span class="sxs-lookup"><span data-stu-id="c6f8e-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="c6f8e-125">Simples</span><span class="sxs-lookup"><span data-stu-id="c6f8e-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="c6f8e-126">F</span><span class="sxs-lookup"><span data-stu-id="c6f8e-126">F</span></span> |
| <xref:System.Decimal> | [<span data-ttu-id="c6f8e-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="c6f8e-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="c6f8e-128">M</span><span class="sxs-lookup"><span data-stu-id="c6f8e-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="c6f8e-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6f8e-129">Examples</span></span>

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a><span data-ttu-id="c6f8e-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="c6f8e-130">BlockExpression</span></span>

<span data-ttu-id="c6f8e-131">Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> difere do tipo da última expressão no bloco, o tipo será exibido entre colchetes angulares (`<` e `>`).</span><span class="sxs-lookup"><span data-stu-id="c6f8e-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="c6f8e-132">Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="c6f8e-133">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6f8e-133">Examples</span></span>

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a><span data-ttu-id="c6f8e-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="c6f8e-134">LambdaExpression</span></span>

<span data-ttu-id="c6f8e-135">Objetos <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> são exibidos junto com seus tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="c6f8e-136">Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="c6f8e-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6f8e-137">Examples</span></span>

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a><span data-ttu-id="c6f8e-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="c6f8e-138">LabelExpression</span></span>

<span data-ttu-id="c6f8e-139">Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="c6f8e-140">O token `.Label` indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="c6f8e-141">O token `.LabelTarget` indica o local para o qual o destino deve saltar.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="c6f8e-142">Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="c6f8e-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6f8e-143">Examples</span></span>

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a><span data-ttu-id="c6f8e-144">Operadores verificados</span><span class="sxs-lookup"><span data-stu-id="c6f8e-144">Checked Operators</span></span>

<span data-ttu-id="c6f8e-145">Os operadores verificados são exibidos com o símbolo `#` na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="c6f8e-146">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="c6f8e-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="c6f8e-147">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6f8e-147">Examples</span></span>

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
