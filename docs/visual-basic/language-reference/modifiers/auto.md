---
title: "Automático (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Auto
dev_langs:
- VB
helpviewer_keywords:
- Auto keyword, external references
- Declare statement, marshaling strings
- Auto keyword
- Auto keyword, marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 336cfe1c8394c6f1d6dc8efc99d1ae410d146f0c
ms.lasthandoff: 03/13/2017

---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Especifica que o Visual Basic deve empacotar cadeias de caracteres de acordo com as regras do .NET Framework com base no nome externo do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente. Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa. O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo. Ele também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo. O `Auto` modificador Especifica Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework e que ele deve determinar o caractere base definido da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se a pesquisa inicial falhar. Para obter mais informações, consulte "Conjuntos de caracteres" [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.  
  
## <a name="remarks"></a>Comentários  
 O `Auto` modificador pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Anotações de desenvolvedor de dispositivo inteligente  
 Não há suporte para essa palavra-chave.  
  
## <a name="see-also"></a>Consulte também  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
