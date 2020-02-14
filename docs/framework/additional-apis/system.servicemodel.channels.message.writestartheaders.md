---
title: Método Message. WriteStartHeaders (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214871"
---
# <a name="messagewritestartheaders-method"></a>Método Message. WriteStartHeaders

Grava o cabeçalho inicial em um arquivo XML chamando o método <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>parâmetros

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
