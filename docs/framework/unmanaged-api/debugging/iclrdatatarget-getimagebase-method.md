---
title: Método ICLRDataTarget::GetImageBase
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e823911280f52e16c745c9c77fe17b49bd35dc0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698272"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="2f57f-102">Método ICLRDataTarget::GetImageBase</span><span class="sxs-lookup"><span data-stu-id="2f57f-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="2f57f-103">Obtém o endereço de memória de base da imagem especificada.</span><span class="sxs-lookup"><span data-stu-id="2f57f-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f57f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f57f-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f57f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f57f-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="2f57f-106">[in] O nome do arquivo de imagem, incluindo seu caminho.</span><span class="sxs-lookup"><span data-stu-id="2f57f-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="2f57f-107">[out] Um ponteiro para um CLRDATA_ADDRESS que armazena o endereço básico da imagem.</span><span class="sxs-lookup"><span data-stu-id="2f57f-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f57f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f57f-108">Remarks</span></span>  
 <span data-ttu-id="2f57f-109">O nome do arquivo de imagem pode ou não ter um caminho.</span><span class="sxs-lookup"><span data-stu-id="2f57f-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="2f57f-110">Se um caminho for especificado, a correspondência é feita no caminho inteiro; Caso contrário, a correspondência é feita apenas no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f57f-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f57f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f57f-111">Requirements</span></span>  
 <span data-ttu-id="2f57f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f57f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f57f-113">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2f57f-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2f57f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f57f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f57f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f57f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f57f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f57f-116">See also</span></span>

- [<span data-ttu-id="2f57f-117">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="2f57f-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
