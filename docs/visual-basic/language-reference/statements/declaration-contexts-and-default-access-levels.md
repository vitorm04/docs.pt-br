---
title: Contextos de declaração e níveis de acesso padrão
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354096"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextos de declaração e níveis de acesso padrão (Visual Basic)
Este tópico descreve quais tipos de Visual Basic podem ser declarados dentro dos outros tipos e quais seus níveis de acesso padrão se não forem especificados.  
  
## <a name="declaration-context-levels"></a>Níveis de contexto de declaração  
 O *contexto de declaração* de um elemento de programação é a região do código na qual ele é declarado. Geralmente, esse é outro elemento de programação, que é chamado de *elemento que o contém*.  
  
 Os níveis para contextos de declaração são os seguintes:  
  
- *Nível de namespace* — dentro de um arquivo de origem ou namespace, mas não dentro de uma classe, estrutura, módulo ou interface  
  
- *Nível de módulo* — dentro de uma classe, estrutura, módulo ou interface, mas não dentro de um procedimento ou bloco  
  
- *Nível de procedimento* — dentro de um procedimento ou bloco (como `If` ou `For`)  
  
 A tabela a seguir mostra os níveis de acesso padrão para vários elementos de programação declarados, dependendo de seus contextos de declaração.  
  
|Elemento declarado|Nível de namespace|Nível de módulo|Nível de procedimento|  
|----------------------|---------------------|------------------|---------------------|  
|Variável ([instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md))|Não permitido|`Private` (`Public` em `Structure`, não permitido em `Interface`)|`Public`|  
|Constante ([instrução const](../../../visual-basic/language-reference/statements/const-statement.md))|Não permitido|`Private` (`Public` em `Structure`, não permitido em `Interface`)|`Public`|  
|Enumeration ([instrução enum](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Não permitido|  
|Classe ([declaração de classe](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Não permitido|  
|Estrutura ([instrução de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Não permitido|  
|Módulo ([instrução Module](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Não permitido|Não permitido|  
|Interface ([instrução de interface](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Não permitido|  
|Procedimento ([instrução function](../../../visual-basic/language-reference/statements/function-statement.md), [sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md))|Não permitido|`Public`|Não permitido|  
|Referência externa ([instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Não permitido|`Public` (não permitido em `Interface`)|Não permitido|  
|Operador ([instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md))|Não permitido|`Public` (não permitido em `Interface` ou `Module`)|Não permitido|  
|Propriedade ([instrução de propriedade](../../../visual-basic/language-reference/statements/property-statement.md))|Não permitido|`Public`|Não permitido|  
|Propriedade Default ([padrão](../../../visual-basic/language-reference/modifiers/default.md))|Não permitido|`Public` (não permitido em `Module`)|Não permitido|  
|Evento ([instrução de evento](../../../visual-basic/language-reference/statements/event-statement.md))|Não permitido|`Public`|Não permitido|  
|Delegate ([instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Não permitido|  
  
 Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Consulte também

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Público](../../../visual-basic/language-reference/modifiers/public.md)
