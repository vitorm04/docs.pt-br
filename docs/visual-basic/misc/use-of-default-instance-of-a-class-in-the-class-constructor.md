---
title: Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 14c498bf3067415f8de2afaeaaa57cf3f28ae857
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022448"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita
Uma instância padrão de uma classe foi usada no construtor da classe. Isso pode levar a uma chamada recursiva infinita, também conhecido como um loop infinito.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a instância padrão do construtor da classe.  
  
## <a name="see-also"></a>Consulte também

- [Construtores](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
