---
title: "Unicode (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Unicode"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Declare, realizando marshaling em cadeias de caracteres"
  - "palavra-chave Unicode"
  - "Unicode, referências externas"
  - "Unicode, realizando marshaling em cadeias de caracteres"
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unicode (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que o Visual Basic deverá empacotar todas as sequências de caracteres para valores unicode, independentemente do nome do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso à informação que ele precisa para chamar o procedimento corretamente.  Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e o conjunto de caracteres que ele usa.  A [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência para um procedimento externo e fornece esta informação necessária.  
  
 A posição do `charsetmodifier` na declaração `Declare` fornece a informação do conjunto de caracteres para empacotar strings durante a chamada ao procedimento externo.  Isso também afeta o modo como o Visual Basic vasculha o arquivo externo procurando o nome do procedimento externo.  O `Unicode` modificador Especifica que o Visual Basic deve realizar marshaling em todas as seqüências de valores Unicode e pesquisar o procedimento sem modificar seu nome durante a pesquisa.  
  
 Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.  
  
## Comentários  
 O modificador `Unicode` pode ser utilizado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## Anotações Developer Dispositivo Inteligente  
 Esta palavra\-chave não é suportada.  
  
## Consulte também  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)