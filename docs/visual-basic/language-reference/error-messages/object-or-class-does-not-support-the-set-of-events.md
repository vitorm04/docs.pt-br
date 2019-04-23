---
title: O objeto ou a classe não dá suporte ao conjunto de eventos
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342876"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>O objeto ou a classe não dá suporte ao conjunto de eventos
Você tentou usar um `WithEvents` variável com um componente que não pode funcionar como uma origem de evento para o conjunto de eventos especificado. Por exemplo, você quiser coletar os eventos de um objeto e, em seguida, criar outro objeto que `Implements` o primeiro objeto. Embora você possa pensar que você pode coletar os eventos do objeto implementado, isso nem sempre é o caso. `Implements` apenas implementa uma interface para métodos e propriedades. `WithEvents` Não há suporte para privado `UserControls`, porque o tipo de informação necessária para elevar o `ObjectEvent` não está disponível em tempo de execução.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Você não pode coletar eventos para um componente que não faz eventos fonte.  
  
## <a name="see-also"></a>Consulte também

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
