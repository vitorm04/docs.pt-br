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
# <a name="derived-math-functions-visual-basic"></a>Funções matemáticas derivadas (Visual Basic)
A tabela a seguir mostra funções matemáticas não intrínsecas que podem ser derivadas das funções matemáticas intrínsecas do objeto <xref:System.Math?displayProperty=nameWithType>. Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` ao seu arquivo ou projeto.  
  
|Função|Equivalentes derivados|  
|--------------|-------------------------|  
|Secante (s (x))|1/cos (x)|  
|Cossecante (CSC (x))|1/sin (x)|  
|Cotangente (ctan (x))|1/tan (x)|  
|Seno inverso (Asen (x))|ATAN (x/sqrt (-x * x + 1))|  
|Cosseno inverso (ACOS (x))|ATAN (-x/sqrt (-x * x + 1)) + 2 \* ATAN (1)|  
|Secante inversa (ASEC (x))|2 * ATAN (1) – ATAN (sinal (x)/sqrt (x \* x – 1))|  
|Cossecante inversa (acsc (x))|ATAN (sinal (x)/sqrt (x * x – 1))|  
|Cotangente inversa (ACOT (x))|2 * ATAN (1)-ATAN (x)|  
|Seno hiperbólico (sinh (x))|(Exp(x) – Exp(-x)) / 2|  
|Cosseno hiperbólico (cosh (x))|(Exp(x) + Exp(-x)) / 2|  
|Tangente hiperbólica (TANH (x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Secante Hiperbólica (sech (x))|2 / (Exp(x) + Exp(-x))|  
|Cossecante hiperbólica (csch (x))|2/(exp (x) – exp (-x))|  
|Cotangente hiperbólica (coth (x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Seno hiperbólico inverso (Asinh (x))|Log(x + Sqrt(x * x + 1))|  
|Cosseno hiperbólico inverso (ACOSH (x))|Log (x + sqrt (x * x – 1))|  
|Tangente hiperbólica inversa (ATANH (x))|Log ((1 + x)/(1 – x))/2|  
|Secante hiperbólica inversa (AsecH (x))|Log((Sqrt(-x * x + 1) + 1) / x)|  
|Cossecante hiperbólica inversa (Acsch (x))|Log ((sinal (x) * sqrt (x \* x + 1) + 1)/x)|  
|Cotangente hiperbólica inversa (Acoth (x))|Log ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>Consulte também

- [Funções Matemáticas](../../../visual-basic/language-reference/functions/math-functions.md)
