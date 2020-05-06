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
ms.openlocfilehash: 71b07e11cd3fec1a0dbebe986d98067c2e6f18e1
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860639"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="32568-102">Método ICLRDataTarget::GetImageBase</span><span class="sxs-lookup"><span data-stu-id="32568-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="32568-103">Obtém o endereço de memória base da imagem especificada.</span><span class="sxs-lookup"><span data-stu-id="32568-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32568-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32568-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32568-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32568-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="32568-106">no O nome do arquivo da imagem, incluindo seu caminho.</span><span class="sxs-lookup"><span data-stu-id="32568-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="32568-107">fora Um ponteiro para um CLRDATA_ADDRESS que armazena o endereço base da imagem.</span><span class="sxs-lookup"><span data-stu-id="32568-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32568-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="32568-108">Remarks</span></span>  
 <span data-ttu-id="32568-109">O nome do arquivo de imagem pode ou não ter um caminho.</span><span class="sxs-lookup"><span data-stu-id="32568-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="32568-110">Se um caminho for especificado, a correspondência será feita no caminho inteiro; caso contrário, a correspondência será feita apenas no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="32568-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32568-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32568-111">Requirements</span></span>  
 <span data-ttu-id="32568-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32568-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32568-113">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="32568-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="32568-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32568-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32568-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32568-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32568-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="32568-116">See also</span></span>

- [<span data-ttu-id="32568-117">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="32568-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
