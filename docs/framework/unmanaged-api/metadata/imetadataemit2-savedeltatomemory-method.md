---
title: Método IMetaDataEmit2::SaveDeltaToMemory
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84972388f90ea23032ed0524723d59077c732e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498889"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="45cc0-102">Método IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="45cc0-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="45cc0-103">Salva as alterações da sessão atual de editar e continuar para a memória.</span><span class="sxs-lookup"><span data-stu-id="45cc0-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cc0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45cc0-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45cc0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45cc0-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="45cc0-106">[out] O endereço no qual começar a gravar o delta de metadados.</span><span class="sxs-lookup"><span data-stu-id="45cc0-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="45cc0-107">[in] O tamanho das alterações.</span><span class="sxs-lookup"><span data-stu-id="45cc0-107">[in] The size of the changes.</span></span> <span data-ttu-id="45cc0-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) para determinar o tamanho.</span><span class="sxs-lookup"><span data-stu-id="45cc0-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45cc0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45cc0-109">Requirements</span></span>  
 <span data-ttu-id="45cc0-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45cc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45cc0-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="45cc0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45cc0-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="45cc0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45cc0-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45cc0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cc0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45cc0-114">See also</span></span>
- [<span data-ttu-id="45cc0-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="45cc0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="45cc0-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="45cc0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
