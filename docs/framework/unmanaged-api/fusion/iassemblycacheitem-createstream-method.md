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
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561211"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="dad48-102">Método IAssemblyCacheItem::CreateStream</span><span class="sxs-lookup"><span data-stu-id="dad48-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="dad48-103">Cria um fluxo com o nome especificado e o formato.</span><span class="sxs-lookup"><span data-stu-id="dad48-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dad48-104">Syntax</span></span>  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dad48-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dad48-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="dad48-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="dad48-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="dad48-107">[in] O nome do fluxo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="dad48-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="dad48-108">[in] O formato do arquivo a ser transmitido.</span><span class="sxs-lookup"><span data-stu-id="dad48-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="dad48-109">[in] Sinalizadores de formato específicos definidos em Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="dad48-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="dad48-110">[out] Um ponteiro para o endereço do retornado [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instância.</span><span class="sxs-lookup"><span data-stu-id="dad48-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="dad48-111">[in, opcional] O tamanho máximo do fluxo referenciado pelo `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="dad48-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad48-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dad48-112">Requirements</span></span>  
 <span data-ttu-id="dad48-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dad48-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad48-114">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="dad48-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dad48-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad48-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad48-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dad48-116">See Also</span></span>  
 [<span data-ttu-id="dad48-117">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="dad48-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
