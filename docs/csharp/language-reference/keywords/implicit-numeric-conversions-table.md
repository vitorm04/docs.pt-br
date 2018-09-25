---
title: Tabela de conversões numéricas implícitas (Referência de C#)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: e46816fc8f3a6ff71dcba3561098d3cfce1e1054
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44213258"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela de conversões numéricas implícitas (Referência de C#)

A tabela a seguir mostra as conversões implícitas predefinidas entre tipos numéricos do .NET.
  
|De|Para|  
|----------|--------|  
|[sbyte](sbyte.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|  
|[byte](byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[short](short.md)|`int`, `long`, `float`, `double` ou `decimal`|  
|[ushort](ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[int](int.md)|`long`, `float`, `double` ou `decimal`|  
|[uint](uint.md)|`long`, `ulong`, `float`, `double` ou `decimal`|  
|[long](long.md)|`float`, `double` ou `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|  
|[float](float.md)|`double`|  
|[ulong](ulong.md)|`float`, `double` ou `decimal`|  
  
## <a name="remarks"></a>Comentários  

- Qualquer [tipo integral](integral-types-table.md) pode ser implicitamente convertido em qualquer [tipo de ponto flutuante](floating-point-types-table.md).

- A precisão, mas não a magnitude, poderá ser perdida nas conversões de `int`, `uint`, `long` ou `ulong` em `float` e de `long` ou `ulong` em `double`.  
  
- Não há conversões implícitas para o tipo `char`.  
  
- Não há conversões implícitas entre os tipos `float` e `double` e o tipo `decimal`.  
  
- Um valor de uma expressão de constante de tipo `int` (por exemplo, um valor representado por um literal integral) pode ser convertido em `sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`, contanto que esteja dentro do intervalo do tipo de destino:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Para obter mais informações sobre conversões implícitas, consulte a seção [Conversões implícitas](/dotnet/csharp/language-reference/language-specification/conversions#implicit-conversions) da [Especificação da linguagem C#](../language-specification/index.md).
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Tabela de tipos integrais](integral-types-table.md)
- [Tabela de tipos de ponto flutuante](floating-point-types-table.md)
- [Tabela de tipos internos](built-in-types-table.md)
- [Tabela de conversões numéricas explícitas](explicit-numeric-conversions-table.md)
- [Conversão e conversões de tipo](../../programming-guide/types/casting-and-type-conversions.md)
