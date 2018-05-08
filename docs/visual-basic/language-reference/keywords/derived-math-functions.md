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
ms.openlocfilehash: 87faa623f5b145eec8b88e350fce4171125324dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="derived-math-functions-visual-basic"></a>Funções matemáticas derivadas (Visual Basic)
A tabela a seguir mostra funções matemáticas intrínsecos que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=nameWithType> objeto. Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` ao projeto ou arquivo.  
  
|Função|Equivalentes derivadas|  
|--------------|-------------------------|  
|Secante (Sec(x))|1 / cos (x)|  
|Cossecante (Csc(x))|1 / sin (x)|  
|Cotangente (Ctan(x))|1 / tan (x)|  
|Seno inverso (Asin(x))|ATAN (x / Sqrt (-x * x + 1))|  
|Cosseno inverso (Acos(x))|ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|Secante inversa (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))|  
|Cossecante inversa (Acsc(x))|ATAN(Sign(x) / Sqrt (x * x – 1))|  
|Cotangente inversa (Acot(x))|2 * Atan(1) - ATAN (x)|  
|Seno hiperbólico (Sinh(x))|(EXP (x) – Exp(-x)) / 2|  
|Cosseno hiperbólico (Cosh(x))|(EXP (x) + Exp(-x)) / 2|  
|Tangente hiperbólica (TANH|(EXP (x) – Exp(-x)) / (EXP (x) + Exp(-x))|  
|Secante hiperbólico (Sech(x))|2 / (EXP (x) + Exp(-x))|  
|Cossecante hiperbólico (Csch(x))|2 / (EXP (x) – Exp(-x))|  
|Cotangente hiperbólica (Coth(x))|(EXP (x) + Exp(-x)) / (EXP (x) – Exp(-x))|  
|Seno hiperbólico inverso (Asinh(x))|Log (x + Sqrt (x * x + 1))|  
|O cosseno hiperbólico inverso (Acosh(x))|Log (x + Sqrt (x * x – 1))|  
|Tangente hiperbólica inversa (Atanh(x))|Log ((1 + x) / (1 – x)) / 2|  
|Secante hiperbólico inversa (AsecH(x))|Log ((Sqrt (-x * x + 1) + 1) / x)|  
|Cossecante hiperbólico inversa (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)|  
|Cotangente hiperbólica inversa (Acoth(x))|Log ((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>Consulte também  
 [Funções Matemáticas](../../../visual-basic/language-reference/functions/math-functions.md)
