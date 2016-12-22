---
title: "Como validar cadeias de caracteres que representam datas ou horas (Visual Basic) | Microsoft Docs"
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
  - "tipo de dados String, validação"
  - "cadeias de caracteres {Visual Basic], validando"
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O seguinte código exemplo define um `Boolean` valor que indica se uma seqüência de caracteres representa uma data ou hora válida.  
  
## Exemplo  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## Compilando o código  
 Substitua `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar.  Você pode substituir a seqüência de caracteres por outra seqüência codificada por um `String` ou variável, com um método que retorna uma seqüência de caracteres, tais como `InputBox`.  
  
## Programação robusta  
 Use esse método para validar a seqüência de caracteres antes de tentar converter o `String` para um `DateTime` variável.  Verificando a data ou hora pela primeira vez, você pode evitar a gerar uma exceção em tempo de execução.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>   
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>   
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)