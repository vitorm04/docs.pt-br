---
title: O uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 5d239fdb7dcc5c488bf0341043b810ec7dadc083
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100315"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>O uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita

Uma instância padrão de uma classe foi usada no construtor da classe. Isso pode levar a uma chamada recursiva infinita, também conhecida como um loop infinito.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a instância padrão do construtor de classe.  
  
## <a name="see-also"></a>Confira também

- [Construtores](../programming-guide/concepts/object-oriented-programming.md#constructors)
