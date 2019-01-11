---
title: Método SqlStreamChars.Write (Char [], Int32, Int32) (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221902"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>Método SqlStreamChars.Write (Char [], Int32, Int32)

Quando substituído em uma classe derivada, grava uma sequência de caracteres no fluxo atual e avança a posição atual dentro desse fluxo pelo número de caracteres gravados. O assembly que contém este método tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parâmetros

`buffer`  
Uma matriz de char para gravar.

`offset`  
Um deslocamento relativo à origem.

`count`  
O número de caracteres a serem gravados no fluxo atual.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlStreamChars.Write` método é privado e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.