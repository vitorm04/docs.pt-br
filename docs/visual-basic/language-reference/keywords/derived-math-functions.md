---
title: Funções matemáticas derivadas
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
ms.openlocfilehash: 73cf56dd72f2baac0474d6f5c4e88228a1fe38cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349845"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="f750c-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f750c-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="f750c-103">A tabela a seguir mostra funções matemáticas não intrínsecas que podem ser derivadas das funções matemáticas intrínsecas do objeto <xref:System.Math?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f750c-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="f750c-104">Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` ao seu arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="f750c-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="f750c-105">Função</span><span class="sxs-lookup"><span data-stu-id="f750c-105">Function</span></span>|<span data-ttu-id="f750c-106">Equivalentes derivados</span><span class="sxs-lookup"><span data-stu-id="f750c-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="f750c-107">Secante (s (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-107">Secant (Sec(x))</span></span>|<span data-ttu-id="f750c-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="f750c-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="f750c-109">Cossecante (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="f750c-110">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="f750c-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="f750c-111">Cotangente (ctan (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="f750c-112">1/tan (x)</span><span class="sxs-lookup"><span data-stu-id="f750c-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="f750c-113">Seno inverso (Asen (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="f750c-114">ATAN (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="f750c-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="f750c-115">Cosseno inverso (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="f750c-116">ATAN (-x/sqrt (-x \* x + 1)) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="f750c-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="f750c-117">Secante inversa (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="f750c-118">2 \* ATAN (1) – ATAN (sinal (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="f750c-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="f750c-119">Cossecante inversa (acsc (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="f750c-120">ATAN (sinal (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="f750c-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="f750c-121">Cotangente inversa (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="f750c-122">2 \* ATAN (1)-ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="f750c-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="f750c-123">Seno hiperbólico (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="f750c-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="f750c-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="f750c-125">Cosseno hiperbólico (cosh (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="f750c-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="f750c-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="f750c-127">Tangente hiperbólica (TANH (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="f750c-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="f750c-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="f750c-129">Secante Hiperbólica (sech (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="f750c-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="f750c-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="f750c-131">Cossecante hiperbólica (csch (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="f750c-132">2/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="f750c-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="f750c-133">Cotangente hiperbólica (coth (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="f750c-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="f750c-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="f750c-135">Seno hiperbólico inverso (Asinh (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="f750c-136">Log(x + Sqrt(x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="f750c-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="f750c-137">Cosseno hiperbólico inverso (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="f750c-138">Log (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="f750c-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="f750c-139">Tangente hiperbólica inversa (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="f750c-140">Log ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="f750c-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="f750c-141">Secante hiperbólica inversa (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="f750c-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="f750c-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="f750c-143">Cossecante hiperbólica inversa (Acsch (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="f750c-144">Log ((sinal (x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="f750c-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="f750c-145">Cotangente hiperbólica inversa (Acoth (x))</span><span class="sxs-lookup"><span data-stu-id="f750c-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="f750c-146">Log ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="f750c-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f750c-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f750c-147">See also</span></span>

- [<span data-ttu-id="f750c-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="f750c-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
