---
title: Retomar sem erro
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597869"
---
# <a name="resume-without-error"></a>Retomar sem erro
Um `Resume` instrução apareceu fora do código de tratamento de erros ou o código pular para um manipulador de erro, embora nenhum erro.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Mover o `Resume` instrução em um manipulador de erro, ou excluí-lo.  
  
2.  Portanto saltos para rótulos não podem ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro. Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é um `On Error GoTo` instrução, alterar o rótulo de linha de acordo com seu destino pretendido.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
