---
title: "Cl&#225;usula Implements (Visual Basic) | Microsoft Docs"
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
  - "vb.ImplementsClause"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Implements"
  - "instrução Implements, sobre Implements"
  - "implementação de interface, palavra-chave Implements"
  - "implementação de interface, reimplementação"
  - "membros de interface"
  - "membros de interface, implementando"
  - "membros de interface, palavra-chave Implements"
  - "membros de interface, reimplementação"
  - "membros, implementando"
  - "membros, palavra-chave Implements"
  - "membros, reimplementação"
  - "reimplementação"
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Implements (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que um membro de classe ou estrutura está fornecendo a implementação de um membro definido em uma interface.  
  
## Comentários  
 A palavra\-chave `Implements`não é igual a [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).  Você usa a instrução `Implements` para especificar que uma classe ou estrutura implementa uma ou mais interfaces, e em seguida, para cada membro você usa a palavra\-chave `Implements` para especificar qual interface e qual membro ele implementa.  
  
 Se uma classe ou estrutura implementa uma interface, ela deve incluir a instrução `Implements` imediatamente após [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) ou [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md),e ela deve implementar todos os membros definidos pela interface.  
  
## Reimplementação  
 Em um classe derivada, você pode re\-implementar um membro de interface que já tenha sido implementado pela classe base.  Isso é diferente de substituir o membro de classe base nos seguintes aspectos:  
  
-   O membro de classe base não precisa ser [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.  
  
-   Você pode re\-implementar o membro com um nome diferente.  
  
 A palavra\-chave `Implements` pode ser usada nesses contextos:  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)