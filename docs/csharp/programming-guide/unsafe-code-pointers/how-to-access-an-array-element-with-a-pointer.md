---
title: "Como acessar um elemento de matriz com um ponteiro (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "ponteiros [C#], acesso à matriz"
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como acessar um elemento de matriz com um ponteiro (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em um contexto não seguro, você pode acessar um elemento na memória por meio do acesso do elemento de ponteiro, conforme mostrado no exemplo a seguir:  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 A expressão entre colchetes deve ser implicitamente conversível em `int`, `uint`, `long`, ou `ulong`.  A operação p \[e\] é equivalente a \*\(p\+e\).  Assim como c e C\+\+, o acesso ao elemento ponteiro não verifica out\-of\-bounds erros.  
  
## Exemplo  
 Neste exemplo, 123 locais de memória são alocados para uma matriz de caracteres, `charPointer`.  A matriz é usada para exibir as letras minúsculas e letras maiúsculas em dois  [para](../../../csharp/language-reference/keywords/for.md) loops.  
  
 Observe que a expressão `charPointer[i]` é equivalente à expressão `*(charPointer + i)`, e você pode obter o mesmo resultado usando uma das duas expressões.  
  
 [!CODE [csProgGuidePointers#11](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#11)]  
  
 [!CODE [csProgGuidePointers#12](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#12)]  
  
  **Letras maiúsculas:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Letras minúsculas:**  
**abcdefghijklmnopqrstuvwxyz**   
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [Tipos](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)