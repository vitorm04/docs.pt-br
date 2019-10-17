---
title: Propriedade SqlStreamChars. CanSeek (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395775"
---
# <a name="sqlstreamcharscanseek-property"></a>Propriedade SqlStreamChars. CanSeek

Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo atual dá suporte à operação de busca. O assembly que contém essa propriedade tem uma relação Friend com SQLAccess. dll. Ele é destinado ao uso por SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Boolean>\
`true` se o fluxo atual der suporte à operação de busca; caso contrário, `false`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A propriedade `SqlStreamChars.CanSeek` é privada e não se destina a ser usada diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso dessa propriedade em um aplicativo de produção em nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em System. Data. dll)

**.NET Framework versões:** Disponível desde 2,0.
