---
title: Método SqlStreamChars. Write (Char [], Int32, Int32) (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395583"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>Método SqlStreamChars. Write (Char [], Int32, Int32)

Quando substituído em uma classe derivada, o grava uma sequência de caracteres no fluxo atual e avança a posição atual dentro desse fluxo pelo número de caracteres gravados. O assembly que contém esse método tem uma relação Friend com SQLAccess. dll. Ele é destinado ao uso por SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido por esse banco.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parâmetros

`buffer`  
Uma matriz char a ser gravada.

`offset`  
Um deslocamento relativo à origem.

`count`  
O número de caracteres a serem gravados no fluxo atual.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `SqlStreamChars.Write` é privado e não se destina a ser usado diretamente no seu código.
>
> A Microsoft não dá suporte ao uso desse método para gravar em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em System. Data. dll)

**.NET Framework versões:** Disponível desde 2,0.
