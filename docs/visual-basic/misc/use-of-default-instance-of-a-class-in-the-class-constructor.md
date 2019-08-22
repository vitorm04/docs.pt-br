---
title: O uso da instância padrão de uma classe no construtor de classe pode levar à chamada recursiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664375"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>O uso da instância padrão de uma classe no construtor de classe pode levar à chamada recursiva infinita
Uma instância padrão de uma classe foi usada no construtor da classe. Isso pode levar a uma chamada recursiva infinita, também conhecida como um loop infinito.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a instância padrão do construtor de classe.  
  
## <a name="see-also"></a>Consulte também

- [Construtores](../programming-guide/concepts/object-oriented-programming.md#constructors)
