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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 833b91ba11111c4a9513ed96fbdd783150283768
ms.lasthandoff: 03/13/2017

---
# <a name="derived-math-functions-visual-basic"></a>Funções matemáticas derivadas (Visual Basic)
A tabela a seguir mostra funções matemáticas não-intrínsecas que podem ser derivadas das funções matemáticas intrínsecas do <xref:System.Math?displayProperty=fullName>objeto.</xref:System.Math?displayProperty=fullName> Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` para o arquivo ou projeto.  
  
|Função|Derivada equivalentes|  
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
|Cosseno hiperbólico inverso (Acosh(x))|Log (x + Sqrt (x * x – 1))|  
|Tangente hiperbólica inversa (Atanh(x))|Log ((1 + x) / (1 – x)) / 2|  
|Secante hiperbólico inversa (AsecH(x))|Log ((Sqrt (-x * x + 1) + 1) / x)|  
|Cossecante hiperbólico inversa (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)|  
|Cotangente hiperbólica inversa (Acoth(x))|Log ((x + 1) /x (– 1)) / 2|  
  
## <a name="see-also"></a>Consulte também  
 [Funções Matemáticas](../../../visual-basic/language-reference/functions/math-functions.md)
