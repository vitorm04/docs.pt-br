---
title: Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: 27cbacacefb64d3a9c0257011a188397e83b9186
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582039"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a>Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero
Todas as larguras de campo, exceto o último elemento, devem ser maiores que zero. Uma largura de campo que menor que ou igual a zero no último elemento indica que o último campo é de comprimento variável.  
  
 A operação falhou porque uma largura de campo que não seja o último elemento é definida como zero ou menos. Uma largura de campo que menor que ou igual a zero pode ser usado como o último elemento para indicar que o último campo é de comprimento variável, mas não pode ser usada como qualquer outro elemento.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina a largura do campo como o tamanho correto.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [Como: Ler arquivos de texto de largura fixa](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
