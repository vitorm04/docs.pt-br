---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344218"
---
# <a name="unicode-visual-basic"></a>Unicode (Visual Basic)
Especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente. Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa. A [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.  
  
 A parte `charsetmodifier` na instrução `Declare` fornece as informações do conjunto de caracteres para empacotar as cadeias durante uma chamada para o procedimento externo. Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo. O modificador de `Unicode` especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores Unicode e deve procurar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.  
  
## <a name="remarks"></a>Comentários  
 O modificador de `Unicode` pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas para desenvolvedores de dispositivos inteligentes  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
