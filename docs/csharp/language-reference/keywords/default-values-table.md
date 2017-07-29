---
title: "Tabela de valores padrão (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d609403269a5cbfe6715647a240c44b254a4d8f9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="default-values-table-c-reference"></a>Tabela de valores padrão (Referência de C#)
A tabela a seguir mostra os valores padrão de tipos de valor retornados por construtores padrão. Construtores padrão são invocados por meio do operador `new`, da seguinte maneira:  
  
```  
int myInt = new int();  
```  
  
 A instrução anterior tem o mesmo efeito da instrução a seguir:  
  
```  
int myInt = 0;  
```  
  
 Lembre-se de que não é permitido usar variáveis não inicializadas no C#.  
  
|Tipo de valor|Valor padrão|  
|----------------|-------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`false`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|0|  
|[char](../../../csharp/language-reference/keywords/char.md)|'\0'|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|0,0M|  
|[double](../../../csharp/language-reference/keywords/double.md)|0,0D|  
|[enum](../../../csharp/language-reference/keywords/enum.md)|O valor produzido pela expressão (E)0, em que E é o identificador de enumeração.|  
|[float](../../../csharp/language-reference/keywords/float.md)|0,0F|  
|[int](../../../csharp/language-reference/keywords/int.md)|0|  
|[long](../../../csharp/language-reference/keywords/long.md)|0L|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|0|  
|[short](../../../csharp/language-reference/keywords/short.md)|0|  
|[struct](../../../csharp/language-reference/keywords/struct.md)|O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|0|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|0|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|0|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Tabela de Tipos de Valor](../../../csharp/language-reference/keywords/value-types-table.md)   
 [Tipos de Valor](../../../csharp/language-reference/keywords/value-types.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)

