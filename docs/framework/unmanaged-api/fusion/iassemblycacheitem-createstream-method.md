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
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="6fd51-102">Método IAssemblyCacheItem::CreateStream</span><span class="sxs-lookup"><span data-stu-id="6fd51-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="6fd51-103">Cria um fluxo com o nome e o formato especificados.</span><span class="sxs-lookup"><span data-stu-id="6fd51-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fd51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fd51-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="6fd51-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fd51-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="6fd51-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="6fd51-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="6fd51-107">no O nome do fluxo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="6fd51-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="6fd51-108">no O formato do arquivo a ser transmitido.</span><span class="sxs-lookup"><span data-stu-id="6fd51-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="6fd51-109">no Sinalizadores específicos de formato definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="6fd51-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="6fd51-110">fora Um ponteiro para o endereço da instância de [IStream](/windows/desktop/api/objidl/nn-objidl-istream) retornada.</span><span class="sxs-lookup"><span data-stu-id="6fd51-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="6fd51-111">[in, opcional] O tamanho máximo do fluxo referenciado por `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="6fd51-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6fd51-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fd51-112">Requirements</span></span>

<span data-ttu-id="6fd51-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fd51-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6fd51-114">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6fd51-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="6fd51-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fd51-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6fd51-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fd51-116">See also</span></span>

- [<span data-ttu-id="6fd51-117">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="6fd51-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
