---
title: Retomar sem erro
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a>Retomar sem erro
Um `Resume` instrução apareceu fora do código de tratamento de erros ou o código pular para um manipulador de erro, embora nenhum erro.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Mover o `Resume` instrução em um manipulador de erro, ou excluí-lo.  
  
2.  Portanto saltos para rótulos não podem ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro. Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é um `On Error GoTo` instrução, alterar o rótulo de linha de acordo com seu destino pretendido.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
