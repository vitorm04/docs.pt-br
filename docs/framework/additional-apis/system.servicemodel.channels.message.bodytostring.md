---
title: Método Message. BodyToString (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 7b0b56bfda1c0c37f43f95e9684d3b4042c1b97c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451202"
---
# <a name="messagebodytostring-method"></a>Método Message. BodyToString

Converte o corpo da mensagem em uma cadeia de caracteres chamando o método <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>Parâmetros

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  O gravador usado para converter o corpo da mensagem em uma cadeia de caracteres.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `Message.BodyToString` é interno e não deve ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.ServiceModel.Channels>

**Assembly:** System. ServiceModel. dll

**.NET Framework versões:** Disponível desde 3,0.
