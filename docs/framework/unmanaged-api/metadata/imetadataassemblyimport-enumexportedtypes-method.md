---
title: Método IMetaDataAssemblyImport::EnumExportedTypes
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: 514488c6e0d2e89de0d8ee483def485ec9f3ef25
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009089"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="a9c22-102">Método IMetaDataAssemblyImport::EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="a9c22-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="a9c22-103">Enumera os tipos exportados referenciados no manifesto do assembly no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="a9c22-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9c22-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9c22-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9c22-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a9c22-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="a9c22-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a9c22-107">Esse deve ser um valor nulo quando o `EnumExportedTypes` método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="a9c22-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="a9c22-108">fora A enumeração de `mdExportedType` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="a9c22-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a9c22-109">no O número máximo de `mdExportedType` tokens que podem ser colocados na `rExportedTypes` matriz.</span><span class="sxs-lookup"><span data-stu-id="a9c22-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a9c22-110">fora O número de `mdExportedType` tokens realmente colocados no `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="a9c22-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9c22-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a9c22-111">Return Value</span></span>  
  
|<span data-ttu-id="a9c22-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9c22-112">HRESULT</span></span>|<span data-ttu-id="a9c22-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9c22-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a9c22-114">`EnumExportedTypes`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a9c22-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a9c22-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="a9c22-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a9c22-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="a9c22-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9c22-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9c22-117">Requirements</span></span>  
 <span data-ttu-id="a9c22-118">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9c22-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9c22-119">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a9c22-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9c22-120">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9c22-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9c22-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9c22-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c22-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9c22-122">See also</span></span>

- [<span data-ttu-id="a9c22-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="a9c22-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
