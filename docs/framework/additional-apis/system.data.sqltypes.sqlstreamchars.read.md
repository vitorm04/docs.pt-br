---
title: Método SqlStreamChars.Read (Char [], Int32, Int32) (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: df92acfd4050eb16d3a101b20b9b44560273f4d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675228"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars.Read(Char[], Int32, Int32) Method

Quando substituído em uma classe derivada, lê o próximo conjunto de caracteres do fluxo de entrada. O assembly que contém este método tem uma relação de amigo com SQLAccess.dll. Ele é destinado a uso pelo SQL Server. Para outros bancos de dados, use o mecanismo de hospedagem fornecido pelo banco de dados.

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parâmetros

`buffer`\
Uma matriz de char para ler.

`offset`\
Um deslocamento relativo à origem.

`count`\
O número de caracteres a serem lidos do fluxo atual.

## <a name="returns"></a>Retorna

<xref:System.Int32>\
O número total de caracteres lidos no buffer.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O `SqlStreamChars.Read` método é privado e não se destina a ser usado diretamente em seu código.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Data.SqlTypes>

**Assembly:** System. Data (em dll)

**Versões do .NET framework:** Disponível desde o 2.0.