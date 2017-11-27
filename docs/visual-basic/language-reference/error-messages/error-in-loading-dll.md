---
title: Erro no carregamento da DLL (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
