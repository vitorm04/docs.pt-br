---
title: "Contextos de declara&#231;&#227;o e n&#237;veis de acesso padr&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "níveis de acesso, níveis padrão"
  - "níveis de acesso, Visual Basic"
  - "contextos de declaração, Visual Basic"
  - "nível de módulo, definido"
  - "nível de namespace, definido"
  - "nível de procedimento, definido"
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Contextos de declara&#231;&#227;o e n&#237;veis de acesso padr&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este tópico descreve quais tipos de Visual Basic podem ser declarados em quais outros tipos, e o que seus níveis de acesso padrão se não for especificado.  
  
## Níveis de contexto de declaração  
 O  *o contexto de declaração* de um elemento de programação é a região de código na qual é declarada.  Geralmente, isso é outro elemento de programação, que é chamado a  *que contém o elemento*.  
  
 Os níveis para contextos de declaração são as seguintes:  
  
-   *Nível de namespace* — dentro de um arquivo de origem ou de um espaço para nome, mas não dentro de uma classe, estrutura, módulo ou interface  
  
-   *Nível de módulo* — dentro de uma classe, estrutura, módulo ou interface, mas não em um procedimento ou bloco  
  
-   *Nível de procedimento* — dentro de um procedimento ou bloco \(como `If` ou `For`\)  
  
 A tabela a seguir mostra os níveis de acesso padrão para vários elementos de programação declarados, dependendo dos seus contextos de declaração.  
  
|Elemento declarado|Nível de namespace|Nível de módulo|Nível de procedimento|  
|------------------------|------------------------|---------------------|---------------------------|  
|Variável \([Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)\)|Não permitido|`Private`\(`Public` in `Structure`, not allowed in `Interface`\)|`Public`|  
|Constante \([Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)\)|Não permitido|`Private`\(`Public` in `Structure`, not allowed in `Interface`\)|`Public`|  
|Enumeração \([Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)\)|`Friend`|`Public`|Não permitido|  
|Class \([Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)\)|`Friend`|`Public`|Não permitido|  
|Estrutura \([Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)\)|`Friend`|`Public`|Não permitido|  
|Module \([Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)\)|`Friend`|Não permitido|Não permitido|  
|Interface \([Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)\)|`Friend`|`Public`|Não permitido|  
|Procedure \([Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md), [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)\)|Não permitido|`Public`|Não permitido|  
|Referência externa \([Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)\)|Não permitido|`Public`\(não permitido em `Interface`\)|Não permitido|  
|Operador \([Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)\)|Não permitido|`Public`\(not allowed in `Interface` or `Module`\)|Não permitido|  
|Propriedade \([Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)\)|Não permitido|`Public`|Não permitido|  
|Propriedade padrão \([Padrão](../../../visual-basic/language-reference/modifiers/default.md)\)|Não permitido|`Public`\(não permitido em `Module`\)|Não permitido|  
|Event \([Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)\)|Não permitido|`Public`|Não permitido|  
|Delegado \([Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)\)|`Friend`|`Public`|Não permitido|  
  
 Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Consulte também  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)