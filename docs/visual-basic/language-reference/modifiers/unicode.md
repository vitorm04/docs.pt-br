---
title: Unicode (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Unicode
dev_langs:
- VB
helpviewer_keywords:
- Unicode, external references
- Declare statement, marshaling strings
- Unicode keyword
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 14
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
ms.openlocfilehash: fcfdd6973a0dd299485ef48370c07b4afa4bd8ea
ms.lasthandoff: 03/13/2017

---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente. Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres para empacotar strings durante uma chamada ao procedimento externo. Ele também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Unicode` modificador Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode e deve consultar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Unicode` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Anotações de desenvolvedor de dispositivo inteligente  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Automático](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
