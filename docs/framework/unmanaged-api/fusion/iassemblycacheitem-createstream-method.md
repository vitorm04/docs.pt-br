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
ms.openlocfilehash: 5af7dc4e1694b66fc4a5ce37e515c71e9fa3db49
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796734"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="a4268-102">Método IAssemblyCacheItem::CreateStream</span><span class="sxs-lookup"><span data-stu-id="a4268-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="a4268-103">Cria um fluxo com o nome e o formato especificados.</span><span class="sxs-lookup"><span data-stu-id="a4268-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4268-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4268-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="a4268-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4268-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="a4268-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="a4268-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="a4268-107">no O nome do fluxo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="a4268-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="a4268-108">no O formato do arquivo a ser transmitido.</span><span class="sxs-lookup"><span data-stu-id="a4268-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="a4268-109">no Sinalizadores específicos de formato definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="a4268-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="a4268-110">fora Um ponteiro para o endereço da instância de [IStream](/windows/desktop/api/objidl/nn-objidl-istream) retornada.</span><span class="sxs-lookup"><span data-stu-id="a4268-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="a4268-111">[in, opcional] O tamanho máximo do fluxo referenciado por `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="a4268-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4268-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4268-112">Requirements</span></span>

<span data-ttu-id="a4268-113">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4268-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a4268-114">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a4268-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="a4268-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4268-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a4268-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4268-116">See also</span></span>

- [<span data-ttu-id="a4268-117">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="a4268-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
