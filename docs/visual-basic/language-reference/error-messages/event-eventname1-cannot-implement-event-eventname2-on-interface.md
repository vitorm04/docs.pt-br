---
title: Evento &#39; &lt;eventname1&gt; &#39; não é possível implementar o evento &#39; &lt;eventname2&gt; &#39; na interface &#39; &lt;interface&gt; &#39; porque seus tipos delegados &#39; &lt;delegate1&gt; &#39; e &#39; &lt;delegate2&gt; &#39; não coincidem
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 024e260f12d3497d64f26e59521f016ad439ebb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638204"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Evento &#39; &lt;eventname1&gt; &#39; não é possível implementar o evento &#39; &lt;eventname2&gt; &#39; na interface &#39; &lt;interface&gt; &#39; porque seus tipos delegados &#39; &lt;delegate1&gt; &#39; e &#39; &lt;delegate2&gt; &#39; não coincidem
Visual Basic não pode implementar um evento porque o tipo de delegado do evento não corresponde ao tipo de delegado do evento na interface. Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá-los junto com o mesmo evento. Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando a `As` sintaxe e especifique o mesmo tipo de delegado.  
  
 **ID do erro:** BC31423  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Implemente os eventos separadamente.  
  
     —ou—  
  
-   Defina os eventos na interface usando o `As` sintaxe e especifique o mesmo tipo de delegado.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
