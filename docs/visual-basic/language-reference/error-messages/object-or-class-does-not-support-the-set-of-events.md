---
title: O objeto ou a classe não dá suporte ao conjunto de eventos
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: c5e8b8de3477147fc3174cdbee401c89753004ad
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159944"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>O objeto ou a classe não dá suporte ao conjunto de eventos

Você tentou usar uma `WithEvents` variável com um componente que não pode funcionar como uma origem do evento para o conjunto de eventos especificado. Por exemplo, você queria coletar os eventos de um objeto e, em seguida, criar outro objeto que `Implements` o primeiro objeto. Embora você possa imaginar que possa coletar os eventos do objeto implementado, esse nem sempre é o caso. `Implements` implementa apenas uma interface para métodos e propriedades. `WithEvents` Não tem suporte para privado `UserControls` , porque as informações de tipo necessárias para gerar o `ObjectEvent` não estão disponíveis no tempo de execução.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Você não pode coletar eventos para um componente que não tem eventos de origem.

## <a name="see-also"></a>Veja também

- [WithEvents](../modifiers/withevents.md)
- [Instrução Implements](../statements/implements-statement.md)
