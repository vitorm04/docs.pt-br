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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98273307003485202d8c12d5c27fda04ff5a0ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629895"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="daeb2-102">Método IAssemblyCacheItem::CreateStream</span><span class="sxs-lookup"><span data-stu-id="daeb2-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="daeb2-103">Cria um fluxo com o nome especificado e o formato.</span><span class="sxs-lookup"><span data-stu-id="daeb2-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="daeb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="daeb2-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="daeb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="daeb2-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="daeb2-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="daeb2-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="daeb2-107">[in] O nome do fluxo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="daeb2-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="daeb2-108">[in] O formato do arquivo a ser transmitido.</span><span class="sxs-lookup"><span data-stu-id="daeb2-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="daeb2-109">[in] Sinalizadores de formato específicos definidos em Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="daeb2-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="daeb2-110">[out] Um ponteiro para o endereço do retornado [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instância.</span><span class="sxs-lookup"><span data-stu-id="daeb2-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="daeb2-111">[in, opcional] O tamanho máximo do fluxo referenciado pelo `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="daeb2-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="daeb2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="daeb2-112">Requirements</span></span>

<span data-ttu-id="daeb2-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daeb2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="daeb2-114">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="daeb2-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="daeb2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daeb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="daeb2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="daeb2-116">See also</span></span>

- [<span data-ttu-id="daeb2-117">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="daeb2-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
