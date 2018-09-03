---
title: int (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 95ac267bc70d2e7873593c08e0b10cb50fefd8c8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43421957"
---
# <a name="int-c-reference"></a>int (Referência de C#)

`int` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET|  
|----------|-----------|----------|-------------------------|  
|`int`|-2.147.483.648 a 2.147.483.647|Inteiro de 32 bits com sinal|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literais  
 
Você pode declarar e inicializar uma variável `int` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.  Se o literal inteiro estiver fora do intervalo de `int` (ou seja, se for menor que <xref:System.Int32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int32.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação. 

No exemplo a seguir, inteiros iguais a 90.946 representados como literais decimais, hexadecimais e binários são atribuídos a valores `int`.  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo. 

Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade. 
 - O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.
 - O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo. Um literal decimal não pode ter um sublinhado à esquerda.

Alguns exemplos são mostrados abaixo.

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 Literais inteiros também podem incluir um sufixo que denote o tipo, embora não haja nenhum sufixo que indique o tipo `int`. Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado: 

1. `int`
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
 
Nestes exemplos, o literal 90946 é do tipo `int`.
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `int` para [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Por exemplo:  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md)ou [char](../../../csharp/language-reference/keywords/char.md) para `int`. Por exemplo, a instrução de atribuição a seguir produzirá um erro de compilação sem uma conversão:  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 Observe também que não há conversão implícita de tipos de ponto flutuante em `int`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 Para obter mais informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Int32>  
- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
