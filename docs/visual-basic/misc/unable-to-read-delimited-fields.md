---
title: Não é possível ler campos delimitados porque aspas duplas não é um delimitador válido quando EscapeQuotes está definido como True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 29682edb78b848897ac2999f2d84dc1a9c1a3367
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100342"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Não é possível ler campos delimitados porque aspas duplas não é um delimitador válido quando EscapeQuotes está definido como True

O `TextFieldParser` não pode ler a partir do arquivo porque uma aspa (") foi fornecida como o delimitador e `EscapeQuotes` está definida como `True` .  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Defina `EscapeQuotes` como `False`.  
  
## <a name="see-also"></a>Confira também

- [Método TextFieldParser. delimitadores](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [Propriedade TextFieldParser. Delimiters](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Como: ler de arquivos de texto separados por vírgula](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Objeto TextFieldParser](../language-reference/objects/textfieldparser-object.md)
