---
title: "int (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "int_CSharpKeyword"
  - "int"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave int [C#]"
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# int (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave de `int` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Size \(Tamanho\)|tipo do .NET Framework|Valor padrão|  
|----------|---------------|----------------------|----------------------------|------------------|  
|`int`|\-2.147.483.648 a 2.147.483.647|Inteiro de 32 bits com sinal|<xref:System.Int32?displayProperty=fullName>|0|  
  
## Literais  
 Você pode declarar e inicializar uma variável do tipo `int` como este exemplo:  
  
```  
  
int i = 123;  
```  
  
 Quando um literal inteiro não tem nenhum sufixo, seu tipo é o primeiro desses tipos em que o valor pode ser representado: `int`, [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md).  Nesse exemplo, é do tipo `int`.  
  
## Conversões  
 Há uma conversão implícita predefinida de `int` a [long](../../../csharp/language-reference/keywords/long.md), a [float](../../../csharp/language-reference/keywords/float.md), a [double](../../../csharp/language-reference/keywords/double.md), ou a [decimal](../../../csharp/language-reference/keywords/decimal.md).  Por exemplo:  
  
```  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), de [byte](../../../csharp/language-reference/keywords/byte.md), de [short](../../../csharp/language-reference/keywords/short.md), de [ushort](../../../csharp/language-reference/keywords/ushort.md), ou de [char](../../../csharp/language-reference/keywords/char.md) a `int`.  Por exemplo, a seguinte declaração de atribuição irá gerar um erro de compilação sem uma conversão:  
  
```  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 Observe também que não existe conversão implícita de tipos de ponto flutuante a `int`.  Por exemplo, a seguinte declaração gera um erro do compilador a menos que uma conversão explícita é usada:  
  
```  
  
        int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 Para obter mais informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integral, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Int32>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)