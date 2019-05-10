---
title: Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes está definido como True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: ca764d5258daf54a7149661549a78b3aca709718
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619812"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Não é possível ler campos delimitados porque aspas duplas não são um delimitador válido quando EscapeQuotes está definido como True
O `TextFieldParser` não é possível ler o arquivo como uma marca de aspas (") foi fornecida como o delimitador e `EscapeQuotes` é definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Defina `EscapeQuotes` como `False`.  
  
## <a name="see-also"></a>Consulte também

- [Método TextFieldParser.SetDelimiters](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [Propriedade Delimiters](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Como: Ler de arquivos de texto separados por vírgula](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
