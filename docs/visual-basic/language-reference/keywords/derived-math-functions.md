---
title: "Fun&#231;&#245;es matem&#225;ticas derivadas (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ângulos"
  - "Função arccosecant"
  - "Função arccosine"
  - "Função arccotangent"
  - "Função arcsecant"
  - "Função arcsine"
  - "operações aritméticas, funções matemáticas derivadas"
  - "Função cosecant"
  - "Função cotangent"
  - "graus"
  - "funções matemáticas derivadas"
  - "funções [Visual Basic], funções matemáticas derivadas"
  - "Funções hiperbólicas"
  - "Funções inversas"
  - "logaritmos"
  - "funções matemáticas, derivado"
  - "Função secant"
  - "Funções trigonométricas"
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fun&#231;&#245;es matem&#225;ticas derivadas (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela a seguir mostra as funções matemáticas não intrínsecas que podem ser derivadas de funções matemáticas intrínsecas da <xref:System.Math?displayProperty=fullName> objeto.  Você pode acessar as funções matemáticas intrínsecas adicionando `Imports System.Math` em seu arquivo ou projeto.  
  
|Função|Equivalentes derivadas|  
|------------|----------------------------|  
|Secante \(Sec\(x\)\)|1 \/ Cos\(x\)|  
|Cossecante \(CSC\(x\)\)|1 \/ Sin\(x\)|  
|Cotangente \(Ctan\(x\)\)|1 \/ Tan\(x\)|  
|Arcoseno \(ASIN\(x\)\)|Atan\(x \/ Sqrt\(\-x \* x \+ 1\)\)|  
|Arcocosseno\(ACOS\(x\)\)|Atan\(\-x \/ Sqrt\(\-x \* x \+ 1\)\) \+ 2 \* Atan\(1\)|  
|Arcosecante \(Asec\(x\)\)|2 \* Atan\(1\) – Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|Arcocosecante \(Acsc\(x\)\)|Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|Arcotangente \(Acot\(x\)\)|2 \* Atan\(1\) \- Atan\(x\)|  
|Seno hiperbólico \(SINH\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ 2|  
|Cosseno hiperbólico \(COSH\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ 2|  
|Tangente hiperbólica \(TANH\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|Secante hiperbólica \(Sech\(x\)\)|2 \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|Cosecante hiperbólica \(Csch\(x\)\)|2 \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|Cotangente hiperbólica \(Coth\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|Arcoseno hiperbólico  \(Asinh\(x\)\)|Log\(x \+ Sqrt\(x \* x \+ 1\)\)|  
|Arcocosseno hiperbólico \(ACOSH\(x\)\)|Log\(x \+ Sqrt\(x \* x – 1\)\)|  
|Arcotangente hiperbólica \(ATANH\(x\)\)|Log\(\(1 \+ x\) \/ \(1 – x\)\) \/ 2|  
|Arcosecante hiperbólico\(AsecH\(x\)\)|Log\(\(Sqrt\(\-x \* x \+ 1\) \+ 1\) \/ x\)|  
|Arcocosecante hiperbólico\(Acsch\(x\)\)|Log\(\(Sign\(x\) \* Sqrt\(x \* x \+ 1\) \+ 1\) \/ x\)|  
|Arcocotangente hiperbólica\(Acoth\(x\)\)|Log\(\(x \+ 1\) \/ \(x – 1\)\) \/ 2|  
  
## Consulte também  
 [Funções matemáticas](../../../visual-basic/language-reference/functions/math-functions.md)