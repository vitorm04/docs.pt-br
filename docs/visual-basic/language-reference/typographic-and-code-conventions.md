---
title: "Tipográficas e de código convenções (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- typographic conventions
- document conventions
- conventions, documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: 17
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
ms.openlocfilehash: 44a1f105b0e0eca9923e4aa427e120274050bc4b
ms.lasthandoff: 03/13/2017

---
# <a name="typographic-and-code-conventions-visual-basic"></a>Convenções tipográficas e de código (Visual Basic)
Documentação do Visual Basic usa as seguintes tipográficos e convenções de código.  
  
## <a name="typographic-conventions"></a>Convenções tipográficas  
  
|Exemplo|Descrição|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Palavras-chave e membros de tempo de execução têm letras maiusculas iniciais e são formatados como mostrado neste exemplo.|  
|**SmallProject**, **ButtonCollection**|Palavras e frases que você é instruído a digitar são formatados como mostrado neste exemplo.|  
|[Instrução Module](../../visual-basic/language-reference/statements/module-statement.md)|Links, que você pode clicar para ir para outra página de ajuda são formatados como mostrado neste exemplo.|  
|*objeto*, *variableName*,`argumentList`|Espaços reservados para informações que você fornece são formatados como mostrado neste exemplo.|  
|[Sombras], [ *expressionList* ]|Na sintaxe, itens opcionais estão entre colchetes.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Na sintaxe, quando você deve fazer uma escolha entre dois ou mais itens, os itens são colocados entre chaves e separados por barras verticais.<br /><br /> Você deve selecionar um e somente um dos itens.|  
|[ `Protected` &#124; `Friend` ]|Na sintaxe, quando você tem a opção de selecionar entre dois ou mais itens, os itens são colocados entre colchetes e separados por barras verticais.<br /><br /> Você pode selecionar qualquer combinação dos itens, ou nenhum item.|  
|[{ `ByVal` &#124; `ByRef` }]|Na sintaxe, quando você pode selecionar não mais do que um item, mas você também pode omitir os itens completamente, os itens estão entre colchetes circundados por chaves e separados por barras verticais.|  
|*nome do membro*1, *memberName*2, *memberName*3|Várias instâncias do mesmo espaço reservado são diferenciadas por subscritos, conforme mostrado no exemplo.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|Na sintaxe, reticências (...) é usado para indicar um número indefinido de itens do tipo imediatamente na frente das reticências.<br /><br /> No código, reticências significam código omitido para fins de clareza.|  
|ESC, DIGITE|Os nomes de chave e sequências de teclas no teclado aparecem em letras maiusculas.|  
|ALT + F1|Quando o sinal de mais (+) aparecer entre nomes de chave, você deve manter uma tecla ao pressionar a outra. Por exemplo, ALT + F1 significa manter pressionada a tecla ALT enquanto pressiona a tecla F1.|  
  
## <a name="code-conventions"></a>Convenções de código  
  
|Exemplo|Descrição|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Exemplos de código aparecem em uma fonte de densidade fixa e são formatados como mostrado neste exemplo.|  
|A instrução anterior define o valor de `sampleString` para "Hello, world!"|Elementos de código em um texto explicativo aparecem em uma fonte de densidade fixa, conforme mostrado neste exemplo.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Comentários de código são introduzidos por um apóstrofo (') ou a palavra-chave REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Um espaço seguido por um sublinhado (_) ao final de uma linha indica que a instrução continua na linha seguinte.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linguagem do Visual Basic](../../visual-basic/language-reference/index.md)   
 [Palavras-chave](../../visual-basic/language-reference/keywords/index.md)   
 [Membros de biblioteca de tempo de execução do Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)   
 [Convenções de nomenclatura do Visual Basic](../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Como: quebrar e combinar instruções no código](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Comentários no Código](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
