---
title: Tabela de tipos internos (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 7407d18c58dd3d12337c6845627d83f02eaf7fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="built-in-types-table-c-reference"></a>Tabela de tipos internos (Referência de C#)
A tabela a seguir mostra as palavras-chave para tipos internos do C#, que são aliases de tipos predefinidos no namespace <xref:System>.  
  
|Tipo de C#|Tipo do .NET Framework|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Comentários  
 Todos os tipos na tabela, exceto `object` e `string`, são referidos como tipos simples.  
  
 As palavras-chave de tipo C# e seus aliases são intercambiáveis. Por exemplo, é possível declarar uma variável de inteiro usando uma das seguintes declarações:  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Para exibir o tipo real para qualquer tipo de C#, use o método do sistema `GetType()`. Por exemplo, a instrução a seguir exibe o alias do sistema que representa o tipo de `myVariable`:  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 Também é possível usar o operador [typeof](../../../csharp/language-reference/keywords/typeof.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)  
 [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tabela de formatação de resultados numéricos](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
