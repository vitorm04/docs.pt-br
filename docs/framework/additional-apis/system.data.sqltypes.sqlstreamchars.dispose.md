---
title: Método SqlStreamChars.Dispose(Boolean) (SqlTypes)
author: douglaslMS
ms.author: douglasl
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
ms.openlocfilehash: 930a4a69c6c44269e728fbcef62e561ab165ea22
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222357"
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