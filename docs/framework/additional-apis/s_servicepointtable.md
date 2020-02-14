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
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214913"
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
