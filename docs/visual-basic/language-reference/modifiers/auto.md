---
title: Automático
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351614"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Especifica que Visual Basic deve empacotar cadeias de caracteres de acordo com .NET Framework regras com base no nome externo do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações que ele deve ter para chamar o procedimento corretamente. Essas informações incluem onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres da cadeia de caracteres que ele usa. A [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece essas informações necessárias.  
  
 A parte `charsetmodifier` na instrução `Declare` fornece as informações de um conjunto de caracteres para o marshaling de cadeias durante uma chamada para o procedimento externo. Ele também afeta como Visual Basic pesquisa o nome do procedimento externo no arquivo externo. O modificador de `Auto` especifica que Visual Basic deve realizar marshaling de cadeia de caracteres de acordo com as regras de .NET Framework e que ele deve determinar o conjunto de caractere base da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se a pesquisa inicial falhar. Para obter mais informações, consulte "conjuntos de caracteres" na [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Se nenhum modificador de conjunto de caracteres for especificado, `Ansi` será o padrão.  
  
## <a name="remarks"></a>Comentários  
 O modificador de `Auto` pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas para desenvolvedores de dispositivos inteligentes  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
