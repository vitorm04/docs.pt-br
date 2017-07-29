---
title: "sbyte (Referência de C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
dev_langs:
- CSharp
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
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
ms.openlocfilehash: 69741a5b9556c769156687584041667312550c17
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="sbyte-c-reference"></a>sbyte (Referência de C#)

`sbyte` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 a 127|Inteiro de 8 bits com sinal|<xref:System.SByte?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais  

Você pode declarar e inicializar uma variável `sbyte` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela. 

No exemplo a seguir, inteiros iguais a -102 representados como literais decimais, hexadecimais e binários são convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `sbyte`.    
  
[!code-cs[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo.

Começando com o C# 7, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-cs[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

Se o literal inteiro estiver fora do intervalo de `sbyte` (ou seja, se for menor que <xref:System.SByte.MinValue?displayProperty=fullName> ou maior que <xref:System.SByte.MaxValue?displayProperty=fullName>, ocorrerá um erro de compilação. Quando um literal inteiro não tem sufixo, seu tipo é o primeiro desses tipos em que seu valor pode ser representado: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md). Isso significa que, neste exemplo, os literais numéricos `0x9A` e `0b10011010` são interpretados como inteiros com sinal de 32 bits com um valor de 156, que excede <xref:System.SByte.MaxValue?displayProperty=fullName>. Por causa disso, o operador de conversão é necessário e a atribuição deve ocorrer em um contexto [não selecionado](unchecked.md). 

## <a name="compiler-overload-resolution"></a>Resolução de sobrecarga do compilador

 Uma conversão deve ser usada ao chamar métodos sobrecarregados. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `sbyte` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 O uso da conversão `sbyte` garante que o tipo correto será chamado, por exemplo:  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `sbyte` para [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Não é possível converter implicitamente tipos numéricos não literais com tamanho de armazenamento maior em `sbyte` (consulte a [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para ver os tamanhos de armazenamento de tipos integrais). Considere, por exemplo, as duas variáveis `sbyte` `x` e `y` a seguir:  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como [int](../../../csharp/language-reference/keywords/int.md) por padrão.  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Para corrigir esse problema, converta a expressão como no exemplo a seguir:  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Observe também que não há conversão implícita de tipos de ponto flutuante em `sbyte`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.SByte>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

