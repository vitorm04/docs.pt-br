---
title: Método MemoryStream. InternalGetOriginAndLength (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284027"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>Método MemoryStream. InternalGetOriginAndLength

Obtém os valores internos de origem e o comprimento do fluxo de memória.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>Parâmetros

- `origin` <xref:System.Int32>\
  Quando esse método retorna, o deslocamento da matriz de bytes especificado ao criar um novo objeto de <xref:System.IO.MemoryStream>. Contém 0 se a matriz de bytes foi criada por <xref:System.IO.MemoryStream>.

- `length` <xref:System.Int32>\
  Quando esse método retorna, o número de bytes dentro do fluxo de memória.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `MemoryStream.InternalGetOriginAndLength` é interno e não deve ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.IO>

**Assembly:** mscorlib. dll (em mscorlib. dll)

**.NET Framework versões:** Disponível desde 2,0.
