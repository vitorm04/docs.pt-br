---
title: "Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes for definida como True"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3644165d0c25189f29f3f878a17b0d9bf4e2623b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes for definida como True
O `TextFieldParser` não é possível ler o arquivo porque um sinal de aspas (") foi fornecida como o delimitador e `EscapeQuotes` é definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina `EscapeQuotes` como `False`.  
  
## <a name="see-also"></a>Consulte também  
 [Método TextFieldParser.SetDelimiters](http://msdn.microsoft.com/en-us/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [Propriedade Delimiters](http://msdn.microsoft.com/en-us/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Como ler a partir de arquivos de texto separados por vírgulas](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
