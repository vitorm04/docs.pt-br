---
title: "Auto (Visual Basic) | Microsoft Docs"
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
  - "vb.Auto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Auto"
  - "palavra-chave Auto, referências externas"
  - "palavra-chave Auto, realizando marshaling em cadeias de caracteres"
  - "instrução Declare, realizando marshaling em cadeias de caracteres"
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auto (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que o Visual Basic deve empacotar strings de acordo com a.Regras do NET Framework com base no nome externo do procedimento externo que está sendo declarado.  
  
 Quando você chama um procedimento definido fora do seu projeto, o compilador Visual Basic não tem acesso às informações que ele deve ter que chamar o procedimento corretamente.  Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno, e o conjunto de caracteres que ele usa.  A [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência para um procedimento externo e fornece esta informação necessária.  
  
 A posição do `charsetmodifier` na declaração `Declare` fornece a informação do conjunto de caracteres para empacotar strings durante a chamada ao procedimento externo.  Isso também afeta o modo como o Visual Basic vasculha o arquivo externo procurando o nome do procedimento externo.  O `Auto` modificador Especifica que o Visual Basic deve empacotar strings de acordo com a.NET Framework regras e que ele deve determinar o caractere base definido da plataforma de tempo de execução e possivelmente modificam o nome do procedimento externo se a pesquisa inicial falhar.  Para obter mais informações, consulte "Conjuntos de caracteres" [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.  
  
## Comentários  
 O modificador `Auto` pode ser utilizado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## Anotações Developer Dispositivo Inteligente  
 Esta palavra\-chave não é suportada.  
  
## Consulte também  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)