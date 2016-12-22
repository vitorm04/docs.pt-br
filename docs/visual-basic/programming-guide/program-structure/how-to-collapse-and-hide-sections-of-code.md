---
title: "Como recolher e ocultar se&#231;&#245;es do c&#243;digo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "código do Visual Basic, recolhendo e ocultando"
  - "Visual Basic, recolhimento de código"
  - "Visual Basic, ocultação de código"
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como recolher e ocultar se&#231;&#245;es do c&#243;digo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `#Region` diretiva permite que você recolher e ocultar seções de código em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos.  O `#Region` diretiva permite especificar um bloco de código que você pode expandir ou recolher ao usar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] o editor de código.  A capacidade para ocultar o código de forma seletiva torna seus arquivos mais gerenciável e mais fácil de ler.  Para obter mais informações, consulte [Estrutura de tópicos](/visual-studio/ide/outlining).  
  
 `#Region`diretivas oferecer suporte à semântica de bloco de código, como `#If...#End If`.  Isso significa que eles não podem começar em um bloco e terminam em outra; o início e fim devem estar no mesmo bloco.  `#Region`Não há suporte para diretivas dentro de funções.  
  
### Para recolher e ocultar uma seção de código  
  
-   Colocar a seção de código entre o `#Region` e `#End Region` instruções, como no exemplo a seguir:  
  
     [!CODE [VbVbalrConditionalComp#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#6)]  
  
     O `#Region` bloco pode ser usado várias vezes em um arquivo de código. Assim, os usuários podem definir seus próprios blocos de procedimentos e classes que podem, por sua vez, ser recolhidos.  `#Region`blocos também podem ser aninhados dentro dos outros `#Region` blocos.  
  
    > [!NOTE]
    >  Ocultando o código não impede que ele seja compilado e não afeta a `#If...#End If` instruções.  
  
## Consulte também  
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [Diretiva \#Region](../../../visual-basic/language-reference/directives/region-directive.md)   
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Estrutura de tópicos](/visual-studio/ide/outlining)