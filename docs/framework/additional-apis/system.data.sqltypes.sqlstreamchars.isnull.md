---
title: Propriedade SqlStreamChars.IsNull (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 79ebb9ec54185a94cb95dfd0fb2929e61cf513ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152619"
---
# <a name="sqlstreamcharsisnull-property"></a>Propriedade SqlStreamChars.IsNull

Quando substituído em uma classe derivada, obtém um valor que indica se o fluxo é `null`. O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

## <a name="syntax"></a>Sintaxe

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>Valor da propriedade

<xref:System.Boolean>\
`true` Se o fluxo estiver `null`; caso contrário, `false`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlStreamChars.IsNull` propriedade é privada e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.