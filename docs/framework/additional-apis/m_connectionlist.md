---
title: Campo ConnectionGroup.m_ConnectionList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 8eb6f215c36e214f7095eeba90bf0aed66dfcea0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155844"
---
# <a name="connectiongroupm_connectionlist-field"></a>Campo ConnectionGroup.m\_ConnectionList

`ConnectionGroup.m_ConnectionList`é <xref:System.Collections.ArrayList> um objeto de conexão que serve o mesmo URI e compartilha os mesmos valores para algumas outras propriedades, como expiração e autenticação.

## <a name="syntax"></a>Sintaxe
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> O `ConnectionGroup.m_ConnectionList` campo é privado e não deve ser usado diretamente em seu código.
>
> A Microsoft não suporta o uso deste campo em um aplicativo de produção nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Espaço de nome:**<xref:System.Net>

**Montagem:** Sistema (em System.dll)

**Versões do Framework .NET:** Disponível desde 2.0.
