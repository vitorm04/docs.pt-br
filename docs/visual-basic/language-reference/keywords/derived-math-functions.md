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
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836578"
---
# <a name="derived-math-functions-visual-basic"></a>Funções matemáticas derivadas (Visual Basic)
A tabela a seguir mostra funções matemáticas intrínsecos que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto. Você pode acessar as funções matemáticas intrínseco adicionando `Imports System.Math` ao seu arquivo ou projeto.  
  
|Função|Equivalentes derivadas|  
|--------------|-------------------------|  
|Secante (Sec(x))|1 / cos (x)|  
|Cossecante (Csc(x))|1 / Sin(x)|  
|Cotangente (Ctan(x))|1 / Tan(x)|  
|Seno inverso (Asin(x))|Atan(x / Sqrt(-x * x + 1))|  
|Cosseno inverso (Acos(x))|ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|Secante inversa (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))|  
|Cossecante inversa (Acsc(x))|Atan(Sign(x) / Sqrt(x * x – 1))|  
|Cotangente inversa (Acot(x))|2 * Atan(1) - ATAN (x)|  
|Seno hiperbólico (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|Cosseno hiperbólico (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|Tangente hiperbólica (TANH|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Secante hiperbólico (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Cossecante hiperbólico (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|Cotangente hiperbólica (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Seno hiperbólico inverso (Asinh(x))|Log(x + Sqrt(x * x + 1))|  
|Cosseno hiperbólico inverso (Acosh(x))|Log(x + Sqrt(x * x – 1))|  
|Tangente hiperbólica (Atanh(x))|Log((1 + x) / (1 – x)) / 2|  
|Secante hiperbólico inversa (AsecH(x))|Log((Sqrt(-x * x + 1) + 1) / x)|  
|Cossecante hiperbólico inversa (Acsch(x))|Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)|  
|Cotangente hiperbólica inversa (Acoth(x))|Log((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>Consulte também

- [Funções Matemáticas](../../../visual-basic/language-reference/functions/math-functions.md)
