---
title: Campo ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8dfdbab78d8efab13487575218820f8b0455248d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable campo

`ServicePointManager.s_ServicePointTable`é um <xref:System.Collections.Hashtable> que contém a lista de conexões ativas de HTTP (<xref:System.Net.ServicePoint>s) na <xref:System.AppDomain>.

## <a name="syntax"></a>Sintaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> O `ServicePointManager.s_ServicePointTable` campo é privado e não se destina a ser usado diretamente no seu código.
> 
> Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:**<xref:System.Net>

**Assembly:** sistema (em System. dll)

**Versões do .NET framework:** disponível desde o 2.0.
