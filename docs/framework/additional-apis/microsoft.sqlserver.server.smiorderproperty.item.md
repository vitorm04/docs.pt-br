---
title: Propriedade SmiOrderProperty.Item (SQLServer)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: e2d8788f610d80c30baf51bff0131f0834d59fcd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634582"
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
