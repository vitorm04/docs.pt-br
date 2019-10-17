---
title: Método SqlStreamChars. Close (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395631"
---
# <a name="sqlstreamcharsclose-method"></a>Método SqlStreamChars. Close

Fecha o fluxo atual e libera todos os recursos do sistema associados ao fluxo. O assembly que contém esse método tem uma relação Friend com SQLAccess. dll. Ele é destinado ao uso por SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.

```csharp
public virtual void Close ();
```

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `SqlStreamChars.Close` é privado e não se destina a ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em System. Data. dll)

**.NET Framework versões:** Disponível desde 2,0.
