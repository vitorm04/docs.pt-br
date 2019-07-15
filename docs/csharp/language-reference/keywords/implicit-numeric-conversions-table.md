---
title: Tabela de conversões numéricas implícitas – Referência de C#
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 516505ccacfd2a8a5c275b0de033e1316fa06d3a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661328"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela de conversões numéricas implícitas (Referência de C#)

A tabela a seguir mostra as conversões implícitas predefinidas entre tipos numéricos do .NET.
  
|De|Para|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|  
|[byte](../builtin-types/integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[short](../builtin-types/integral-numeric-types.md)|`int`, `long`, `float`, `double` ou `decimal`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[int](../builtin-types/integral-numeric-types.md)|`long`, `float`, `double` ou `decimal`|  
|[uint](../builtin-types/integral-numeric-types.md)|`long`, `ulong`, `float`, `double` ou `decimal`|  
|[long](../builtin-types/integral-numeric-types.md)|`float`, `double` ou `decimal`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`float`, `double` ou `decimal`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`double`|  
  
## <a name="remarks"></a>Comentários  

- Qualquer [tipo integral](../builtin-types/integral-numeric-types.md) pode ser implicitamente convertido em qualquer [tipo de ponto flutuante](../builtin-types/floating-point-numeric-types.md).

- A precisão, mas não a magnitude, poderá ser perdida nas conversões de `int`, `uint`, `long` ou `ulong` em `float` e de `long` ou `ulong` em `double`.  
  
- Não há nenhuma conversão implícita para os tipos `char`, `byte` e `sbyte`.  

- Não há nenhuma conversão implícita dos tipos `double` e `decimal`.
  
- Não há nenhuma conversão implícita entre os tipos `decimal` e `float` ou os tipos `double`.  
  
- Um valor de uma expressão de constante de tipo `int` (por exemplo, um valor representado por um literal integral) pode ser convertido em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, contanto que esteja dentro do intervalo do tipo de destino:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Para obter mais informações sobre conversões implícitas, consulte a seção [Conversões implícitas](~/_csharplang/spec/conversions.md#implicit-conversions) da [Especificação da linguagem C#](../language-specification/index.md).
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Tipos integrais](../builtin-types/integral-numeric-types.md)
- [Tabela de tipos de ponto flutuante](../builtin-types/floating-point-numeric-types.md)
- [Tabela de tipos internos](built-in-types-table.md)
- [Tabela de conversões numéricas explícitas](explicit-numeric-conversions-table.md)
- [Conversão e conversões de tipo](../../programming-guide/types/casting-and-type-conversions.md)
