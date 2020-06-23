---
title: Classe MailAddressParser (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990301"
---
# <a name="mailaddressparser-class"></a>Classe MailAddressParser

Analisa endereços de email conforme descrito em RFC 2822. Esta classe não pode ser herdada.

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> Essa classe é interna e não deve ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.

## <a name="parseaddress-method"></a>Método ParseAddress

Analisa um único endereço de email da cadeia de caracteres especificada.

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>Parâmetros

`data` <xref:System.String>

A cadeia de caracteres que contém um endereço de email a ser analisado.

### <a name="return-value"></a>Valor retornado

<xref:System.Net.Mail.MailAddress>

Um endereço de email válido.

### <a name="exceptions"></a>Exceções

<xref:System.FormatException?displayProperty=nameWithType>

O endereço de email é inválido.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System.dll)
