---
title: "Como usar ponteiros para copiar uma matriz de bytes (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "matrizes [C#], byte"
  - "matrizes de bytes [C#]"
  - "ponteiros [C#], para copiar bytes"
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como usar ponteiros para copiar uma matriz de bytes (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O exemplo a seguir usa ponteiros para copiar bytes de um array para outro.  
  
 Este exemplo usa a  [não seguros](../../../csharp/language-reference/keywords/unsafe.md) palavra\-chave, que permite que você use os ponteiros na `Copy` método.  O  [fixa](../../../csharp/language-reference/keywords/fixed-statement.md) declaração é usada para declarar os ponteiros para os arrays de origem e de destino.  Isso  *pinos* o local de origem e destino arrays na memória para que eles não serão movidos pela coleta de lixo.  Os blocos de memória para os arrays são fixados quando o `fixed` bloco for concluído.  Porque o `Copy` método neste exemplo usa o `unsafe` palavra\-chave, ele deve ser compilado com o **\/unsafe** opção de compilador.  Para definir a opção no Visual Studio, clique com o botão direito no nome do projeto e clique em  **Propriedades**.  Sobre o  **Build** guia, selecione  **código inseguro de permitir**.  
  
## Exemplo  
 [!CODE [csProgGuidePointers#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#3)]  
  
 [!CODE [csProgGuidePointers#18](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#18)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [\/unsafe \(Enable Unsafe Mode\)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)