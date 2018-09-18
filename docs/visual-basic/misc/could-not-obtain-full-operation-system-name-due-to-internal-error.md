---
title: Não foi possível obter o nome do sistema de operação completa devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 192033348a779591a54860505d5d707a802c415a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45972711"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Não foi possível obter o nome do sistema de operação completa devido a erro interno
Não foi possível obter o nome do sistema de operação completa devido a erro interno. Isso pode ser causado pelo WMI não existente no computador atual.  
  
 Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou. Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar um `Try...Catch` bloco em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.  
  
2.  Para obter mais informações sobre o WMI e como instalá-lo, vá para e pesquise por "Core de instrumentação de gerenciamento do Windows".  
  
## <a name="see-also"></a>Consulte também  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Exceção e tratamento de erro no Visual Basic](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Instrução Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
