---
title: Propriedade SmiOrderProperty.Item (SQLServer)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5453167e16e2658b3546b7114201b04d481a0c79
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222995"
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