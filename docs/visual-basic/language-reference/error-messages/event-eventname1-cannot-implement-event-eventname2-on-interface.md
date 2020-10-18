---
title: O evento '<eventname1>' não pode implementar o evento '<eventname2>' na interface '<interface>' porque seus tipos delegados '<delegate1>' e '<delegate2>' não correspondem.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d0b2b095ed355b420b28e87ed0b9d6a31f049ebf
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162018"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>BC31423: o evento ' \<eventname1> ' não pode implementar \<eventname2> o evento ' ' na interface ' \<interface> ' porque seus tipos delegados ' \<delegate1> ' e ' \<delegate2> ' não correspondem

Visual Basic não pode implementar um evento porque o tipo delegado do evento não corresponde ao tipo delegado do evento na interface. Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tenta implementá-los junto com o mesmo evento. Um evento pode implementar dois ou mais eventos somente se todos os eventos implementados forem declarados usando a `As` sintaxe e especificarem o mesmo tipo de delegado.

 **ID do erro:** BC31423

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Implemente os eventos separadamente.

     — ou —

- Defina os eventos na interface usando a `As` sintaxe e especifique o mesmo tipo de delegado.

## <a name="see-also"></a>Veja também

- [Instrução Event](../statements/event-statement.md)
- [Instrução Delegate](../statements/delegate-statement.md)
- [Eventos](../../programming-guide/language-features/events/index.md)
