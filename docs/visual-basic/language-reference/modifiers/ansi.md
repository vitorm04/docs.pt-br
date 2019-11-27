---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344734"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores de American National Standards Institute (ANSI), independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente. Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa. A [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.  
  
 A parte `charsetmodifier` na instrução `Declare` fornece as informações de um conjunto de caracteres para o marshaling de cadeias durante uma chamada para o procedimento externo. Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo. O modificador de `Ansi` especifica que Visual Basic deve realizar marshaling de todas as cadeias de caracteres para valores ANSI e deve procurar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.  
  
## <a name="remarks"></a>Comentários  
 O modificador de `Ansi` pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas para desenvolvedores de dispositivos inteligentes  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
