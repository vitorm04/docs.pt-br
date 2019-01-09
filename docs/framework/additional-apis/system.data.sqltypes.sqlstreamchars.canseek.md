---
title: Propriedade SqlStreamChars.CanSeek (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 0145fe87e2c8aa3dd40e73f0089fe40b6b6cca30
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152729"
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