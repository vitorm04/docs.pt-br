---
title: Campo ConnectionGroup.m_ConnectionList
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b89a621e5a438e2385f07bcaf910d799a49d32d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="connectiongroupmconnectionlist-field"></a>ConnectionGroup.m\_ConnectionList campo

`ConnectionGroup.m_ConnectionList`é um <xref:System.Collections.ArrayList> de objetos de conexão que serve o mesmo URI e compartilhar os mesmos valores para algumas outras propriedades como expiração e autenticação.

## <a name="syntax"></a>Sintaxe
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> O `ConnectionGroup.m_ConnectionList` campo é privado e não se destina a ser usado diretamente no seu código.
> 
> Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:**<xref:System.Net>

**Assembly:** sistema (em System. dll)

**Versões do .NET framework:** disponível desde o 2.0.
