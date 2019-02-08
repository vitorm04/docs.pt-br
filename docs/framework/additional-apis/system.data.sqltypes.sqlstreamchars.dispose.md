---
title: Método SqlStreamChars.Dispose(Boolean) (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4e6cfd6d4c04b1a2835b6e34b82c95b564dea588
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826857"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>Método SqlStreamChars.Dispose(Boolean)

Quando substituído em uma classe derivada, libera os recursos usados pelo fluxo. O assembly que contém este método tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>Parâmetros

`disposing`\
`true` para liberar recursos gerenciados e não gerenciados; `false` para liberar apenas recursos não gerenciados.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlStreamChars.Dispose` método é privado e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.