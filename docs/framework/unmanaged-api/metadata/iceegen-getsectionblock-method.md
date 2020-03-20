---
title: Método ICeeGen::GetSectionBlock
ms.date: 03/30/2017
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
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176078"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="c9817-102">Método ICeeGen::GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="c9817-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="c9817-103">Obtém um bloco de seção da base de código.</span><span class="sxs-lookup"><span data-stu-id="c9817-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="c9817-104">Este método é obsoleto e não deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="c9817-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9817-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9817-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c9817-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9817-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="c9817-107">[em] A seção a partir da qual recuperar um bloco da base de código.</span><span class="sxs-lookup"><span data-stu-id="c9817-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="c9817-108">[em] O comprimento do bloco a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="c9817-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="c9817-109">[em] O byte, relativo ao início da seção, com o qual alinhar o primeiro byte do bloco.</span><span class="sxs-lookup"><span data-stu-id="c9817-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="c9817-110">Esta é a posição do bloco dentro da seção.</span><span class="sxs-lookup"><span data-stu-id="c9817-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="c9817-111">[fora] Um ponteiro para um local que recebe o endereço do bloco recuperado.</span><span class="sxs-lookup"><span data-stu-id="c9817-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9817-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9817-112">Remarks</span></span>  
 <span data-ttu-id="c9817-113">Ligue `GetSectionBlock` somente se tiver requisitos especiais de seção que não sejam tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="c9817-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9817-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9817-114">Requirements</span></span>  
 <span data-ttu-id="c9817-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9817-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9817-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9817-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9817-117">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9817-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9817-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9817-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9817-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9817-119">See also</span></span>

- [<span data-ttu-id="c9817-120">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="c9817-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
