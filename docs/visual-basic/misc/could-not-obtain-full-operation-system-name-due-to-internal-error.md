---
title: "Não foi possível obter o nome do sistema completo de operação devido a erro interno"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c67d47126718c3d90d853add61b7d06aaf84fc70
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Não foi possível obter o nome do sistema completo de operação devido a erro interno
Não foi possível obter o nome do sistema completo de operação devido a erro interno. Isso pode ser causado pelo WMI não existentes no computador atual.  
  
 Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou. Uma possível causa dessa falha é se o Windows Management Instrumentation (WMI) não está instalado no computador atual.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar um `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.  
  
2.  Para obter mais informações sobre WMI e como instalá-lo, vá para e procure "Windows Management Instrumentation Core".  
  
## <a name="see-also"></a>Consulte também  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Instrução Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
