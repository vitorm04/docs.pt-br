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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801888"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="a99fc-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a99fc-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="a99fc-103">A tabela a seguir mostra funções matemáticas intrínsecos que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="a99fc-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="a99fc-104">Você pode acessar as funções matemáticas intrínseco adicionando `Imports System.Math` ao seu arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="a99fc-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="a99fc-105">Função</span><span class="sxs-lookup"><span data-stu-id="a99fc-105">Function</span></span>|<span data-ttu-id="a99fc-106">Equivalentes derivadas</span><span class="sxs-lookup"><span data-stu-id="a99fc-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="a99fc-107">Secante (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-107">Secant (Sec(x))</span></span>|<span data-ttu-id="a99fc-108">1 / cos (x)</span><span class="sxs-lookup"><span data-stu-id="a99fc-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="a99fc-109">Cossecante (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="a99fc-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="a99fc-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="a99fc-111">Cotangente (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="a99fc-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="a99fc-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="a99fc-113">Seno inverso (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="a99fc-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="a99fc-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="a99fc-115">Cosseno inverso (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="a99fc-116">ATAN (-x / Sqrt (-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="a99fc-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="a99fc-117">Secante inversa (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="a99fc-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="a99fc-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="a99fc-119">Cossecante inversa (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="a99fc-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="a99fc-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="a99fc-121">Cotangente inversa (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="a99fc-122">2 \* Atan(1) - ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="a99fc-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="a99fc-123">Seno hiperbólico (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="a99fc-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="a99fc-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="a99fc-125">Cosseno hiperbólico (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="a99fc-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="a99fc-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="a99fc-127">Tangente hiperbólica (TANH</span><span class="sxs-lookup"><span data-stu-id="a99fc-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="a99fc-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="a99fc-129">Secante hiperbólico (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="a99fc-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="a99fc-131">Cossecante hiperbólico (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="a99fc-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="a99fc-133">Cotangente hiperbólica (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="a99fc-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="a99fc-135">Seno hiperbólico inverso (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="a99fc-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="a99fc-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="a99fc-137">Cosseno hiperbólico inverso (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="a99fc-138">Log(x + Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="a99fc-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="a99fc-139">Tangente hiperbólica (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="a99fc-140">Log((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="a99fc-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="a99fc-141">Secante hiperbólico inversa (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="a99fc-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="a99fc-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="a99fc-143">Cossecante hiperbólico inversa (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="a99fc-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="a99fc-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="a99fc-145">Cotangente hiperbólica inversa (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="a99fc-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="a99fc-146">Log((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="a99fc-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a99fc-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a99fc-147">See also</span></span>

- [<span data-ttu-id="a99fc-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="a99fc-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
