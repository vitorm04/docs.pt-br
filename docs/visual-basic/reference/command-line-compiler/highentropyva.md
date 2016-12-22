---
title: "/highentropyva (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Opção de compilador /highentropyva (Visual Basic)"
  - "Opção de compilador highentropyva (Visual Basic)"
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /highentropyva (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica se um executável de 64 bits ou um executável que é marcado pela  [anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) opção de compilador suporta alta entropia randomização de Layout de espaço de endereço \(ASLR\).  
  
## Sintaxe  
  
```  
/highentropyva[+ | -]  
```  
  
## Argumentos  
 `+` &#124; `-`  
 Opcional.  A opção está desativada por padrão ou se você especificar `/highentropyva-`.  A opção está ativada, se você especificar `/highentropyva` ou `/highentropyva+`.  
  
## Comentários  
 Se você especificar esta opção, compatível com versões do kernel do Windows podem usar níveis mais altos de entropia ao kernel aleatoriamente o layout do espaço de endereço de um processo como parte da ASLR.  Se o kernel usa níveis mais altos de entropia, um número maior de endereços pode ser alocado para regiões de memória, como pilhas e pilhas.  Como resultado, é mais difícil de adivinhar a localização de uma região específica da memória.  
  
 Quando a opção está ativada, o executável de destino e todos os módulos no qual ele depende deve ser capaz de lidar com valores de ponteiro são maiores do que 4 gigabytes \(GB\) quando esses módulos estão sendo executados como processos de 64 bits.  
  
 Para obter mais informações sobre a ASLR, consulte [Atenuar vulnerabilidades de Software](http://go.microsoft.com/fwlink/?LinkId=226234).  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)