---
title: Método Message. BodyToString (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215502"
---
# <a name="messagebodytostring-method"></a>Método Message. BodyToString

Converte o corpo da mensagem em uma cadeia de caracteres chamando o método <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>parâmetros

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
