---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 491bbb24be8e6a3044b0a433c5ad262596ae00d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655277"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora de seu projeto, o compilador do Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente. Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` parte o `Declare` instrução fornece a informação de conjunto de caracteres em cadeias de caracteres de marshaling durante uma chamada ao procedimento externo. Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Unicode` modificador Especifica que o Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode e deve consultar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Unicode` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também
- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
