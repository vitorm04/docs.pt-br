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
ms.openlocfilehash: 05c2d6420526b660ead2f50eba7feb6b20524705
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623938"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextos de declaração e níveis de acesso padrão (Visual Basic)
Este tópico descreve quais tipos de Visual Basic podem ser declarados dentro do quais outros tipos, e o que seus níveis de acesso padrão se não especificado.  
  
## <a name="declaration-context-levels"></a>Níveis de contexto de declaração  
 O *contexto de declaração* de um elemento de programação é a região de código no qual ela é declarada. Isso geralmente é outro elemento de programação, que é chamado, em seguida, o *que contém o elemento*.  
  
 Os níveis para contextos de declaração são os seguintes:  
  
- *Nível de Namespace* — dentro de um arquivo de origem ou namespace, mas não dentro de uma classe, estrutura, módulo ou interface  
  
- *Nível de módulo* — dentro de uma classe, estrutura, módulo ou interface, mas não dentro de um procedimento ou bloco  
  
- *Nível de procedimento* — dentro de um procedimento ou bloco (como `If` ou `For`)  
  
 A tabela a seguir mostra os níveis de acesso padrão para vários elementos de programação declarados, dependendo de seus contextos de declaração.  
  
|Elemento declarado|Nível de Namespace|Nível de módulo|Nível de procedimento|  
|----------------------|---------------------|------------------|---------------------|  
|Variáveis ([instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md))|Não permitida|`Private` (`Public` na `Structure`, não permitido em `Interface`)|`Public`|  
|Constante ([instrução Const](../../../visual-basic/language-reference/statements/const-statement.md))|Não permitida|`Private` (`Public` na `Structure`, não permitido em `Interface`)|`Public`|  
|Enumeração ([instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Não permitida|  
|Classe ([instrução Class](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Não permitida|  
|Estrutura ([estrutura instrução](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Não permitida|  
|Módulo ([declaração de módulo](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Não permitida|Não permitida|  
|Interface ([instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Não permitida|  
|Procedimento ([instrução Function](../../../visual-basic/language-reference/statements/function-statement.md), [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md))|Não permitida|`Public`|Não permitida|  
|Referência externa ([instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md))|Não permitida|`Public` (não permitido em `Interface`)|Não permitida|  
|Operador ([instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md))|Não permitida|`Public` (não permitido em `Interface` ou `Module`)|Não permitida|  
|Propriedade ([declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md))|Não permitida|`Public`|Não permitida|  
|Propriedade padrão ([padrão](../../../visual-basic/language-reference/modifiers/default.md))|Não permitida|`Public` (não permitido em `Module`)|Não permitida|  
|Evento ([declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md))|Não permitida|`Public`|Não permitida|  
|Delegado ([instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Não permitida|  
  
 Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Consulte também

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Público](../../../visual-basic/language-reference/modifiers/public.md)
