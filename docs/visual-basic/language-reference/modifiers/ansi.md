---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c7037acac58de56a396bd89f595ef897743ff4e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores American National Standards Institute (ANSI), independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente. Essa informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e a cadeia de caracteres do conjunto de caracteres ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` no `Declare` instrução fornece as informações de conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo. Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Ansi` modificador Especifica que o Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores ANSI e deve consultar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres for especificada, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Ansi` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 Não há suporte para esta palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
