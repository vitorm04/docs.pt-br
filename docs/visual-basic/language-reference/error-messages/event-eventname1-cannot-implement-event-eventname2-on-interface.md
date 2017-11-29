---
title: "Evento &#39; &lt;eventname1&gt;&#39; não pode implementar o evento &#39;&lt; eventname2&gt;&#39; interface &#39;&lt; interface&gt;&#39; porque seus tipos delegados &#39;&lt; delegate1&gt;&#39; e &#39;&lt; delegate2&gt;&#39; não coincidem"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords: BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Evento &#39; &lt;eventname1&gt;&#39; não pode implementar o evento &#39;&lt; eventname2&gt;&#39; interface &#39;&lt; interface&gt;&#39; porque seus tipos delegados &#39;&lt; delegate1&gt;&#39; e &#39;&lt; delegate2&gt;&#39; não coincidem
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]não é possível implementar um evento porque o tipo delegado do evento não corresponde ao tipo delegado do evento na interface. Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá-las em conjunto com o mesmo evento. Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando o `As` sintaxe e especifique o mesmo tipo delegado.  
  
 **ID do erro:** BC31423  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Implemente os eventos separadamente.  
  
     —ou—  
  
-   Defina os eventos na interface usando o `As` sintaxe e especifique o mesmo tipo delegado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
