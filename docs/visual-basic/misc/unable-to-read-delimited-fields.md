---
title: Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes for definida como True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 66116e6f3d8338db3884cd375aeb880930c8d861
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639279"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes for definida como True
O `TextFieldParser` não é possível ler o arquivo porque um sinal de aspas (") foi fornecida como o delimitador e `EscapeQuotes` é definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina `EscapeQuotes` como `False`.  
  
## <a name="see-also"></a>Consulte também  
 [Método TextFieldParser.SetDelimiters](http://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [Propriedade Delimiters](http://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Como ler a partir de arquivos de texto separados por vírgulas](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
