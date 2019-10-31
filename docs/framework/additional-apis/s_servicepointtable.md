---
title: Campo ServicePointManager. s_ServicePointTable
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119998"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>ServicePointManager. s\_campo do objectpointtable

`ServicePointManager.s_ServicePointTable` é uma <xref:System.Collections.Hashtable> que contém a lista de conexões HTTP ativas (<xref:System.Net.ServicePoint>s) no <xref:System.AppDomain>.

## <a name="syntax"></a>Sintaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> O campo `ServicePointManager.s_ServicePointTable` é privado e não deve ser usado diretamente no seu código.
> 
> A Microsoft não oferece suporte ao uso deste campo em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System. dll)

**.NET Framework versões:** Disponível desde 2,0.
