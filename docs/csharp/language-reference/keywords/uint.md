---
title: uint (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
ms.openlocfilehash: fa0169ad92819cee36832d6c928202eb0dd6733e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288899"
---
# <a name="uint-c-reference"></a>uint (Referência de C#)

A palavra-chave `uint` significa um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`uint`|0 a 4.294.967.295|Inteiro de 32 bits sem sinal|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 **Observação** O tipo `uint` não está em conformidade com CLS. Use `int` sempre que possível.  
  
## <a name="literals"></a>Literais  

Você pode declarar e inicializar uma variável `uint` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário. Se o literal inteiro estiver fora do intervalo de `uint` (ou seja, se for menor que <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 3.000.000.000 representados como literais decimais, hexadecimais e binários são atribuídos a valores `uint`.  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo. 

Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade. 
 - O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.
 - O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo. Um literal decimal não pode ter um sublinhado à esquerda.

Alguns exemplos são mostrados abaixo.

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 Literais inteiros também podem incluir um sufixo que indica o tipo. O sufixo `U` ou 'u' indica um `uint` ou um `ulong`, dependendo do valor numérico do literal. O exemplo a seguir usa o sufixo `u` para indicar um inteiro sem sinal dos dois tipos. Observe que o primeiro literal é um `uint` porque seu valor é menor que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, enquanto o segundo é um `ulong` porque seu valor é maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado: 

1. [int](int.md)
2. `uint`
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `uint` para [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Por exemplo:  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Há uma conversão implícita predefinida de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) para `uint`. Caso contrário, você deve usar uma conversão. Por exemplo, a instrução de atribuição a seguir produzirá um erro de compilação sem uma conversão:  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 Observe também que não há conversão implícita de tipos de ponto flutuante em `uint`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt32>  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
