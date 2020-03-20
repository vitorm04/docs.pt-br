---
title: Campo ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155801"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Campo servicepointtable\_servicepointmanager.s

`ServicePointManager.s_ServicePointTable`é <xref:System.Collections.Hashtable> um que contém a lista<xref:System.Net.ServicePoint>de conexões <xref:System.AppDomain>HTTP ativas (s) no .

## <a name="syntax"></a>Sintaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> O `ServicePointManager.s_ServicePointTable` campo é privado e não deve ser usado diretamente em seu código.
>
> A Microsoft não suporta o uso deste campo em um aplicativo de produção nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Espaço de nome:**<xref:System.Net>

**Montagem:** Sistema (em System.dll)

**Versões do Framework .NET:** Disponível desde 2.0.
