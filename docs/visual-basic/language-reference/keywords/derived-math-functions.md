---
title: Funções Matemáticas Derivadas
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
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373869"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="24304-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24304-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="24304-103">A tabela a seguir mostra funções matemáticas não intrínsecas que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="24304-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="24304-104">Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` ao seu arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="24304-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="24304-105">Função</span><span class="sxs-lookup"><span data-stu-id="24304-105">Function</span></span>|<span data-ttu-id="24304-106">Equivalentes derivados</span><span class="sxs-lookup"><span data-stu-id="24304-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="24304-107">Secante (s (x))</span><span class="sxs-lookup"><span data-stu-id="24304-107">Secant (Sec(x))</span></span>|<span data-ttu-id="24304-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="24304-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="24304-109">Cossecante (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="24304-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="24304-110">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="24304-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="24304-111">Cotangente (ctan (x))</span><span class="sxs-lookup"><span data-stu-id="24304-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="24304-112">1/tan (x)</span><span class="sxs-lookup"><span data-stu-id="24304-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="24304-113">Seno inverso (Asen (x))</span><span class="sxs-lookup"><span data-stu-id="24304-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="24304-114">ATAN (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="24304-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="24304-115">Cosseno inverso (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="24304-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="24304-116">ATAN (-x/sqrt (-x \* x + 1)) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="24304-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="24304-117">Secante inversa (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="24304-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="24304-118">2 \* ATAN (1) – ATAN (sinal (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="24304-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="24304-119">Cossecante inversa (acsc (x))</span><span class="sxs-lookup"><span data-stu-id="24304-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="24304-120">ATAN (sinal (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="24304-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="24304-121">Cotangente inversa (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="24304-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="24304-122">2 \* ATAN (1)-ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="24304-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="24304-123">Seno hiperbólico (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="24304-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="24304-124">(Exp (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="24304-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="24304-125">Cosseno hiperbólico (cosh (x))</span><span class="sxs-lookup"><span data-stu-id="24304-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="24304-126">(Exp (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="24304-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="24304-127">Tangente hiperbólica (TANH (x))</span><span class="sxs-lookup"><span data-stu-id="24304-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="24304-128">(Exp (x) – exp (-x))/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="24304-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="24304-129">Secante Hiperbólica (sech (x))</span><span class="sxs-lookup"><span data-stu-id="24304-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="24304-130">2/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="24304-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="24304-131">Cossecante hiperbólica (csch (x))</span><span class="sxs-lookup"><span data-stu-id="24304-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="24304-132">2/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="24304-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="24304-133">Cotangente hiperbólica (coth (x))</span><span class="sxs-lookup"><span data-stu-id="24304-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="24304-134">(Exp (x) + exp (-x))/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="24304-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="24304-135">Seno hiperbólico inverso (Asinh (x))</span><span class="sxs-lookup"><span data-stu-id="24304-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="24304-136">Log (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="24304-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="24304-137">Cosseno hiperbólico inverso (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="24304-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="24304-138">Log (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="24304-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="24304-139">Tangente hiperbólica inversa (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="24304-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="24304-140">Log ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="24304-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="24304-141">Secante hiperbólica inversa (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="24304-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="24304-142">Log ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="24304-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="24304-143">Cossecante hiperbólica inversa (Acsch (x))</span><span class="sxs-lookup"><span data-stu-id="24304-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="24304-144">Log ((sinal (x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="24304-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="24304-145">Cotangente hiperbólica inversa (Acoth (x))</span><span class="sxs-lookup"><span data-stu-id="24304-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="24304-146">Log ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="24304-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24304-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="24304-147">See also</span></span>

- [<span data-ttu-id="24304-148">Funções matemáticas</span><span class="sxs-lookup"><span data-stu-id="24304-148">Math Functions</span></span>](../functions/math-functions.md)
