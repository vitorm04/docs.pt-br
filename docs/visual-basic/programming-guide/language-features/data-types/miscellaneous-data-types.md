---
title: "Tipos de dados diversos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "tipos de dados [Visual Basic], escolha"
  - "tipo de dados Object, tipos de dados"
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados diversos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece vários tipos de dados que não estão familiarizados com números ou caracteres.  Em vez disso, eles lidam com dados especializados, como valores Sim\/Não, valores de data\/hora e endereços de objeto.  
  
 Para obter uma tabela que mostre uma comparação lado\-a\-lado dos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Tipo booleano  
 O [Tipo de dados booliano](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) é um valor sem\-sinal que é interpretado como `True` ou `False`.  Sua largura de dados depende da plataforma de implementação.  Se uma variável pode conter apenas valores de dois estados, como Verdadeiro\/Falso, Sim\/Não, ou ligado\/desligado, declare\-a como `Boolean`.  
  
## Tipo de dados  
 O [Tipo de dados Data](../../../../visual-basic/language-reference/data-types/date-data-type.md) é um valor de 64 bits que contém as informações tanto de data como de hora.  Cada incremento representa 100 nanossegundos de tempo decorrido desde o início \(12: 00\) de 1 º de janeiro do ano 1 no calendário gregoriano.  Se uma variável pode conter um valor de data, um valor de tempo, ou ambos, declare\-a como `Date`.  
  
## Tipo de objeto  
 O [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) é um endereço de 32 bits que aponta para uma instância de objeto dentro de seu aplicativo ou em algum outro aplicativo.  Uma variável `Object` pode referir\-se a qualquer objeto que seu aplicativo reconheça, ou aos dados de qualquer tipo de dados.  Isso inclui os  *tipos de valor*, como `Integer`, `Boolean`e as instâncias de estrutura, e  *tipos de referência*, que são instâncias de objetos criados a partir de classes, como `String` e <xref:System.Windows.Forms.Form>e instâncias de matriz.  
  
 Se uma variável armazena um ponteiro para uma instância de uma classe que você não conheça em tempo de compilação, ou se ele pode apontar para dados de vários tipos de dados, declare\-a como `Object`.  
  
 A vantagem do `Object` tipo de dados é que você pode usá\-lo para armazenar dados de qualquer tipo de dados.  A desvantagem é que você provoca operações extras que levam mais tempo de execução e deixa seu aplicativo mais lento.  Se você usar uma variável `Object`para tipos de valor, você provoca *boxing* e  *unboxing* .  Se você usá\-la para tipos de referência, você provoca  *vinculação atrasada.*  
  
## Consulte também  
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Tipos de dados de caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Associação antecipada e tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)