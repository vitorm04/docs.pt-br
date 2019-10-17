---
title: Método SqlStreamChars. Seek (Int64, SeekOrigin) (System. Data. SqlTypes)
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
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395590"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>Método SqlStreamChars. Seek (Int64, SeekOrigin)

Quando substituído em uma classe derivada, define a posição dentro do fluxo atual. O assembly que contém esse método tem uma relação Friend com SQLAccess. dll. Ele é destinado ao uso por SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.

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
> O método `SqlStreamChars.Seek` é privado e não se destina a ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em System. Data. dll)

**.NET Framework versões:** Disponível desde 2,0.
