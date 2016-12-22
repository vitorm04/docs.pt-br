---
title: "Conven&#231;&#245;es tipogr&#225;ficas e de c&#243;digo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "práticas recomendadas, convenções de codificação"
  - "convenções de codificação, Visual Basic"
  - "convenções, documentação"
  - "convenções, codificação do Visual Basic"
  - "convenções de documento"
  - "convenções tipográficas"
  - "código do Visual Basic, convenções"
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conven&#231;&#245;es tipogr&#225;ficas e de c&#243;digo (Visual Basic)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

A documentação do Visual Basic usa as seguintes convenções tipográficas e de código.  
  
## Convenções tipográficas  
  
|Exemplo|Descrição|  
|-------------|---------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Palavras\-chave específicas da linguagem e membros de tempo de execução têm letras maiúsculas iniciais e são formatados como mostrado neste exemplo.|  
|SmallProject, ButtonCollection \(excluir \-\>\)|As palavras e frases que você é instruído a digitar são formatadas como mostrado neste exemplo.|  
|[Instrução Module](../../visual-basic/language-reference/statements/module-statement.md)|Links que você pode clicar para ir para outra página da Ajuda são formatados como mostrado neste exemplo.|  
|*object*, *variableName*, `argumentList`|Espaços reservados para informações que você fornece são formatados como mostrado neste exemplo.|  
|\[ Sombras\], \[*expressionList*\]|Na sintaxe, itens opcionais estão entre colchetes.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Na sintaxe, quando você deve fazer uma escolha entre dois ou mais itens, os itens são colocados entre chaves e separados por barras verticais.<br /><br /> Você deve selecionar um, e somente um, dos itens.|  
|\[ `Protected` &#124; `Friend` \]|Na sintaxe, quando você tem a opção de selecionar entre dois ou mais itens, os itens são colocados entre colchetes e separados por barras verticais.<br /><br /> Você pode selecionar qualquer combinação dos itens, ou nenhum item.|  
|\[{ `ByVal` &#124; `ByRef` }\]|Na sintaxe, quando você pode selecionar não mais do que um item, mas também pode omitir os itens completamente, os itens são colocados entre colchetes circundados por chaves e separados por barras verticais.|  
|*memberName* 1, *memberName*2, *memberName*3|Várias instâncias do mesmo espaço reservado são diferenciadas por subscritos, conforme mostrado no exemplo.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|Na sintaxe, reticências \(...\) são usadas para indicar um número indefinido de itens do tipo imediatamente na frente das reticências.<br /><br /> No código, reticências significam código omitido para fins de clareza.|  
|ESC, ENTER|Nomes de teclas e sequências de teclas no teclado aparecem com todas as letras maiúsculas.|  
|ALT\+F1|Quando o sinal de mais \(\+\) aparecer entre nomes de teclas, você deve manter uma tecla ao pressionar a outra.  Por exemplo, ALT\+F1 significa manter pressionada a tecla ALT enquanto pressiona a tecla F1.|  
  
## Convenções de código  
  
|Exemplo|Descrição|  
|-------------|---------------|  
|`sampleString = "Hello, world!"`|Exemplos de código aparecem em uma fonte de densidade fixa e são formatados como mostrado neste exemplo.|  
|A instrução anterior define o valor de `sampleString` como "Hello, world\!"|Elementos de código em um texto explicativo aparecem em uma fonte de densidade fixa, conforme mostrado no exemplo.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Comentários do código são introduzidos por um apóstrofo \('\) ou pela palavra\-chave REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Um espaço seguido por um sublinhado \(\_\) ao final de uma linha indica que a instrução continua na linha seguinte.|  
  
## Consulte também  
 [Referência da linguagem Visual Basic](../../visual-basic/language-reference/index.md)   
 [Palavras\-chave](../../visual-basic/language-reference/keywords/index.md)   
 [Membros da biblioteca em tempo de execução do Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)   
 [Convenções de nomenclatura do Visual Basic](../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)   
 [Comentários no código](../../visual-basic/programming-guide/program-structure/comments-in-code.md)