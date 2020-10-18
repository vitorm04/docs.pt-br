---
title: "'<eventname>' é um evento, e não pode ser chamado diretamente"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161979"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a>BC32022: ' \<eventname> ' é um evento e não pode ser chamado diretamente

' <`eventname`> ' é um evento e, portanto, não pode ser chamado diretamente. Use uma `RaiseEvent` instrução para gerar um evento.

 Uma chamada de procedimento especifica um evento para o nome do procedimento. Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo de sinalização, que deve ser gerado e manipulado.

 **ID do erro:** BC32022

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Use uma `RaiseEvent` instrução para sinalizar um evento e invocar o procedimento ou procedimentos que o manipulam.

## <a name="see-also"></a>Veja também

- [Instrução RaiseEvent](../statements/raiseevent-statement.md)
