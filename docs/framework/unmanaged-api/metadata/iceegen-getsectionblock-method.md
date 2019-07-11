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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84ccbd7a8be7d90a541fb2d54baa3d7f66d3d31e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746117"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="7675c-102">Método ICeeGen::GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="7675c-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="7675c-103">Obtém um bloco de seção da base de código.</span><span class="sxs-lookup"><span data-stu-id="7675c-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="7675c-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="7675c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7675c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7675c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="7675c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7675c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7675c-107">[in] A seção da qual recuperar um bloco de base de código.</span><span class="sxs-lookup"><span data-stu-id="7675c-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="7675c-108">[in] O tamanho do bloco a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="7675c-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="7675c-109">[in] O byte, relativo ao início da seção, com a qual alinhar o primeiro byte do bloco.</span><span class="sxs-lookup"><span data-stu-id="7675c-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="7675c-110">Esta é a posição do bloco de dentro da seção.</span><span class="sxs-lookup"><span data-stu-id="7675c-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="7675c-111">[out] Um ponteiro para um local que recebe o endereço do bloco recuperado.</span><span class="sxs-lookup"><span data-stu-id="7675c-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7675c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7675c-112">Remarks</span></span>  
 <span data-ttu-id="7675c-113">Chamar `GetSectionBlock` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="7675c-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7675c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7675c-114">Requirements</span></span>  
 <span data-ttu-id="7675c-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7675c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7675c-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7675c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7675c-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7675c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7675c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7675c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7675c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7675c-119">See also</span></span>

- [<span data-ttu-id="7675c-120">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="7675c-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
