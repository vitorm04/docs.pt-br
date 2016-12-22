---
title: "C&#243;digo n&#227;o seguro e ponteiros (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "segurança [c#], segurança de tipo"
  - "Linguagem c#, código não seguro"
  - "segurança de tipo [C#]"
  - "palavra-chave unsafe [C#]"
  - "código não seguro [C#]"
  - "Linguagem c#, ponteiros"
  - "ponteiros [c#], sobre ponteiros"
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C&#243;digo n&#227;o seguro e ponteiros (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para manter a segurança de tipo, C\# não oferece suporte a aritmética do ponteiro, por padrão.  No entanto, usando a palavra\-chave de [não seguro](../../../csharp/language-reference/keywords/unsafe.md) , você pode definir um contexto no qual não seguro ponteiros podem ser usados.  Para obter mais informações sobre os ponteiros, consulte o tópico [Tipos ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  Em tempo de execução \(CLR\) language runtime, o código não seguro é conhecido como código não verificável.  O código não seguro em C\# não necessariamente é perigoso; é apenas o código cuja segurança não pode ser marcada pelo CLR.  O CLR como consequência será executado somente o código seguro não estiver em um assembly totalmente confiável.  Se você usar o código não seguro, é de sua responsabilidade assegurar que seu código não apresentam riscos de segurança ou erros do ponteiro.  
  
## Visão geral não seguro de código  
 O código não seguro tem as seguintes propriedades:  
  
-   Os métodos, os tipos, e os blocos de código podem ser definidos como não seguro.  
  
-   Em alguns casos, o código não seguro pode aumentar o desempenho de um aplicativo removendo as verificações dos limites da matriz.  
  
-   O código não seguro é necessário quando você chama funções nativos que exigem ponteiros.  
  
-   Usar o código não seguro apresenta os riscos de segurança e de estabilidade.  
  
-   Para C\# que compila o código não seguro, o aplicativo deve ser compilado com [\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## Seções relacionadas  
 Para obter mais informações, consulte  
  
-   [Tipos de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Buffers de tamanho fixo](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Como usar ponteiros para copiar uma matriz de bytes](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)