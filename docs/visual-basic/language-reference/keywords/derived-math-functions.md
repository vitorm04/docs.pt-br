---
title: Funções matemáticas derivadas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: 1273871faf65afdd1a894c03f13a2c93507c1b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505855"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="ceb1c-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="ceb1c-103">A tabela a seguir mostra funções matemáticas intrínsecos que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="ceb1c-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="ceb1c-104">Você pode acessar as funções matemáticas intrínseco adicionando `Imports System.Math` ao seu arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="ceb1c-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="ceb1c-105">Função</span><span class="sxs-lookup"><span data-stu-id="ceb1c-105">Function</span></span>|<span data-ttu-id="ceb1c-106">Equivalentes derivadas</span><span class="sxs-lookup"><span data-stu-id="ceb1c-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="ceb1c-107">Secante (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-107">Secant (Sec(x))</span></span>|<span data-ttu-id="ceb1c-108">1 / cos (x)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="ceb1c-109">Cossecante (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="ceb1c-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="ceb1c-111">Cotangente (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="ceb1c-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="ceb1c-113">Seno inverso (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="ceb1c-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="ceb1c-115">Cosseno inverso (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="ceb1c-116">ATAN (-x / Sqrt (-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="ceb1c-117">Secante inversa (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="ceb1c-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ceb1c-119">Cossecante inversa (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="ceb1c-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ceb1c-121">Cotangente inversa (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="ceb1c-122">2 \* Atan(1) - ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="ceb1c-123">Seno hiperbólico (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="ceb1c-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ceb1c-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ceb1c-125">Cosseno hiperbólico (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="ceb1c-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ceb1c-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="ceb1c-127">Tangente hiperbólica (TANH</span><span class="sxs-lookup"><span data-stu-id="ceb1c-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="ceb1c-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ceb1c-129">Secante hiperbólico (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="ceb1c-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="ceb1c-131">Cossecante hiperbólico (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="ceb1c-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ceb1c-133">Cotangente hiperbólica (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="ceb1c-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="ceb1c-135">Seno hiperbólico inverso (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="ceb1c-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="ceb1c-137">Cosseno hiperbólico inverso (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="ceb1c-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="ceb1c-139">Tangente hiperbólica (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="ceb1c-140">Log((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="ceb1c-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="ceb1c-141">Secante hiperbólico inversa (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="ceb1c-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ceb1c-143">Cossecante hiperbólico inversa (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="ceb1c-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="ceb1c-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="ceb1c-145">Cotangente hiperbólica inversa (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="ceb1c-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="ceb1c-146">Log((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="ceb1c-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceb1c-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceb1c-147">See also</span></span>
- [<span data-ttu-id="ceb1c-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="ceb1c-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
