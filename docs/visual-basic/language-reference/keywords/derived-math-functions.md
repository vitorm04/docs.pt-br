---
title: "Funções matemáticas derivadas (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="1cda5-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cda5-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="1cda5-103">A tabela a seguir mostra funções matemáticas intrínsecos que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="1cda5-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="1cda5-104">Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` ao projeto ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="1cda5-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="1cda5-105">Função</span><span class="sxs-lookup"><span data-stu-id="1cda5-105">Function</span></span>|<span data-ttu-id="1cda5-106">Equivalentes derivadas</span><span class="sxs-lookup"><span data-stu-id="1cda5-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="1cda5-107">Secante (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-107">Secant (Sec(x))</span></span>|<span data-ttu-id="1cda5-108">1 / cos (x)</span><span class="sxs-lookup"><span data-stu-id="1cda5-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="1cda5-109">Cossecante (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="1cda5-110">1 / sin (x)</span><span class="sxs-lookup"><span data-stu-id="1cda5-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="1cda5-111">Cotangente (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="1cda5-112">1 / tan (x)</span><span class="sxs-lookup"><span data-stu-id="1cda5-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="1cda5-113">Seno inverso (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="1cda5-114">ATAN (x / Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="1cda5-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="1cda5-115">Cosseno inverso (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="1cda5-116">ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="1cda5-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="1cda5-117">Secante inversa (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="1cda5-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="1cda5-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="1cda5-119">Cossecante inversa (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="1cda5-120">ATAN(Sign(x) / Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="1cda5-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="1cda5-121">Cotangente inversa (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="1cda5-122">2 * Atan(1) - ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="1cda5-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="1cda5-123">Seno hiperbólico (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="1cda5-124">(EXP (x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="1cda5-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="1cda5-125">Cosseno hiperbólico (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="1cda5-126">(EXP (x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="1cda5-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="1cda5-127">Tangente hiperbólica (TANH</span><span class="sxs-lookup"><span data-stu-id="1cda5-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="1cda5-128">(EXP (x) – Exp(-x)) / (EXP (x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="1cda5-129">Secante hiperbólico (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="1cda5-130">2 / (EXP (x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="1cda5-131">Cossecante hiperbólico (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="1cda5-132">2 / (EXP (x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="1cda5-133">Cotangente hiperbólica (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="1cda5-134">(EXP (x) + Exp(-x)) / (EXP (x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="1cda5-135">Seno hiperbólico inverso (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="1cda5-136">Log (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="1cda5-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="1cda5-137">O cosseno hiperbólico inverso (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="1cda5-138">Log (x + Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="1cda5-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="1cda5-139">Tangente hiperbólica inversa (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="1cda5-140">Log ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="1cda5-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="1cda5-141">Secante hiperbólico inversa (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="1cda5-142">Log ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="1cda5-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="1cda5-143">Cossecante hiperbólico inversa (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="1cda5-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="1cda5-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="1cda5-145">Cotangente hiperbólica inversa (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="1cda5-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="1cda5-146">Log ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="1cda5-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cda5-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cda5-147">See Also</span></span>  
 [<span data-ttu-id="1cda5-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="1cda5-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
