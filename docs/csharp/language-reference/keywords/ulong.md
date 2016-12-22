---
title: "ulong (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "ulong_CSharpKeyword"
  - "ulong"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave ulong [C#]"
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ulong (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `ulong` palavra\-chave denota um tipo integral que armazena valores de acordo com o tamanho e o intervalo, mostrado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`ulong`|0 a 18,446,744,073,709,551,615|Inteiro de 64 bits sem\-sinal|<xref:System.UInt64?displayProperty=fullName>|  
  
## Literais  
 Você pode declarar e inicializar um `ulong` variável semelhante ao exemplo:  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 Quando um literal inteiro não tem nenhum sufixo, seu tipo é o primeiro desses tipos no qual o seu valor pode ser representado:  [int](../../../csharp/language-reference/keywords/int.md),  [uint](../../../csharp/language-reference/keywords/uint.md),  [longo](../../../csharp/language-reference/keywords/long.md), `ulong`.  No exemplo acima, ele é do tipo `ulong`.  
  
 Você também pode usar os sufixos para especificar o tipo literal de acordo com às seguintes regras:  
  
-   Se você usar l ou l, o tipo do literal inteiro será um  [longo](../../../csharp/language-reference/keywords/long.md) ou `ulong` de acordo com a seu tamanho.  
  
    > [!NOTE]
    >  Você pode usar a letra minúscula "l" como um sufixo.  No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1". Use o "L" para fins de esclarecimento.  
  
-   Se você usar `U` ou `u`, o tipo do literal inteiro será um  [uint](../../../csharp/language-reference/keywords/uint.md) ou `ulong` de acordo com a seu tamanho.  
  
-   Se você usar UL, ul, Ul, uL, LU, lu, Lu ou lU, o tipo do literal inteiro será `ulong`.  
  
     Por exemplo, a saída das três instruções seguintes serão do tipo de sistema `UInt64`, que corresponde ao alias `ulong`:  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 Um uso comum do sufixo é chamando métodos sobrecarregados.  Considere, por exemplo, o seguinte sobrecarregado métodos que usam `ulong` e  [int](../../../csharp/language-reference/keywords/int.md) parâmetros:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 Usando um sufixo com o `ulong` parâmetro garante que o tipo correto é chamado, por exemplo:  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## Conversões  
 Há uma conversão implícita predefinida de `ulong` para  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Não há nenhuma conversão implícita de `ulong` a qualquer tipo integral.  Por exemplo, a instrução a seguir gerará um erro de compilação sem uma conversão explícita:  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Há uma conversão implícita predefinida de  [bytes](../../../csharp/language-reference/keywords/byte.md),  [ushort](../../../csharp/language-reference/keywords/ushort.md),  [uint](../../../csharp/language-reference/keywords/uint.md), ou  [char](../../../csharp/language-reference/keywords/char.md) para `ulong`.  
  
 Além disso, não há nenhuma conversão implícita de tipos de ponto flutuante para `ulong`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre regras de conversão numérica implícito, consulte o [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.UInt64>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)