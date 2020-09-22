---
title: O objeto ou a classe não dá suporte ao conjunto de eventos
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873650"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>O objeto ou a classe não dá suporte ao conjunto de eventos

Você tentou usar uma `WithEvents` variável com um componente que não pode funcionar como uma origem do evento para o conjunto de eventos especificado. Por exemplo, você queria coletar os eventos de um objeto e, em seguida, criar outro objeto que `Implements` o primeiro objeto. Embora você possa imaginar que possa coletar os eventos do objeto implementado, esse nem sempre é o caso. `Implements` implementa apenas uma interface para métodos e propriedades. `WithEvents` Não tem suporte para privado `UserControls` , porque as informações de tipo necessárias para gerar o `ObjectEvent` não estão disponíveis no tempo de execução.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Você não pode coletar eventos para um componente que não tem eventos de origem.  
  
## <a name="see-also"></a>Confira também

- [WithEvents](../modifiers/withevents.md)
- [Instrução Implements](../statements/implements-statement.md)
