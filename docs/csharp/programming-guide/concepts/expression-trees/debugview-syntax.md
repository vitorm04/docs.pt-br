---
title: Sintaxe usada pela propriedade DebugView (C#)
description: Descreve a sintaxe especial usada pela propriedade DebugView para produzir uma representação de cadeia de caracteres de árvores de expressão
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: de82a738430cdd37c4905a5ae7da5faeb46f00a4
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196362"
---
# <a name="debugview-syntax"></a><span data-ttu-id="30046-103">Sintaxe de `DebugView`</span><span class="sxs-lookup"><span data-stu-id="30046-103">`DebugView` syntax</span></span>

<span data-ttu-id="30046-104">A propriedade `DebugView` (disponível apenas durante a depuração) fornece uma renderização de cadeia de caracteres de árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="30046-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="30046-105">A maior parte da sintaxe é bastante simples de entender; os casos especiais são descritos nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="30046-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="30046-106">Cada exemplo é seguido por um comentário de bloco, que contém `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="30046-106">Each example is followed by a block comment, containing the `DebugView`.</span></span> 

## <a name="parameterexpression"></a><span data-ttu-id="30046-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="30046-107">ParameterExpression</span></span> 

<span data-ttu-id="30046-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> os nomes de variáveis são exibidos com o símbolo `$` no início.</span><span class="sxs-lookup"><span data-stu-id="30046-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>
  
<span data-ttu-id="30046-109">Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="30046-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>
  
### <a name="examples"></a><span data-ttu-id="30046-110">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30046-110">Examples</span></span>

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a><span data-ttu-id="30046-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="30046-111">ConstantExpression</span></span>  

<span data-ttu-id="30046-112">Para objetos <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.</span><span class="sxs-lookup"><span data-stu-id="30046-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
<span data-ttu-id="30046-113">Para tipos numéricos que têm sufixos padrão como literais de C#, o sufixo é adicionado ao valor.</span><span class="sxs-lookup"><span data-stu-id="30046-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="30046-114">A tabela a seguir mostra os sufixos associados com vários tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="30046-114">The following table shows the suffixes associated with various numeric types.</span></span>  

| <span data-ttu-id="30046-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="30046-115">Type</span></span> | <span data-ttu-id="30046-116">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="30046-116">Keyword</span></span> | <span data-ttu-id="30046-117">Sufixo</span><span class="sxs-lookup"><span data-stu-id="30046-117">Suffix</span></span> |  
|--|--|--|  
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="30046-118">uint</span><span class="sxs-lookup"><span data-stu-id="30046-118">uint</span></span>](../../../language-reference/keywords/uint.md) | <span data-ttu-id="30046-119">U</span><span class="sxs-lookup"><span data-stu-id="30046-119">U</span></span> |  
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="30046-120">long</span><span class="sxs-lookup"><span data-stu-id="30046-120">long</span></span>](../../../language-reference/keywords/long.md) | <span data-ttu-id="30046-121">L</span><span class="sxs-lookup"><span data-stu-id="30046-121">L</span></span> |  
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="30046-122">ulong</span><span class="sxs-lookup"><span data-stu-id="30046-122">ulong</span></span>](../../../language-reference/keywords/ulong.md) | <span data-ttu-id="30046-123">UL</span><span class="sxs-lookup"><span data-stu-id="30046-123">UL</span></span> |  
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="30046-124">double</span><span class="sxs-lookup"><span data-stu-id="30046-124">double</span></span>](../../../language-reference/keywords/double.md) | <span data-ttu-id="30046-125">D</span><span class="sxs-lookup"><span data-stu-id="30046-125">D</span></span> |  
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="30046-126">float</span><span class="sxs-lookup"><span data-stu-id="30046-126">float</span></span>](../../../language-reference/keywords/float.md) | <span data-ttu-id="30046-127">F</span><span class="sxs-lookup"><span data-stu-id="30046-127">F</span></span> |  
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="30046-128">decimal</span><span class="sxs-lookup"><span data-stu-id="30046-128">decimal</span></span>](../../../language-reference/keywords/decimal.md) | <span data-ttu-id="30046-129">M</span><span class="sxs-lookup"><span data-stu-id="30046-129">M</span></span> |  
  
### <a name="examples"></a><span data-ttu-id="30046-130">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30046-130">Examples</span></span>  

```csharp
int num = 10; 
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10; 
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a><span data-ttu-id="30046-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="30046-131">BlockExpression</span></span>
 
<span data-ttu-id="30046-132">Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> difere do tipo da última expressão no bloco, o tipo será exibido entre colchetes angulares (`<` e `>`).</span><span class="sxs-lookup"><span data-stu-id="30046-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="30046-133">Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.</span><span class="sxs-lookup"><span data-stu-id="30046-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="30046-134">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30046-134">Examples</span></span>  

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a><span data-ttu-id="30046-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="30046-135">LambdaExpression</span></span>

<span data-ttu-id="30046-136">Objetos <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> são exibidos junto com seus tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="30046-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>
  
<span data-ttu-id="30046-137">Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="30046-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>
  
### <a name="examples"></a><span data-ttu-id="30046-138">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30046-138">Examples</span></span>

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```
  
## <a name="labelexpression"></a><span data-ttu-id="30046-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="30046-139">LabelExpression</span></span>

<span data-ttu-id="30046-140">Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30046-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>
  
<span data-ttu-id="30046-141">O token `.Label` indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="30046-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="30046-142">O token `.LabelTarget` indica o local para o qual o destino deve saltar.</span><span class="sxs-lookup"><span data-stu-id="30046-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>
  
<span data-ttu-id="30046-143">Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="30046-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>
  
### <a name="examples"></a><span data-ttu-id="30046-144">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30046-144">Examples</span></span>

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```
  
## <a name="checked-operators"></a><span data-ttu-id="30046-145">Operadores verificados</span><span class="sxs-lookup"><span data-stu-id="30046-145">Checked Operators</span></span>  

<span data-ttu-id="30046-146">Os operadores verificados são exibidos com o símbolo `#` na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="30046-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="30046-147">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="30046-147">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="30046-148">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30046-148">Examples</span></span>  

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```