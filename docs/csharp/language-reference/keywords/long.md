---
title: "long (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "long_CSharpKeyword"
  - "long"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave long [C#]"
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# long (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `long` palavra\-chave denota um tipo integral que armazena valores de acordo com o tamanho e o intervalo, mostrado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`long`|–9, 223, 372, 036, 854, 775, 808 para 9.223.372.036.854.775.807|Inteiro assinado de 64 bits|<xref:System.Int64?displayProperty=fullName>|  
  
## Literais  
 Você pode declarar e inicializar um `long` variável semelhante ao exemplo:  
  
```  
  
long long1 = 4294967296;  
```  
  
 Quando um literal inteiro não tem nenhum sufixo, seu tipo é o primeiro desses tipos no qual o seu valor pode ser representado:  [int](../../../csharp/language-reference/keywords/int.md),  [uint](../../../csharp/language-reference/keywords/uint.md), `long`,  [ulong](../../../csharp/language-reference/keywords/ulong.md).  No exemplo anterior, ele é do tipo `long` porque ele excede o intervalo de  [uint](../../../csharp/language-reference/keywords/uint.md) \(consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para os tamanhos de armazenamento dos tipos integrais\).  
  
 Você também pode usar o sufixo l com o `long` tipo como este:  
  
```  
  
long long2 = 4294967296L;  
```  
  
 Quando você usa o sufixo L, o tipo do inteiro literal é determinado para ser uma `long` ou  [ulong](../../../csharp/language-reference/keywords/ulong.md) de acordo com a seu tamanho.  No caso em que ele é `long` porque ele menor do que o intervalo de  [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Um uso comum do sufixo é chamando métodos sobrecarregados.  Considere, por exemplo, o seguinte sobrecarregado métodos que usam `long` e  [int](../../../csharp/language-reference/keywords/int.md) parâmetros:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 Usar o sufixo l garante que o tipo correto é chamado, por exemplo:  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 Você pode usar o `long` tipo com outros tipos numéricos de integrais na mesma expressão, nesse caso, a expressão é avaliado como `long` \(ou  [bool](../../../csharp/language-reference/keywords/bool.md) no caso de expressões booleanas ou relacionais\).  Por exemplo, a seguinte expressão for avaliada como `long`:  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  Você também pode usar a letra minúscula "l" como um sufixo.  No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1". Use o "L" para fins de esclarecimento.  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
## Conversões  
 Há uma conversão implícita predefinida de `long` para  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  Caso contrário, a projeção de deve ser usada.  Por exemplo, a instrução a seguir gerará um erro de compilação sem uma conversão explícita:  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Há uma conversão implícita predefinida de  [sbyte](../../../csharp/language-reference/keywords/sbyte.md),  [bytes](../../../csharp/language-reference/keywords/byte.md),  [curto](../../../csharp/language-reference/keywords/short.md),  [ushort](../../../csharp/language-reference/keywords/ushort.md),  [int](../../../csharp/language-reference/keywords/int.md),  [uint](../../../csharp/language-reference/keywords/uint.md), ou  [char](../../../csharp/language-reference/keywords/char.md) para `long`.  
  
 Observe também que não há nenhuma conversão implícita de tipos de ponto flutuante para `long`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
  
        long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Int64>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)