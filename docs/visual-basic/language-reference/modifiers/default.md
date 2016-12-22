---
title: "Padr&#227;o (Visual Basic) | Microsoft Docs"
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
  - "vb.Default"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Default [Visual Basic]"
  - "propriedades padrão"
  - "propriedades padrão, em Visual Basic"
  - "padrões, propriedades"
  - "propriedades [Visual Basic], default"
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Padr&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Identifica uma propriedade como a propriedade padrão de sua classe, estrutura ou interface.  
  
## Comentários  
 Uma classe, estrutura ou interface pode designar no máximo uma de suas propriedades como a *propriedade padrão* , desde que a propriedade aceite pelo menos um parâmetro.  Se o código faz uma referência a uma classe ou estrutura sem especificar um membro, o Visual Basic toma essa referência como propriedade padrão.  
  
 As propriedades padrão podem resultar em uma pequena redução nos caracteres do código\-fonte, mas elas podem deixar seu código mais difícil de ler.  Se o código de chamada não está familiarizado com sua classe ou estrutura, quando ele faz uma referência ao nome de classe ou estrutura não poderá determinar se essa referência acessa a classe ou estrutura em si ou uma propriedade padrão.  Isso pode levar a erros de compilador ou a sutis erros de lógica em tempo de execução.  
  
 Você tanto pode reduzir a chance de erros de propriedade padrão sempre usando a [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) para configurar a verificação do tipo do compilador como `On`.  
  
 Se você estiver planejando usar uma classe ou estrutura predefinidas no seu código, você deve determinar se ela tem uma propriedade padrão, e em caso afirmativo, qual seu nome.  
  
 Por causa dessas desvantagens, você deve considerar não definir as propriedades padrão.  Para legibilidade de código, você deve também considerar sempre referir\-se a todas as propriedades explicitamente, mesmo propriedades padrão.  
  
 O modificador `Default` pode ser utilizado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## Consulte também  
 [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)