---
title: Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 02039b81251e59a951a0fe37ec2c9534b458b6a5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161914"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>BC30594: eventos de variáveis WithEvents compartilhadas não podem ser tratados por métodos não compartilhados

Uma variável declarada com o `Shared` modificador é uma variável compartilhada. Uma variável compartilhada identifica exatamente um local de armazenamento. Uma variável declarada com o `WithEvents` modificador afirma que o tipo ao qual a variável pertence trata o conjunto de eventos que a variável gera. Quando um valor é atribuído à variável, a propriedade criada pela `WithEvents` declaração desvincula qualquer manipulador de eventos existente e conecta o novo manipulador de eventos por meio do `Add` método.

 **ID do erro:** BC30594

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Declare seu manipulador de eventos `Shared` .

## <a name="see-also"></a>Veja também

- [Compartilhado](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
