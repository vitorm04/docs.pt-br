---
title: "O identificador &#233; muito longo | Microsoft Docs"
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
  - "bc30033"
  - "vbc30033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30033"
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O identificador &#233; muito longo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O nome, ou identificador, de todo elemento de programação é limitado a 1023 caracteres.  Além disso, um nome completamente qualificado não pode exceder 1023 caracteres.  Isso significa que a cadeia de caracteres do identificador \(`<namespace>.<...>.<namespace>.<class>.<element>`\) não pode ter mais de 1023 caracters, incluindo os caracteres `.` de operadores de acesso ao membro.  
  
 **Identificação do erro:**  BC30033  
  
### Para corrigir este erro  
  
-   Diminua o comprimento do identificador.  
  
## Consulte também  
 [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)