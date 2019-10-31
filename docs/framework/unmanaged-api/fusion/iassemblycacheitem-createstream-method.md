---
title: Método IAssemblyCacheItem::CreateStream
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134479"
---
# <a name="iassemblycacheitemcreatestream-method"></a>Método IAssemblyCacheItem::CreateStream

Cria um fluxo com o nome e o formato especificados.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a>Parâmetros

`dwFlags`\
no Sinalizadores definidos em Fusion. idl.

`pszStreamName`\
no O nome do fluxo a ser criado.

`dwFormat`\
no O formato do arquivo a ser transmitido.

`dwFormatFlags`\
no Sinalizadores específicos de formato definidos em Fusion. idl.

`ppIStream`\
fora Um ponteiro para o endereço da instância de [IStream](/windows/desktop/api/objidl/nn-objidl-istream) retornada.

`puliMaxSize`\
[in, opcional] O tamanho máximo do fluxo referenciado por `ppIStream`.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** Fusion. h

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface IAssemblyCacheItem](iassemblycacheitem-interface.md)
