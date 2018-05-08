---
title: Não foi possível obter o nome do sistema completo de operação devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: f85ca5f7f325cb0dd2b8fc55d3f90f6abdfd4a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Não foi possível obter o nome do sistema completo de operação devido a erro interno
Não foi possível obter o nome do sistema completo de operação devido a erro interno. Isso pode ser causado pelo WMI não existentes no computador atual.  
  
 Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou. Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar um `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.  
  
2.  Para obter mais informações sobre WMI e como instalá-lo, vá para e procure "Windows Management Instrumentation Core".  
  
## <a name="see-also"></a>Consulte também  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Instrução Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
