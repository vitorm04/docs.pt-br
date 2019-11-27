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
ms.openlocfilehash: 0731053fb37c775d25052a5fd99a479a44ff5862
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434872"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="e4eb9-102">Método ICeeGen::GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="e4eb9-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="e4eb9-103">Obtém um bloco de seção da base de código.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="e4eb9-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4eb9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4eb9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="e4eb9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4eb9-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="e4eb9-107">no A seção da qual recuperar um bloco da base de código.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="e4eb9-108">no O comprimento do bloco a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="e4eb9-109">no O byte, em relação ao início da seção, com o qual alinhar o primeiro byte do bloco.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="e4eb9-110">Essa é a posição do bloco dentro da seção.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="e4eb9-111">fora Um ponteiro para um local que recebe o endereço do bloco recuperado.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4eb9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4eb9-112">Remarks</span></span>  
 <span data-ttu-id="e4eb9-113">Chame `GetSectionBlock` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="e4eb9-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4eb9-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4eb9-114">Requirements</span></span>  
 <span data-ttu-id="e4eb9-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4eb9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4eb9-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e4eb9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4eb9-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4eb9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4eb9-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4eb9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4eb9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4eb9-119">See also</span></span>

- [<span data-ttu-id="e4eb9-120">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="e4eb9-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
