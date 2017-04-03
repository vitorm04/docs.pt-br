---
title: "double (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- double
- double_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
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
ms.openlocfilehash: ccdd29c78a3cdc9d32fa08b1be94eecd717418fc
ms.lasthandoff: 03/13/2017

---
# <a name="double-c-reference"></a>double (Referência de C#)
A palavra-chave `double` indica um tipo simples que armazena valores de ponto flutuante de 64 bits. A tabela a seguir mostra a precisão e o intervalo aproximado do tipo `double`.  
  
|Tipo|Intervalo aproximado|Precisão|Tipo do .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup>|15 a 16 dígitos|<xref:System.Double?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais  
 Por padrão, um literal numérico real no lado direito do operador de atribuição é tratado como `double`. No entanto, se você quiser que um número inteiro seja tratado como `double`, use o sufixo d ou D, por exemplo:  
  
```  
  
double x = 3D;  
```  
  
## <a name="conversions"></a>Conversões  
 Você pode misturar tipos integrais numéricos e tipos de ponto flutuante em uma expressão. Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante. A avaliação da expressão é executada de acordo com as regras a seguir:  
  
-   Se um dos tipos de ponto flutuantes for `double`, a expressão será avaliada como `double` ou [bool](../../../csharp/language-reference/keywords/bool.md) em expressões relacionais ou boolianas.  
  
-   Se não houver um tipo `double` na expressão, ela será avaliada como [float](../../../csharp/language-reference/keywords/float.md) ou [bool](../../../csharp/language-reference/keywords/bool.md) em expressões relacionais ou boolianas.  
  
 Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:  
  
-   Zero positivo e negativo.  
  
-   Infinito positivo e negativo.  
  
-   Valor diferente de um número (NaN).  
  
-   O conjunto finito de valores diferentes de zero.  
  
 Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um [int](../../../csharp/language-reference/keywords/int.md), um [short](../../../csharp/language-reference/keywords/short.md), um [float](../../../csharp/language-reference/keywords/float.md) e um `double` são adicionados, levando a um resultado `double`.  
  
 [!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de tipos de ponto flutuante](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
