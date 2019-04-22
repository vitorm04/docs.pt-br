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
ms.openlocfilehash: 0d0606c52d1d50fcc2fd8eea3ad2851c95b18a69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836578"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="205f0-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="205f0-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="205f0-103">A tabela a seguir mostra funções matemáticas intrínsecos que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="205f0-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="205f0-104">Você pode acessar as funções matemáticas intrínseco adicionando `Imports System.Math` ao seu arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="205f0-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="205f0-105">Função</span><span class="sxs-lookup"><span data-stu-id="205f0-105">Function</span></span>|<span data-ttu-id="205f0-106">Equivalentes derivadas</span><span class="sxs-lookup"><span data-stu-id="205f0-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="205f0-107">Secante (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-107">Secant (Sec(x))</span></span>|<span data-ttu-id="205f0-108">1 / cos (x)</span><span class="sxs-lookup"><span data-stu-id="205f0-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="205f0-109">Cossecante (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="205f0-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="205f0-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="205f0-111">Cotangente (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="205f0-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="205f0-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="205f0-113">Seno inverso (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="205f0-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="205f0-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="205f0-115">Cosseno inverso (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="205f0-116">ATAN (-x / Sqrt (-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="205f0-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="205f0-117">Secante inversa (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="205f0-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="205f0-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="205f0-119">Cossecante inversa (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="205f0-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="205f0-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="205f0-121">Cotangente inversa (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="205f0-122">2 \* Atan(1) - ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="205f0-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="205f0-123">Seno hiperbólico (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="205f0-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="205f0-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="205f0-125">Cosseno hiperbólico (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="205f0-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="205f0-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="205f0-127">Tangente hiperbólica (TANH</span><span class="sxs-lookup"><span data-stu-id="205f0-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="205f0-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="205f0-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="205f0-129">Secante hiperbólico (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="205f0-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="205f0-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="205f0-131">Cossecante hiperbólico (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="205f0-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="205f0-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="205f0-133">Cotangente hiperbólica (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="205f0-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="205f0-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="205f0-135">Seno hiperbólico inverso (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="205f0-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="205f0-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="205f0-137">Cosseno hiperbólico inverso (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="205f0-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="205f0-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="205f0-139">Tangente hiperbólica (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="205f0-140">Log((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="205f0-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="205f0-141">Secante hiperbólico inversa (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="205f0-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="205f0-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="205f0-143">Cossecante hiperbólico inversa (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="205f0-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="205f0-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="205f0-145">Cotangente hiperbólica inversa (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="205f0-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="205f0-146">Log((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="205f0-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="205f0-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="205f0-147">See also</span></span>

- [<span data-ttu-id="205f0-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="205f0-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
