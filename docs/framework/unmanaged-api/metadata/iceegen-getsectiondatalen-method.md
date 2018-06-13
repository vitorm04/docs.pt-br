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
ms.openlocfilehash: b85cdee4a65e91c51fdb014bdcc4797b99214daf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446125"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="732cf-102">Método ICeeGen::GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="732cf-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="732cf-103">Obtém o comprimento da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="732cf-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="732cf-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="732cf-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="732cf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="732cf-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="732cf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="732cf-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="732cf-107">[in] A seção de dados cujo comprimento será recuperado.</span><span class="sxs-lookup"><span data-stu-id="732cf-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="732cf-108">[out] O comprimento retornado da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="732cf-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="732cf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="732cf-109">Remarks</span></span>  
 <span data-ttu-id="732cf-110">Chamar `GetSectionDataLen` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="732cf-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="732cf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="732cf-111">Requirements</span></span>  
 <span data-ttu-id="732cf-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="732cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="732cf-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="732cf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="732cf-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="732cf-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="732cf-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="732cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="732cf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="732cf-116">See Also</span></span>  
 [<span data-ttu-id="732cf-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="732cf-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
