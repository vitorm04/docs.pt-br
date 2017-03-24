---
title: "Contextos de declaração e padrão de acesso a níveis (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a4e5072ae0ea4778b8521b0d4cfea1d942fb033b
ms.lasthandoff: 03/13/2017

---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextos de declaração e níveis de acesso padrão (Visual Basic)
Este tópico descreve quais tipos de Visual Basic podem ser declarados no quais outros tipos, e o que os níveis de acesso padrão se não especificado.  
  
## <a name="declaration-context-levels"></a>Níveis de contexto de declaração  
 O *contexto declaração* de um elemento de programação é a região de código no qual ela é declarada. Isso geralmente é outro elemento de programação, que é chamado de *que contém o elemento*.  
  
 Os níveis de contextos de declaração são os seguintes:  
  
-   *Nível de Namespace* — dentro de um namespace ou arquivo de origem, mas não dentro de uma classe, estrutura, módulo ou interface  
  
-   *Nível de módulo* — dentro de uma classe, estrutura, módulo ou interface, mas não dentro de um procedimento ou bloco  
  
-   *Nível de procedimento* — dentro de um procedimento ou bloco (como `If` ou `For`)  
  
 A tabela a seguir mostra os níveis de acesso padrão para vários elementos de programação declarados, dependendo de seus contextos de declaração.  
  
|Elementos declarados|Nível de Namespace|Nível de módulo|Nível de procedimento|  
|----------------------|---------------------|------------------|---------------------|  
|Variável ([instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md))|Não permitido|`Private`(`Public` na `Structure`, não é permitido em `Interface`)|`Public`|  
|Constante ([instrução Const](../../../visual-basic/language-reference/statements/const-statement.md))|Não permitido|`Private`(`Public` na `Structure`, não é permitido em `Interface`)|`Public`|  
|Enumeração ([instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Não permitido|  
|Classe ([instrução Class](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Não permitido|  
|Estrutura ([estrutura instrução](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Não permitido|  
|Módulo ([instrução módulo](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Não permitido|Não permitido|  
|Interface ([instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Não permitido|  
|Procedimento ([declaração de função](../../../visual-basic/language-reference/statements/function-statement.md), [Sub instrução](../../../visual-basic/language-reference/statements/sub-statement.md))|Não permitido|`Public`|Não permitido|  
|Referência externa ([instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Não permitido|`Public`(não permitido em `Interface`)|Não permitido|  
|Operador ([instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md))|Não permitido|`Public`(não permitido em `Interface` ou `Module`)|Não permitido|  
|Propriedade ([declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md))|Não permitido|`Public`|Não permitido|  
|Propriedade padrão ([padrão](../../../visual-basic/language-reference/modifiers/default.md))|Não permitido|`Public`(não permitido em `Module`)|Não permitido|  
|Evento ([instrução Event](../../../visual-basic/language-reference/statements/event-statement.md))|Não permitido|`Public`|Não permitido|  
|Delegado ([instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Não permitido|  
  
 Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Consulte também  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)   
 [Público](../../../visual-basic/language-reference/modifiers/public.md)
