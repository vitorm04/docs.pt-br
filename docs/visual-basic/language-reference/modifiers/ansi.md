---
title: ANSI (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
dev_langs:
- VB
helpviewer_keywords:
- Declare statement, marshaling strings
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 13
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
ms.openlocfilehash: 0e3ad802a6730f6635d3d862d45e6d25c37344c2
ms.lasthandoff: 03/13/2017

---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Especifica que o Visual Basic deve empacotar todas as strings para valores American National Standards Institute (ANSI) independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente. Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo. Ele também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Ansi` modificador Especifica que o Visual Basic deve empacotar todas as strings para valores ANSI e deve consultar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Ansi` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Anotações de desenvolvedor de dispositivo inteligente  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Automático](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
