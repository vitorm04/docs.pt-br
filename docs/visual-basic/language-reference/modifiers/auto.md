---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Especifica que Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework com base no nome externo do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente. Essa informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e a cadeia de caracteres do conjunto de caracteres ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` no `Declare` instrução fornece as informações de conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo. Isso também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Auto` modificador Especifica Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework e que ele deve determinar o caractere de base definido da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se inicial de pesquisa falhará. Para obter mais informações, consulte "Conjuntos de caracteres" [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Se nenhum modificador de conjunto de caracteres for especificada, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Auto` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 Não há suporte para esta palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
