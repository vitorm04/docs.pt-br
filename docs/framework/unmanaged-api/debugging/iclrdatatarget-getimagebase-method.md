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
ms.openlocfilehash: fcf0ab73c79a5fa116a89cdfcc2e73b17d9eabfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785488"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="d0f6e-102">Método ICLRDataTarget::GetImageBase</span><span class="sxs-lookup"><span data-stu-id="d0f6e-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="d0f6e-103">Obtém o endereço de memória base da imagem especificada.</span><span class="sxs-lookup"><span data-stu-id="d0f6e-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0f6e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0f6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0f6e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0f6e-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="d0f6e-106">no O nome do arquivo da imagem, incluindo seu caminho.</span><span class="sxs-lookup"><span data-stu-id="d0f6e-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="d0f6e-107">fora Um ponteiro para um CLRDATA_ADDRESS que armazena o endereço base da imagem.</span><span class="sxs-lookup"><span data-stu-id="d0f6e-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0f6e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0f6e-108">Remarks</span></span>  
 <span data-ttu-id="d0f6e-109">O nome do arquivo de imagem pode ou não ter um caminho.</span><span class="sxs-lookup"><span data-stu-id="d0f6e-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="d0f6e-110">Se um caminho for especificado, a correspondência será feita no caminho inteiro; caso contrário, a correspondência será feita apenas no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d0f6e-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0f6e-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d0f6e-111">Requirements</span></span>  
 <span data-ttu-id="d0f6e-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0f6e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0f6e-113">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d0f6e-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d0f6e-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0f6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0f6e-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0f6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f6e-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="d0f6e-116">See also</span></span>

- [<span data-ttu-id="d0f6e-117">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="d0f6e-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
