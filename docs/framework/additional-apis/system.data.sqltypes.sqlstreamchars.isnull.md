---
title: Propriedade SqlStreamChars. IsNull (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395742"
---
# <a name="sqlstreamcharsisnull-property"></a>Propriedade SqlStreamChars. IsNull

Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`. O assembly que contém essa propriedade tem uma relação Friend com SQLAccess. dll. Ele é destinado ao uso por SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.

## <a name="syntax"></a>Sintaxe

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Boolean>\
`true` se o fluxo for `null`; caso contrário, `false`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A propriedade `SqlStreamChars.IsNull` é privada e não se destina a ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em System. Data. dll)

**.NET Framework versões:** Disponível desde 2,0.
