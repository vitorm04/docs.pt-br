---
title: Erro no carregamento da DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584677"
---
# <a name="error-in-loading-dll-visual-basic"></a>Erro no carregamento da DLL (Visual Basic)
Uma biblioteca de vínculo dinâmico (DLL) é uma biblioteca especificada no `Lib` cláusula de um `Declare` instrução. Possíveis causas para esse erro incluem:  
  
-   O arquivo não é um executável de DLL.  
  
-   O arquivo não é uma DLL do Microsoft Windows.  
  
-   A DLL referências outro DLL que não está presente.  
  
-   A DLL ou referenciado DLL não está em um diretório especificado no caminho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o arquivo é um arquivo de texto de origem e, portanto, não DLL executável, ele deve ser compilado e vinculado a um formulário DLL-executável.  
  
-   Se o arquivo não é uma DLL do Microsoft Windows, obtenha o Microsoft Windows equivalente.  
  
-   Se a DLL referências outro DLL que não está presente, obter a DLL de referência e disponibilizá-lo.  
  
-   Se a DLL ou DLL referenciado não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
