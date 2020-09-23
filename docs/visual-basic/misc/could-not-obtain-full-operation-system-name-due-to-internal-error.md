---
title: Não foi possível obter o nome do sistema completo de operação devido a erro interno
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 744d549b9313727af2feb82e45c24b729cae7262
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079081"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>Não foi possível obter o nome do sistema completo de operação devido a erro interno

Não foi possível obter o nome completo do sistema operacional devido a um erro interno. Isso pode ser causado por WMI não existente no computador atual.  
  
 Falha em uma chamada para a `My.Computer.Info.OSFullName` propriedade. Uma possível causa dessa falha é se a Instrumentação de Gerenciamento do Windows (WMI) não estiver instalada no computador atual.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Adicione um `Try...Catch` bloco em volta da chamada para a `My.Computer.Info.OSFullName` propriedade.  
  
2. Para obter mais informações sobre o WMI e como instalá-lo, vá para e pesquise "Instrumentação de Gerenciamento do Windows Core".  
  
## <a name="see-also"></a>Confira também

- [My. Computer. info. OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [Tratando e gerando exceções no .NET](../../standard/exceptions/index.md)
- [Instrução Try...Catch...Finally](../language-reference/statements/try-catch-finally-statement.md)
