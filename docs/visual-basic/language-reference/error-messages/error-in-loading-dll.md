---
title: Erro no carregamento da DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: c3f88a5a3c37c89d23055aa413957b2add38ed67
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816896"
---
# <a name="error-in-loading-dll-visual-basic"></a>Erro no carregamento da DLL (Visual Basic)
Uma biblioteca de vínculo dinâmico (DLL) é uma biblioteca especificada na `Lib` cláusula de um `Declare` instrução. Possíveis causas para esse erro incluem:  
  
-   O arquivo não é executável da DLL.  
  
-   O arquivo não é uma DLL do Microsoft Windows.  
  
-   A DLL faz referência a outro DLL que não está presente.  
  
-   A DLL ou DLL referenciada não está em um diretório especificado no caminho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o arquivo for um arquivo de texto de origem e, portanto, não DLL executável, ele deve ser compilado e vinculado a um formulário de DLL executável.  
  
-   Se o arquivo não é uma DLL do Microsoft Windows, obtenha o Windows Microsoft equivalente.  
  
-   Se a DLL referências outro DLL que não está presente, obtenha a DLL de referência e disponibilizá-lo.  
  
-   Se a DLL ou DLL referenciada não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
