---
title: Não foi possível obter o nome do sistema de operação completa devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 6a0e24743c861ba92fc284a84fa4ef26e2ee48a8
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022757"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Não foi possível obter o nome do sistema de operação completa devido a erro interno
Não foi possível obter o nome do sistema de operação completa devido a erro interno. Isso pode ser causado pelo WMI não existente no computador atual.  
  
 Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou. Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar um `Try...Catch` bloco em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.  
  
2.  Para obter mais informações sobre o WMI e como instalá-lo, vá para e pesquise por "Core de instrumentação de gerenciamento do Windows".  
  
## <a name="see-also"></a>Consulte também

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Tratando e gerando exceções no .NET](../../standard/exceptions/index.md)
- [Instrução Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
