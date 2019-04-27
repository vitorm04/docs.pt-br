---
title: Propriedade SqlStreamChars.CanSeek (SqlTypes)
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
ms.openlocfilehash: 52f88a3551e20c74d7a1144c3cd6859a023980db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675164"
---
# <a name="sqlstreamcharscanseek-property"></a>Propriedade SqlStreamChars.CanSeek

Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo atual dá suporte à operação de busca. O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Boolean>\
`true` Se o fluxo atual dá suporte à operação de busca; Caso contrário, `false`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlStreamChars.CanSeek` propriedade é privada e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.