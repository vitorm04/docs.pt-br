---
title: Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 1cad1e3cf3943e945d519aee061a877c91684b4a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623477"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Uso de instância padrão de uma classe no construtor da classe pode levar a chamada recursiva infinita
Uma instância padrão de uma classe foi usada no construtor da classe. Isso pode levar a uma chamada recursiva infinita, também conhecido como um loop infinito.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a instância padrão do construtor da classe.  
  
## <a name="see-also"></a>Consulte também

- [Construtores](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
