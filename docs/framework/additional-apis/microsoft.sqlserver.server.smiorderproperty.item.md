---
title: Propriedade SmiOrderProperty.Item (SQLServer)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c586d07e8ea0c2ac0b1efb603e8900d681fd0a91
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152659"
---
# <a name="smiorderpropertyitem-property"></a>Propriedade SmiOrderProperty.Item

Obtém a ordem das colunas para a entidade. O assembly que contém essa propriedade tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

## <a name="syntax"></a>Sintaxe

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a>Valor da propriedade

A ordem das colunas.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SmiOrderProperty.Item` propriedade é interna e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso dessa propriedade em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:Microsoft.SqlServer.Server>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.