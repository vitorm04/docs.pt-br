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
ms.openlocfilehash: f84b1ef18ef2a924bb2e47da85ecbb51f982873a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869025"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="43207-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43207-102">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="43207-103">A tabela a seguir mostra funções matemáticas não intrínsecas que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="43207-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="43207-104">Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` ao seu arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="43207-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="43207-105">Função</span><span class="sxs-lookup"><span data-stu-id="43207-105">Function</span></span>|<span data-ttu-id="43207-106">Equivalentes derivados</span><span class="sxs-lookup"><span data-stu-id="43207-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="43207-107">Secante (s (x))</span><span class="sxs-lookup"><span data-stu-id="43207-107">Secant (Sec(x))</span></span>|<span data-ttu-id="43207-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="43207-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="43207-109">Cossecante (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="43207-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="43207-110">1/sin (x)</span><span class="sxs-lookup"><span data-stu-id="43207-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="43207-111">Cotangente (ctan (x))</span><span class="sxs-lookup"><span data-stu-id="43207-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="43207-112">1/tan (x)</span><span class="sxs-lookup"><span data-stu-id="43207-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="43207-113">Seno inverso (Asen (x))</span><span class="sxs-lookup"><span data-stu-id="43207-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="43207-114">ATAN (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="43207-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="43207-115">Cosseno inverso (ACOS (x))</span><span class="sxs-lookup"><span data-stu-id="43207-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="43207-116">ATAN (-x/sqrt (-x \* x + 1)) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="43207-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="43207-117">Secante inversa (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="43207-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="43207-118">2 \* ATAN (1) – ATAN (sinal (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="43207-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="43207-119">Cossecante inversa (acsc (x))</span><span class="sxs-lookup"><span data-stu-id="43207-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="43207-120">ATAN (sinal (x)/sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="43207-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="43207-121">Cotangente inversa (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="43207-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="43207-122">2 \* ATAN (1)-ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="43207-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="43207-123">Seno hiperbólico (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="43207-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="43207-124">(Exp (x) – exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="43207-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="43207-125">Cosseno hiperbólico (cosh (x))</span><span class="sxs-lookup"><span data-stu-id="43207-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="43207-126">(Exp (x) + exp (-x))/2</span><span class="sxs-lookup"><span data-stu-id="43207-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="43207-127">Tangente hiperbólica (TANH (x))</span><span class="sxs-lookup"><span data-stu-id="43207-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="43207-128">(Exp (x) – exp (-x))/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="43207-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="43207-129">Secante Hiperbólica (sech (x))</span><span class="sxs-lookup"><span data-stu-id="43207-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="43207-130">2/(exp (x) + exp (-x))</span><span class="sxs-lookup"><span data-stu-id="43207-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="43207-131">Cossecante hiperbólica (csch (x))</span><span class="sxs-lookup"><span data-stu-id="43207-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="43207-132">2/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="43207-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="43207-133">Cotangente hiperbólica (coth (x))</span><span class="sxs-lookup"><span data-stu-id="43207-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="43207-134">(Exp (x) + exp (-x))/(exp (x) – exp (-x))</span><span class="sxs-lookup"><span data-stu-id="43207-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="43207-135">Seno hiperbólico inverso (Asinh (x))</span><span class="sxs-lookup"><span data-stu-id="43207-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="43207-136">Log (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="43207-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="43207-137">Cosseno hiperbólico inverso (ACOSH (x))</span><span class="sxs-lookup"><span data-stu-id="43207-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="43207-138">Log (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="43207-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="43207-139">Tangente hiperbólica inversa (ATANH (x))</span><span class="sxs-lookup"><span data-stu-id="43207-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="43207-140">Log ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="43207-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="43207-141">Secante hiperbólica inversa (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="43207-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="43207-142">Log ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="43207-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="43207-143">Cossecante hiperbólica inversa (Acsch (x))</span><span class="sxs-lookup"><span data-stu-id="43207-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="43207-144">Log ((sinal (x) \* sqrt (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="43207-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="43207-145">Cotangente hiperbólica inversa (Acoth (x))</span><span class="sxs-lookup"><span data-stu-id="43207-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="43207-146">Log ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="43207-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43207-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="43207-147">See also</span></span>

- [<span data-ttu-id="43207-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="43207-148">Math Functions</span></span>](../functions/math-functions.md)
