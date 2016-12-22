---
title: "Usando operadores de convers&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "operadores de conversão [C#]"
  - "conversões [C#], operadores"
  - "operadores de conversão explícita [C#]"
  - "operadores de conversão implícita [C#]"
  - "operadores [C#], conversão"
  - "conversões definidas pelo usuário [C#]"
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando operadores de convers&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar os operadores de conversão de `implicit` , que são mais fácil de usar, ou os operadores de conversão de `explicit` , que indicam claramente a qualquer um que lê o código que você está convertendo um tipo.  Este tópico demonstra ambos os tipos de operador de conversão.  
  
> [!NOTE]
>  Para obter informações sobre as conversões de tipo simples, consulte [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), ou <xref:System.Convert>.  
  
## Exemplo  
 Este é um exemplo de um operador de conversão explícita.  Este operador converte\-se de tipo <xref:System.Byte> a um tipo de valor chamado `Digit`.  Porque nem todos os bytes podem ser convertidos em um dígito, a conversão explícita é, o que significa que uma conversão deve ser usada, conforme mostrado no método de `Main` .  
  
 [!code-cs[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## Exemplo  
 Este exemplo demonstra um operador de conversão implícita definir um operador de conversão que desfça o que o exemplo anterior fez: converte\-se de uma classe de valor `Digit` chamada para o tipo integral de <xref:System.Byte> .  Porque qualquer dígito puder ser convertido em <xref:System.Byte>, não há necessidade de forçar usuários para estar explícito sobre a conversão.  
  
 [!code-cs[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [is](../../../csharp/language-reference/keywords/is.md)