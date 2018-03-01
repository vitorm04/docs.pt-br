---
title: "Método ICeeGen::GetSectionBlock"
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
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e00d7ae1b110fc9f1e1d41d8c3ddb9427b3d44a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="651f4-102">Método ICeeGen::GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="651f4-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="651f4-103">Obtém um bloco de seção da base de código.</span><span class="sxs-lookup"><span data-stu-id="651f4-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="651f4-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="651f4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="651f4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="651f4-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="651f4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="651f4-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="651f4-107">[in] A seção da qual recuperar um bloco da base de código.</span><span class="sxs-lookup"><span data-stu-id="651f4-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="651f4-108">[in] O comprimento do bloco a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="651f4-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="651f4-109">[in] O byte, relativo ao início da seção, com a qual alinhar o primeiro byte do bloco.</span><span class="sxs-lookup"><span data-stu-id="651f4-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="651f4-110">Esta é a posição do bloco dentro da seção.</span><span class="sxs-lookup"><span data-stu-id="651f4-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="651f4-111">[out] Um ponteiro para um local que recebe o endereço do bloco recuperado.</span><span class="sxs-lookup"><span data-stu-id="651f4-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="651f4-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="651f4-112">Remarks</span></span>  
 <span data-ttu-id="651f4-113">Chamar `GetSectionBlock` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="651f4-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="651f4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="651f4-114">Requirements</span></span>  
 <span data-ttu-id="651f4-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="651f4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="651f4-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="651f4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="651f4-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="651f4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="651f4-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="651f4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="651f4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="651f4-119">See Also</span></span>  
 [<span data-ttu-id="651f4-120">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="651f4-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
