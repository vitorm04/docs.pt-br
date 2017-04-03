---
title: "ulong (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
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
ms.openlocfilehash: 36de0add1d7fdf58745c65d231f3789c532ab69f
ms.lasthandoff: 03/13/2017

---
# <a name="ulong-c-reference"></a>ulong (Referência de C#)
A palavra-chave `ulong` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 a 18.446.744.073.709.551.615|Inteiro de 64 bits sem sinal|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais  
 É possível declarar e inicializar uma variável `ulong` como neste exemplo:  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 Quando um literal inteiro não tem sufixo, seu tipo é o primeiro desses tipos em que seu valor pode ser representado: [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), `ulong`. No exemplo acima, ele é do tipo `ulong`.  
  
 Você também pode usar sufixos para especificar o tipo do literal de acordo com as regras a seguir:  
  
-   Se você usar L ou l, o tipo do inteiro literal será [long](../../../csharp/language-reference/keywords/long.md) ou `ulong`, de acordo com seu tamanho.  
  
    > [!NOTE]
    >  Você pode usar a letra minúscula "l" como sufixo. No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1". Use "L" para fins de clareza.  
  
-   Se você usar `U` ou `u`, o tipo do inteiro literal será [uint](../../../csharp/language-reference/keywords/uint.md) ou `ulong`, de acordo com seu tamanho.  
  
-   Se você usar UL, ul, Ul, uL, LU, lu, Lu ou lU, o tipo do inteiro literal será `ulong`.  
  
     Por exemplo, a saída das três instruções a seguir será o tipo do sistema `UInt64`, que corresponde ao alias `ulong`:  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 Um uso comum do sufixo é a chamada de métodos sobrecarregados. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `ulong` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 Usar o sufixo com o parâmetro `ulong` garante que o tipo correto seja chamado, por exemplo:  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `ulong` para [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Não há nenhuma conversão implícita de `ulong` em qualquer tipo integral. Por exemplo, a instrução a seguir produzirá um erro de compilação sem uma conversão explícita:  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Há uma conversão implícita predefinida de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) em `ulong`.  
  
 Além disso, não há conversão implícita de tipos de ponto flutuante em `ulong`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt64>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
