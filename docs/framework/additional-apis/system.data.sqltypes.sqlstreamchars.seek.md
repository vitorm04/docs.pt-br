---
title: Método SqlStreamChars.Seek (Int64, SeekOrigin) (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: aab3195ec0d300a7f001f98f2d646c85be939356
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152549"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>Método SqlStreamChars.Seek (Int64, SeekOrigin)

Quando substituído em uma classe derivada, define a posição dentro do fluxo atual. O assembly que contém este método tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parâmetros

`offset`\
Um deslocamento de bytes em relação a `origin`.

`origin`\
Um dos valores de enumeração que indica o ponto de referência do qual obter a nova posição.

## <a name="returns"></a>Retorna

<xref:System.Int32>\
A nova posição dentro do fluxo atual.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlStreamChars.Seek` método é privado e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.