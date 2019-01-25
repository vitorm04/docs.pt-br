---
title: Contextos de declaração e níveis de acesso padrão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 75c5b16164e9ecb6558e445c59e4a312158ff4f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580805"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextos de declaração e níveis de acesso padrão (Visual Basic)
Este tópico descreve quais tipos de Visual Basic podem ser declarados dentro do quais outros tipos, e o que seus níveis de acesso padrão se não especificado.  
  
## <a name="declaration-context-levels"></a>Níveis de contexto de declaração  
 O *contexto de declaração* de um elemento de programação é a região de código no qual ela é declarada. Isso geralmente é outro elemento de programação, que é chamado, em seguida, o *que contém o elemento*.  
  
 Os níveis para contextos de declaração são os seguintes:  
  
-   *Nível de Namespace* — dentro de um arquivo de origem ou namespace, mas não dentro de uma classe, estrutura, módulo ou interface  
  
-   *Nível de módulo* — dentro de uma classe, estrutura, módulo ou interface, mas não dentro de um procedimento ou bloco  
  
-   *Nível de procedimento* — dentro de um procedimento ou bloco (como `If` ou `For`)  
  
 A tabela a seguir mostra os níveis de acesso padrão para vários elementos de programação declarados, dependendo de seus contextos de declaração.  
  
|Elemento declarado|Nível de Namespace|Nível de módulo|Nível de procedimento|  
|----------------------|---------------------|------------------|---------------------|  
|Variáveis ([instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md))|Não permitido|`Private` (`Public` na `Structure`, não permitido em `Interface`)|`Public`|  
|Constante ([instrução Const](../../../visual-basic/language-reference/statements/const-statement.md))|Não permitido|`Private` (`Public` na `Structure`, não permitido em `Interface`)|`Public`|  
|Enumeração ([instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Não permitido|  
|Classe ([instrução Class](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Não permitido|  
|Estrutura ([estrutura instrução](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Não permitido|  
|Módulo ([declaração de módulo](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Não permitido|Não permitido|  
|Interface ([instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Não permitido|  
|Procedimento ([instrução Function](../../../visual-basic/language-reference/statements/function-statement.md), [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md))|Não permitido|`Public`|Não permitido|  
|Referência externa ([instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Não permitido|`Public` (não permitido em `Interface`)|Não permitido|  
|Operador ([instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md))|Não permitido|`Public` (não permitido em `Interface` ou `Module`)|Não permitido|  
|Propriedade ([declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md))|Não permitido|`Public`|Não permitido|  
|Propriedade padrão ([padrão](../../../visual-basic/language-reference/modifiers/default.md))|Não permitido|`Public` (não permitido em `Module`)|Não permitido|  
|Evento ([declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md))|Não permitido|`Public`|Não permitido|  
|Delegado ([instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Não permitido|  
  
 Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Consulte também
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Público](../../../visual-basic/language-reference/modifiers/public.md)
