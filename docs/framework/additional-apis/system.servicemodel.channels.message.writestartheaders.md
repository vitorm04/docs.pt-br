---
title: Método Message. WriteStartHeaders (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: a2c82ee4029c7af0396219f5ded8c999fd01d65b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451174"
---
# <a name="messagewritestartheaders-method"></a>Método Message. WriteStartHeaders

Grava o cabeçalho inicial em um arquivo XML chamando o método <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>Parâmetros

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  O gravador usado para gravar o cabeçalho inicial em um arquivo XML.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `Message.WriteStartHeaders` é interno e não deve ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.ServiceModel.Channels>

**Assembly:** System. ServiceModel. dll

**.NET Framework versões:** Disponível desde 3,0.
