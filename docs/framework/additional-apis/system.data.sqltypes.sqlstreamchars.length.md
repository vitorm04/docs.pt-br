---
title: Propriedade SqlStreamChars. Length (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395603"
---
# <a name="sqlstreamcharslength-property"></a>Propriedade SqlStreamChars. Length

Quando substituído em uma classe derivada, obtém o comprimento do fluxo atual. O assembly que contém essa propriedade tem uma relação Friend com SQLAccess. dll. Ele é destinado ao uso por SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.

## <a name="syntax"></a>Sintaxe

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Int64>\
O comprimento do fluxo.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A propriedade `SqlStreamChars.Length` é privada e não se destina a ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em System. Data. dll)

**.NET Framework versões:** Disponível desde 2,0.
