---
title: Tabela de valores padrão (Referência de C#)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="default-values-table-c-reference"></a>Tabela de valores padrão (Referência de C#)

A tabela a seguir mostra os valores padrão de tipos de valor retornados por construtores padrão. Construtores padrão são invocados por meio do operador `new`, da seguinte maneira:

```csharp
int myInt = new int();
```

A instrução anterior tem o mesmo efeito da instrução a seguir:

```csharp
int myInt = 0;
```

Lembre-se de que não é permitido usar variáveis não inicializadas no C#.

|Tipo de valor|Valor padrão|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0,0D|
|[enum](enum.md)|O valor produzido pela expressão (E)0, em que E é o identificador de enumeração.|
|[float](float.md)|0,0F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="see-also"></a>Consulte também
 [Referência de C#](../index.md)  
 [Guia de Programação em C#](../../programming-guide/index.md)  
 [Tabela de tipos de valor](value-types-table.md)  
 [Tipos de valor](value-types.md)  
 [Tabela de tipos internos](built-in-types-table.md)  
 [Tabelas de referência de tipos](reference-tables-for-types.md)
