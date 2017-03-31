---
title: "long (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
dev_langs:
- CSharp
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c28c8308d7ed32f7240f56113a77a0794cb1ba62
ms.lasthandoff: 03/13/2017

---
# <a name="long-c-reference"></a>long (Referência de C#)
A palavra-chave `long` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`long`|–9.223.372.036.854.775.808 a 9.223.372.036.854.775.807|Inteiro de 64 bits com sinal|<xref:System.Int64?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais  
 É possível declarar e inicializar uma variável `long` como neste exemplo:  
  
```  
  
long long1 = 4294967296;  
```  
  
 Quando um literal inteiro não tem sufixo, seu tipo é o primeiro desses tipos em que seu valor pode ser representado: [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), `long`, [ulong](../../../csharp/language-reference/keywords/ulong.md). No exemplo anterior, ele é do tipo `long` porque excede o intervalo de [uint](../../../csharp/language-reference/keywords/uint.md) (consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para os tamanhos de armazenamento de tipos integrais).  
  
 Você também pode usar o sufixo L com o tipo `long` dessa forma:  
  
```  
  
long long2 = 4294967296L;  
```  
  
 Quando você usa o sufixo L, o tipo do literal inteiro é determinado para ser `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md) de acordo com seu tamanho. Nesse caso é `long` porque ele menor do que o intervalo de [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Um uso comum do sufixo é a chamada de métodos sobrecarregados. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `long` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 O uso do sufixo L garante que o tipo correto será chamado, por exemplo:  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 Você pode usar o tipo `long` com outros tipos integrais numéricos na mesma expressão, caso em que a expressão é avaliada como `long` (ou [bool](../../../csharp/language-reference/keywords/bool.md) no caso de expressões relacionais ou boolianas). Por exemplo, a expressão a seguir é avaliada como `long`:  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  Você também pode usar a letra minúscula "l" como sufixo. No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1". Use "L" para fins de clareza.  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `long` para [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Caso contrário, uma conversão deve ser usada. Por exemplo, a instrução a seguir produzirá um erro de compilação sem uma conversão explícita:  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) para `long`.  
  
 Observe também que não há conversão implícita de tipos de ponto flutuante em `long`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```  
  
      long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int64>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
