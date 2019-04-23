---
title: Retomar sem erro
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 61332486b20af66af24eac06b222a38353578c16
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300899"
---
# <a name="resume-without-error"></a>Retomar sem erro
Um `Resume` instrução apareceu fora do código de tratamento de erro ou o código entrou em um manipulador de erro, mesmo que não houve erro.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Mover o `Resume` instrução em um manipulador de erro, ou excluí-lo.  
  
2. Portanto, salta para rótulos não pode ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro. Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não seja um `On Error GoTo` instrução, altere o rótulo de linha de acordo com seu destino pretendido.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
