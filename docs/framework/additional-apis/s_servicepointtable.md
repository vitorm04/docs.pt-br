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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 5450a0cb3e5bd39a86365b16d372c7e573a43496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351752"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable campo

`ServicePointManager.s_ServicePointTable` é um <xref:System.Collections.Hashtable> que contém a lista de conexões ativas de HTTP (<xref:System.Net.ServicePoint>s) na <xref:System.AppDomain>.

## <a name="syntax"></a>Sintaxe
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> O `ServicePointManager.s_ServicePointTable` campo é privado e não se destina a ser usado diretamente no seu código.
> 
> Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** sistema (em System. dll)

**Versões do .NET framework:** disponível desde o 2.0.
