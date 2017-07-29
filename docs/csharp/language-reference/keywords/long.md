---
title: "long (Referência de C#)"
ms.date: 2017-03-14
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5f7d2d6a3d5781b4e120b8399c7206d4429dd98e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="long-c-reference"></a>long (Referência de C#)

`long` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`long`|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807|Inteiro de 64 bits com sinal|<xref:System.Int64?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais 

Você pode declarar e inicializar uma variável `long` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela. 

No exemplo a seguir, inteiros iguais a 4.294.967.296 representados como literais decimais, hexadecimais e binários são atribuídos a valores `long`.  
  
[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo. 

Começando com o C# 7, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Literais inteiros também podem incluir um sufixo que indica o tipo. O sufixo `L` indica um `long`. O exemplo a seguir usa o sufixo `L` para indicar um inteiro longo:
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Você também pode usar a letra minúscula "l" como sufixo. No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1". Use "L" para fins de clareza.  
  
 Quando você usa o sufixo `L`, o tipo do inteiro integral é determinado para ser `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md), dependendo de seu tamanho. Nesse caso é `long` porque ele menor do que o intervalo de [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Um uso comum do sufixo é para chamar métodos sobrecarregados. Por exemplo, os métodos sobrecarregados a seguir têm parâmetros do tipo `long` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 O sufixo `L` garante que a sobrecarga correta é chamada:  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

O literal 4294967296 no exemplo anterior é do tipo `long` porque excede o intervalo de [uint](../../../csharp/language-reference/keywords/uint.md) (consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para os tamanhos de armazenamento de tipos integrais).  
  
 Se você usar o tipo `long` com outros tipos integrais na mesma expressão, a expressão será avaliada como `long` (ou [bool](../../../csharp/language-reference/keywords/bool.md) no caso de expressões relacionais ou boolianas). Por exemplo, a expressão a seguir é avaliada como `long`:  
  
```csharp  
898L + 88  
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `long` para [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Caso contrário, uma conversão deve ser usada. Por exemplo, a instrução a seguir produzirá um erro de compilação sem uma conversão explícita:  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) para `long`.  
  
 Observe também que não há conversão implícita de tipos de ponto flutuante em `long`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int64>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

