---
title: Método ICeeGen::GetSectionDataLen
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: febf952dbfd80a37017cb165aec4a6b207052d1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745951"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="eb0d8-102">Método ICeeGen::GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="eb0d8-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="eb0d8-103">Obtém o comprimento da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="eb0d8-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb0d8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb0d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb0d8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb0d8-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="eb0d8-107">[in] A seção de dados cujo comprimento será recuperado.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="eb0d8-108">[out] O comprimento retornado da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb0d8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb0d8-109">Remarks</span></span>  
 <span data-ttu-id="eb0d8-110">Chamar `GetSectionDataLen` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="eb0d8-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb0d8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb0d8-111">Requirements</span></span>  
 <span data-ttu-id="eb0d8-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb0d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb0d8-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eb0d8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb0d8-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="eb0d8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb0d8-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0d8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb0d8-116">See also</span></span>

- [<span data-ttu-id="eb0d8-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="eb0d8-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
