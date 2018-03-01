---
title: "Método ICLRDataTarget::GetImageBase"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 504c3ce7115cbab11d0510eaa2ebb0fdd9f1888b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="86c79-102">Método ICLRDataTarget::GetImageBase</span><span class="sxs-lookup"><span data-stu-id="86c79-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="86c79-103">Obtém o endereço de memória base da imagem especificada.</span><span class="sxs-lookup"><span data-stu-id="86c79-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86c79-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86c79-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86c79-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="86c79-106">[in] O nome do arquivo de imagem, incluindo seu caminho.</span><span class="sxs-lookup"><span data-stu-id="86c79-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="86c79-107">[out] Um ponteiro para um CLRDATA_ADDRESS que armazena o endereço base da imagem.</span><span class="sxs-lookup"><span data-stu-id="86c79-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c79-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="86c79-108">Remarks</span></span>  
 <span data-ttu-id="86c79-109">O nome do arquivo de imagem pode ou não ter um caminho.</span><span class="sxs-lookup"><span data-stu-id="86c79-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="86c79-110">Se um caminho for especificado, a correspondência é feita no caminho inteiro; Caso contrário, a correspondência é feita apenas no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="86c79-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c79-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86c79-111">Requirements</span></span>  
 <span data-ttu-id="86c79-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c79-113">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="86c79-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="86c79-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86c79-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86c79-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c79-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86c79-116">See Also</span></span>  
 [<span data-ttu-id="86c79-117">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="86c79-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
