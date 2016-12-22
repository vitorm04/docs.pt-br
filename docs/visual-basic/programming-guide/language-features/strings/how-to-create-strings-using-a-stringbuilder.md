---
title: "Como criar cadeias de caracteres usando StringBuilder no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Classe StringBuilder"
  - "cadeias de caracteres {Visual Basic], Usando StringBuilder"
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar cadeias de caracteres usando StringBuilder no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esse exemplo constrói uma cadeia de caracteres extensa a partir de várias cadeias menores utilizando a classe <xref:System.Text.StringBuilder>.  A classe <xref:System.Text.StringBuilder> é mais eficiente que o operador `&=` para realizar concatenação de muitas cadeias de caracteres.  
  
## Exemplo  
 O exemplo a seguir cria uma instância da classe <xref:System.Text.StringBuilder>, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retona sua representação em cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## Consulte também  
 [Usando a classe StringBuilder](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)   
 [Operador &\=](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Criando novas cadeias de caracteres](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [Manipulando cadeias de caracteres](../Topic/Manipulating%20Strings%20in%20the%20.NET%20Framework.md)   
 [Strings Sample](http://msdn.microsoft.com/pt-br/be9e82a3-dc95-4aaa-9396-61b66e467e02)