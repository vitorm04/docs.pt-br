---
title: "Método ICeeGen::GetSectionDataLen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionDataLen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7d119fdfe5c0202d08ca78026a6917bb4ef51422
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="18d70-102">Método ICeeGen::GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="18d70-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="18d70-103">Obtém o comprimento da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="18d70-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="18d70-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="18d70-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18d70-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18d70-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18d70-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18d70-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="18d70-107">[in] A seção de dados cujo comprimento será recuperado.</span><span class="sxs-lookup"><span data-stu-id="18d70-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="18d70-108">[out] O comprimento retornado da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="18d70-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18d70-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="18d70-109">Remarks</span></span>  
 <span data-ttu-id="18d70-110">Chamar `GetSectionDataLen` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="18d70-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18d70-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18d70-111">Requirements</span></span>  
 <span data-ttu-id="18d70-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18d70-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18d70-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18d70-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18d70-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="18d70-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18d70-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18d70-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d70-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18d70-116">See Also</span></span>  
 [<span data-ttu-id="18d70-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="18d70-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
