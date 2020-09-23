---
title: Não foi possível obter informações sobre memória devido a um erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: 550ac0345d54c8a78e805b224ffaba47a3970ea9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91076273"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a>Não foi possível obter informações sobre memória devido a um erro interno

Falha em uma chamada para uma das propriedades de informações de memória do `My.Computer.Info` objeto.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicione um `Try...Catch` bloco em volta da chamada à propriedade Memory-Information do `My.Computer.Info` objeto.  
  
## <a name="see-also"></a>Confira também

- [My.Computer.Info](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [Instrução Try...Catch...Finally](../language-reference/statements/try-catch-finally-statement.md)
