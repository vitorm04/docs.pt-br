---
title: "Derivado de funções matemáticas (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c5ef3849e4e3ff0a83bd90f1f0313896fb47fb29
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="95cd9-102">Funções matemáticas derivadas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95cd9-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="95cd9-103">A tabela a seguir mostra funções matemáticas não-intrínsecas que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=fullName>objeto.</xref:System.Math?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="95cd9-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=fullName> object.</span></span> <span data-ttu-id="95cd9-104">Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` para o arquivo ou projeto.</span><span class="sxs-lookup"><span data-stu-id="95cd9-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="95cd9-105">Função</span><span class="sxs-lookup"><span data-stu-id="95cd9-105">Function</span></span>|<span data-ttu-id="95cd9-106">Derivada equivalentes</span><span class="sxs-lookup"><span data-stu-id="95cd9-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="95cd9-107">Secante (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-107">Secant (Sec(x))</span></span>|<span data-ttu-id="95cd9-108">1 / cos (x)</span><span class="sxs-lookup"><span data-stu-id="95cd9-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="95cd9-109">Cossecante (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="95cd9-110">1 / sin (x)</span><span class="sxs-lookup"><span data-stu-id="95cd9-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="95cd9-111">Cotangente (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="95cd9-112">1 / tan (x)</span><span class="sxs-lookup"><span data-stu-id="95cd9-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="95cd9-113">Seno inverso (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="95cd9-114">ATAN (x / Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="95cd9-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="95cd9-115">Cosseno inverso (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="95cd9-116">ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="95cd9-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="95cd9-117">Secante inversa (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="95cd9-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="95cd9-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="95cd9-119">Cossecante inversa (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="95cd9-120">ATAN(Sign(x) / Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="95cd9-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="95cd9-121">Cotangente inversa (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="95cd9-122">2 * Atan(1) - ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="95cd9-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="95cd9-123">Seno hiperbólico (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="95cd9-124">(EXP (x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="95cd9-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="95cd9-125">Cosseno hiperbólico (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="95cd9-126">(EXP (x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="95cd9-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="95cd9-127">Tangente hiperbólica (TANH</span><span class="sxs-lookup"><span data-stu-id="95cd9-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="95cd9-128">(EXP (x) – Exp(-x)) / (EXP (x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="95cd9-129">Secante hiperbólico (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="95cd9-130">2 / (EXP (x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="95cd9-131">Cossecante hiperbólico (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="95cd9-132">2 / (EXP (x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="95cd9-133">Cotangente hiperbólica (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="95cd9-134">(EXP (x) + Exp(-x)) / (EXP (x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="95cd9-135">Seno hiperbólico inverso (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="95cd9-136">Log (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="95cd9-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="95cd9-137">Cosseno hiperbólico inverso (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="95cd9-138">Log (x + Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="95cd9-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="95cd9-139">Tangente hiperbólica inversa (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="95cd9-140">Log ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="95cd9-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="95cd9-141">Secante hiperbólico inversa (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="95cd9-142">Log ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="95cd9-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="95cd9-143">Cossecante hiperbólico inversa (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="95cd9-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="95cd9-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="95cd9-145">Cotangente hiperbólica inversa (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="95cd9-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="95cd9-146">Log ((x + 1) /x (– 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="95cd9-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95cd9-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95cd9-147">See Also</span></span>  
 [<span data-ttu-id="95cd9-148">Funções Matemáticas</span><span class="sxs-lookup"><span data-stu-id="95cd9-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
