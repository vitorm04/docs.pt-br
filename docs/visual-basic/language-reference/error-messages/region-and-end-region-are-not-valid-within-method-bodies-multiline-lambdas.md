---
title: As instruções '#Region' e '#End Region' não são válidas dentro dos corpos/lambdas de várias linhas do método
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c792fa1a42bde22959ae21439cb2a0a1e4be343f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162278"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>BC32025: as instruções ' #Region ' e ' #End Region ' não são válidas em corpos de método/lambdas de várias linhas

O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace. Uma região recolhível pode incluir um ou mais procedimentos, mas não pode começar ou terminar dentro de um procedimento.

 **ID do erro:** BC32025

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Verifique se o procedimento anterior foi encerrado corretamente com `End Function` uma `End Sub` instrução ou.

2. Verifique se as `#Region` `#End Region` diretivas e estão no mesmo bloco de código.

## <a name="see-also"></a>Veja também

- [#Region diretiva](../directives/region-directive.md)
