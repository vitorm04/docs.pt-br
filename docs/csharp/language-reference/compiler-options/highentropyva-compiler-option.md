---
title: "/highentropyva (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/highentropyva"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/highentropyva compiler option [C#]"
  - "-highentropyva compiler option [C#]"
  - "highentropyva compiler option [C#]"
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /highentropyva (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção do compilador de **\/highentropyva** informa o kernel do windows se um executável específico da suporte ao Randomization alto \(ASLR\) do layout do espaço de endereço da entropia.  
  
## Sintaxe  
  
```  
/highentropyva[+ | -]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Esta opção especifica que um executável de 64 bits ou um executável que é marcado pela opção do compilador de [\/platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) oferecem suporte a um espaço de endereço virtual superior da entropia.  A opção é desabilitada por padrão.  Use **\/highentropyva\+** ou **\/highentropyva** para habilitá\-lo.  
  
## Comentários  
 A opção de **\/highentropyva** habilita versões correspondentes de kernel do windows para usar um graus mais altos da entropia randomizing o layout do espaço de endereço de um processo como parte de ASLR.  Usar um graus mais altos da entropia significa que um número maior de endereços pode ser atribuído às regiões da memória como pilhas e heaps.  No resultado, é mais difícil determinar o local de uma região de memórias específico.  
  
 Quando a opção de compilador de **\/highentropyva** for especificada, o executável destino e todos os módulos que depender deve ser capaz de lidar com os valores de ponteiro maiores de 4 gigabytes \(GB\) quando o estiver executando como um processo de 64 bits.  
  
 Para obter mais informações sobre como ASLR, consulte [Vulnerabilidades de software da eliminação](http://go.microsoft.com/fwlink/?LinkId=226234).