---
title: "#region (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "#region"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Diretiva #region [C#]"
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #region (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#region`permite especificar um bloco de código que você pode expandir ou recolher ao usar o  [estrutura de tópicos](/visual-studio/ide/outlining) recurso do Editor de código Visual Studio.  Nos arquivos de código mais tempo, é conveniente poder recolher ou ocultar uma ou mais regiões para que você possa se concentrar na parte do arquivo que você está trabalhando atualmente.  O exemplo a seguir mostra como definir uma região:  
  
```  
  
      #region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## Comentários  
 A `#region` bloco deve ser finalizado com um  [\# endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) diretiva.  
  
 A `#region` bloco não pode sobrepor um  [\# if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloco.  No entanto, um `#region` bloco pode ser aninhado em um `#if` bloco e um `#if` bloco pode ser aninhado em um `#region` bloco.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Diretivas de pré\-processador em C\#](../../../visual-basic/reference/command-line-compiler/index.md)