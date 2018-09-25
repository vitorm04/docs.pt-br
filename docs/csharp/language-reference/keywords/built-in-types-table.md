---
title: Tabela de tipos internos (Referência de C#)
description: Palavras-chave para tipos C# internos
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fd9ba878d77bdb219542db55bb38023c60c7bec4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507306"
---
# <a name="built-in-types-table-c-reference"></a>Tabela de tipos internos (Referência de C#)

A tabela a seguir mostra as palavras-chave para tipos internos do C#, que são aliases de tipos predefinidos no namespace <xref:System>.  
  
|Tipo de C#|Tipo .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Comentários

Todos os tipos na tabela, exceto `object` e `string`, são referidos como tipos simples.  
  
As palavras-chave de tipo C# e seus aliases são intercambiáveis. Por exemplo, é possível declarar uma variável de inteiro usando uma das seguintes declarações:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Use o operador [typeof](typeof.md) para obter a instância <xref:System.Type?displayProperty=nameWithType> que representa o tipo especificado:

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tabelas de referência de tipos](reference-tables-for-types.md)
- [Tipos de valor](value-types.md)
- [Tipos de referência](reference-types.md)
- [Tabela de valores padrão](default-values-table.md)
- [dynamic](dynamic.md)
