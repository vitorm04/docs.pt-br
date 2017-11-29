---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente. Essa informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e a cadeia de caracteres do conjunto de caracteres ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` no `Declare` instrução fornece as informações do conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo. Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Unicode` modificador Especifica que o Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode e deve consultar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres for especificada, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Unicode` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 Não há suporte para esta palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
