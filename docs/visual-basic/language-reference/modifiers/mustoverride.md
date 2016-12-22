---
title: "MustOverride (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.MustOverride"
  - "MustOverride"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elementos, puro virtual"
  - "Palavra-chave MustOverride"
  - "substituição, Palavra-chave MustOverride"
  - "procedimentos, substituição"
  - "procedimentos, redefinindo"
  - "propriedades [Visual Basic], substituição"
  - "propriedades [Visual Basic], redefinindo"
  - "elementos puros virtuais"
  - "elementos virtuais, puro"
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# MustOverride (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma propriedade ou um procedimento não é implementado dessa classe e deve ser substituído em uma classe derivada antes que ela pode ser usada.  
  
## Comentários  
 Você pode usar `MustOverride` somente na declaração de uma propriedade ou procedimento.  A propriedade ou procedimento que especifica `MustOverride` deve ser membro de uma classe, e a classe deve ser marcada [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## Regras  
  
-   **Declaração incompleta.** Quando você especifica `MustOverride`, você não fornecer nenhuma linha adicional de código da propriedade ou um procedimento, não até mesmo o `End Function`, `End Property`, ou `End Sub` instrução.  
  
-   **Modificadores Combinados.** Não é possível especificar `MustOverride` em conjunto com `NotOverridable`, `Overridable`, ou `Shared` na mesma declaração.  
  
-   **Sombreamento e substituição.** Tanto o sombreamento quanto a desautorização redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.  Para obter mais informações, consulte [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Termos alternativos.** Um elemento que não pode ser usado, exceto em substituição às vezes é chamado um  *puro virtual* elemento.  
  
 O modificador `MustOverride` pode ser utilizado nestes contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)