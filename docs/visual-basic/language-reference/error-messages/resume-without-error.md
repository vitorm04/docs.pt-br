---
title: Retomar sem erro
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870831"
---
# <a name="resume-without-error"></a>Retomar sem erro

Uma `Resume` instrução apareceu fora do código de tratamento de erros ou o código entrou em um manipulador de erros, embora não haja erro.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Mova a `Resume` instrução para um manipulador de erro ou exclua-a.  
  
2. Saltos para rótulos não podem ocorrer entre procedimentos. portanto, pesquise o procedimento para o rótulo que identifica o manipulador de erros. Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é uma `On Error GoTo` instrução, altere o rótulo da linha para concordar com o destino pretendido.  
  
## <a name="see-also"></a>Confira também

- [Instrução Resume](../statements/resume-statement.md)
- [Instrução On Error](../statements/on-error-statement.md)
