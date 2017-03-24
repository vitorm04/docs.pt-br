---
title: "Evento &quot;&lt;eventname1&gt;&quot;não pode implementar o evento&quot;&lt;eventname2&gt;&quot;na interface&quot;&lt;interface&gt;&quot; porque seus tipos delegados&lt;delegate1&gt;&quot;e&quot;&lt;delegate2&gt;&quot; não coincidem | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
dev_langs:
- VB
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
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
ms.openlocfilehash: b6253b3e9ad07c3715c55a8cfd0891792b45a452
ms.lasthandoff: 03/13/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Evento '&lt;eventname1&gt;'não pode implementar o evento'&lt;eventname2&gt;'na interface'&lt;interface&gt;' porque seus tipos delegados&lt;delegate1&gt;'e'&lt;delegate2&gt;' não correspondem
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]não é possível implementar um evento porque o tipo delegado do evento não corresponde ao tipo delegado do evento na interface. Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá-los junto com o mesmo evento. Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando a `As` sintaxe e especifique o mesmo tipo delegado.  
  
 **ID do erro:** BC31423  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Implemente os eventos separadamente.  
  
     —ou—  
  
-   Defina os eventos na interface usando o `As` sintaxe e especifique o mesmo tipo delegado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
