---
title: Método SqlStreamChars.Read (Char [], Int32, Int32) (SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 87bff6dd78743ae08a5a3db8a783b56a0b7c3f24
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152529"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>Método SqlStreamChars.Read (Char [], Int32, Int32)

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