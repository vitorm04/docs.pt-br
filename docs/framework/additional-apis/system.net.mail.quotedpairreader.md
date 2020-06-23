---
title: Classe QuotedPairReader (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990297"
---
# <a name="quotedpairreader-class"></a>Classe QuotedPairReader

Determina quais caracteres são colocados entre aspas (escape) em uma cadeia de caracteres entre aspas. Esta classe não pode ser herdada.

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> Essa classe é interna e não deve ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.

## <a name="countquotedchars-method"></a>Método CountQuotedChars

Conta o número de caracteres entre aspas consecutivas, incluindo várias barras invertidas precedentes, na cadeia de caracteres especificada. Por exemplo, considerando a cadeia `a\\\b` de caracteres e um índice de `4` , o método retorna `4` , porque `b` está entre aspas e, portanto, as três barras invertidas precedentes.

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a>Parâmetros

- `data` <xref:System.String>

  A cadeia de dados na qual contar caracteres entre aspas consecutivas.

- `index` <xref:System.Int32>

  A posição na cadeia de caracteres especificada até e incluindo quais caracteres entre aspas consecutivas devem ser contados.

- `permitUnicodeEscaping` <xref:System.Boolean>

  `true`para permitir que os caracteres Unicode sejam ignorados; caso contrário, `false` .

### <a name="return-value"></a>Valor retornado

<xref:System.Int32?displayProperty=nameWithType>

`0`Se o caractere no índice especificado não for de escape; caso contrário, o número de caracteres entre aspas consecutivas até e incluindo o caractere em `index` .

### <a name="exceptions"></a>Exceções

<xref:System.FormatException?displayProperty=nameWithType>

Um caractere Unicode de escape foi encontrado, mas não é permitido.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System.dll)
