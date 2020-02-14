---
title: Método MemoryStream. InternalGetOriginAndLength (System.IO)
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d82b5080e9fbd5fc6603f1cddae996c75a06d3a3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215470"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>Método MemoryStream. InternalGetOriginAndLength

Obtém os valores internos de origem e o comprimento do fluxo de memória.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>parâmetros

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
