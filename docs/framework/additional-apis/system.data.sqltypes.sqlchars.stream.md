---
title: Propriedade SqlChars.Stream (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d756b78a7cdbc12562e474ca3d2c9a1f3529f6bf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223046"
---
# <a name="sqlcharsstream-property"></a>Propriedade SqlChars.Stream

Obtém ou define o fluxo de caracteres. O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a>Valor da propriedade

`System.Data.SqlTypes.SqlStreamChars`\
O fluxo de caracteres.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlChars.Stream` propriedade é interna e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso dessa propriedade em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.