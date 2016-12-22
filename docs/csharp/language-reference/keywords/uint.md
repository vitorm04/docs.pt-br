---
title: "uint (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "uint"
  - "uint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave uint [C#]"
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# uint (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `uint` palavra\-chave significa tipo integral que armazena valores de acordo com o tamanho e o intervalo, mostrado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`uint`|0 a 4,294,967,295|Inteiro de 32 bits sem\-sinal|<xref:System.UInt32?displayProperty=fullName>|  
  
 **Nota** a `uint` o tipo não é compatível com CLS.  Use `int` sempre que possível.  
  
## Literais  
 Você pode declarar e inicializar uma variável do tipo `uint` , como neste exemplo:  
  
```  
  
uint myUint = 4294967290;  
```  
  
 Quando um literal inteiro não tem nenhum sufixo, seu tipo é o primeiro desses tipos no qual o seu valor pode ser representado:  [int](../../../csharp/language-reference/keywords/int.md), `uint`,  [longo](../../../csharp/language-reference/keywords/long.md),  [ulong](../../../csharp/language-reference/keywords/ulong.md).  Neste exemplo, é `uint`:  
  
```  
  
uint uInt1 = 123;  
```  
  
 Você também pode usar o sufixo u ou U, como este:  
  
```  
  
uint uInt2 = 123U;  
```  
  
 Quando você usa o sufixo `U` ou `u`, o tipo do literal é determinado para ser uma `uint` ou `ulong` ao valor numérico do literal.  Por exemplo:  
  
```  
Console.WriteLine(44U.GetType());  
Console.WriteLine(323442434344U.GetType());  
```  
  
 Esse código exibe `System.UInt32`, em seguida, `System.UInt64` – a base tipos para `uint` e `ulong` respectivamente – porque o segundo literal é muito grande para ser armazenadas pelo `uint` tipo.  
  
## Conversões  
 Há uma conversão implícita predefinida de `uint` para  [longo](../../../csharp/language-reference/keywords/long.md),  [ulong](../../../csharp/language-reference/keywords/ulong.md),  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  Por exemplo:  
  
```  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Há uma conversão implícita predefinida de  [bytes](../../../csharp/language-reference/keywords/byte.md),  [ushort](../../../csharp/language-reference/keywords/ushort.md), ou  [char](../../../csharp/language-reference/keywords/char.md) para `uint`.  Caso contrário, você deve usar uma projeção.  Por exemplo, a seguinte instrução de atribuição produzirá um erro de compilação sem uma conversão:  
  
```  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 Observe também que não há nenhuma conversão implícita de tipos de ponto flutuante para `uint`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre regras de conversão numérica implícito, consulte o [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.UInt32>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)