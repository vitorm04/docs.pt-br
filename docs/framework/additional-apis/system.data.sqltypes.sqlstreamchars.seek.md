---
title: Método SqlStreamChars.Seek (Int64, SeekOrigin) (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 6b69f87da9fb3829d765dc135de1f6c10765b63a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634353"
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
