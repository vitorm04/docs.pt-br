---
title: "Buffers de tamanho fixo (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "buffer de tamanho fixo [C#]"
  - "buffers não seguros [C#]"
  - "código não seguro [C#], buffer de tamanho fixo"
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Buffers de tamanho fixo (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

No C\#, você pode usar o  [fixa](../../../csharp/language-reference/keywords/fixed-statement.md) a instrução para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados.  Isso é útil quando você estiver trabalhando com o código existente, como, por exemplo, códigos escritos em outras linguagens, DLLs pré\-existente ou COM projetos.  Matriz fixed pode levar nenhum atributo ou modificadores que têm permissão para membros de struct regular.  The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.  
  
```  
private fixed char name[30];  
```  
  
## Comentários  
 Nas primeiras versões do C\#, declarar uma estrutura de tamanho fixo de estilo C\+\+ era difícil porque uma struct C\# contém uma matriz não contém os elementos da matriz.  Em vez disso, a estrutura contém uma referência aos elementos.  
  
 C\# 2.0 adicionou a capacidade de incorporar uma matriz de tamanho fixo em um  [struct](../../../csharp/language-reference/keywords/struct.md) quando ele é usado em um  [não seguros](../../../csharp/language-reference/keywords/unsafe.md) bloco de código.  
  
 Por exemplo, antes de C\# 2.0, o seguinte `struct` seria 8 bytes de tamanho.  O `pathName` matriz é uma referência para o array alocada em heap com:  
  
 [!CODE [csProgGuidePointers#19](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#19)]  
  
 Começando com o C\# 2.0, um `struct` pode conter uma matriz incorporada.  No exemplo a seguir, o `fixedBuffer` matriz tem um tamanho fixo.  Para acessar os elementos da matriz, você usar um `fixed` a instrução para estabelecer um ponteiro para o primeiro elemento.  O `fixed` instrução fixa de uma instância de `fixedBuffer` para um local específico na memória.  
  
 [!CODE [csProgGuidePointers#20](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#20)]  
  
 O tamanho do elemento 128 `char` matriz é de 256 bytes.  Fixa o tamanho  [char](../../../csharp/language-reference/keywords/char.md) buffers terão sempre dois bytes por caractere, independentemente da codificação.  Isso é verdadeiro mesmo quando os buffers de char são empacotados para métodos de API ou estruturas com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.  Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.  
  
 Outra matriz de tamanho fixo comum é o  [bool](../../../csharp/language-reference/keywords/bool.md) array.  Os elementos em um `bool` matriz são sempre um byte de tamanho.  `bool`arrays não são adequados para a criação de matrizes de bits ou os buffers.  
  
> [!NOTE]
>  Com exceção de memória criada usando  [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), o compilador C\# e o common language runtime \(CLR\) não executarem nenhuma verificação de saturação do buffer de segurança.  Assim como acontece com todo o código não seguro, tome cuidado.  
  
 Buffers inseguros diferem dos arrays regulares das seguintes maneiras:  
  
-   Você só pode usar buffers não seguros em um contexto.  
  
-   Buffers inseguros são sempre vetores ou matrizes unidimensionais.  
  
-   A declaração da matriz deve incluir uma contagem, tais como `char id[8]`.  Não é possível usar `char id[]` em vez disso.  
  
-   Buffers não seguros só podem ser campos de instância de estruturas em um contexto.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [Interoperabilidade](../../../csharp/programming-guide/interop/interoperability.md)