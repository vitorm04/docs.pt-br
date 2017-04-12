---
title: "Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes for definida como True | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b378083540ea95a883b13d8bd27993f44167499
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes for definida como True
O `TextFieldParser` não é possível ler do arquivo porque uma aspas (") foi fornecida como o delimitador e `EscapeQuotes` é definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Set `EscapeQuotes` to `False`.  
  
## <a name="see-also"></a>Consulte também  
 [Método TextFieldParser.SetDelimiters](http://msdn.microsoft.com/en-us/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [Propriedade Delimiters](http://msdn.microsoft.com/en-us/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [Como: ler arquivos de texto delimitado por vírgula](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
