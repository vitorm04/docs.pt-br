---
title: Erro ao carregar a DLL (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID48
dev_langs:
- VB
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c63146400d45604140f4f2362f84a1534937df81
ms.lasthandoff: 03/13/2017

---
# <a name="error-in-loading-dll-visual-basic"></a>Erro no carregamento da DLL (Visual Basic)
Uma biblioteca de vínculo dinâmico (DLL) é uma biblioteca especificada no `Lib` cláusula de um `Declare` instrução. Possíveis causas para esse erro incluem:  
  
-   O arquivo não é DLL executável.  
  
-   O arquivo não é uma DLL do Microsoft Windows.  
  
-   A DLL referências outro DLL que não está presente.  
  
-   A DLL ou DLL referenciado não está em um diretório especificado no caminho.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o arquivo for um arquivo de texto de origem e, portanto, não DLL executável, ele deve ser compilado e vinculado a um formulário DLL-executável.  
  
-   Se o arquivo não é uma DLL do Microsoft Windows, obtenha o Microsoft Windows equivalente.  
  
-   Se a DLL referências outro DLL que não está presente, obter a DLL de referência e disponibilizá-lo.  
  
-   Se a DLL ou DLL referenciado não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
