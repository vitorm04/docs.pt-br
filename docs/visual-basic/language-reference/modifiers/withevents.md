---
title: WithEvents (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
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
ms.openlocfilehash: 708cf6fec78faf2c7a5959a3a2694d237d728882
ms.lasthandoff: 03/13/2017

---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Especifica que uma ou mais variáveis de membro declaradas se referir a uma instância de uma classe que pode gerar eventos.  
  
## <a name="remarks"></a>Comentários  
 Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método trata os eventos da variável usando a `Handles` palavra-chave.  
  
 Você pode usar `WithEvents` somente no nível de classe ou módulo. Isso significa que o contexto da declaração para um `WithEvents` variável deve ser uma classe ou módulo e não pode ser um arquivo fonte, namespace, estrutura ou procedimento.  
  
 Não é possível usar `WithEvents` em um membro de estrutura.  
  
 Você pode declarar apenas variáveis individuais — não matrizes — com `WithEvents`.  
  
## <a name="rules"></a>Regras  
  
-   **Tipos de elemento.** Você deve declarar `WithEvents` variáveis para serem variáveis de objeto para que eles possam aceitar instâncias de classe. No entanto, você não pode declará-los como `Object`. Você deve declará-los como a classe específica que pode lançar os eventos.  
  
 O `WithEvents` modificador pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
