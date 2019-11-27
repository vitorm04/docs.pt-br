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
ms.openlocfilehash: 277e2584049fae397cf91281a65d05b0b49d9454
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448079"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="d707f-102">Método ICeeGen::GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="d707f-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="d707f-103">Obtém o comprimento da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="d707f-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="d707f-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="d707f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d707f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d707f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d707f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d707f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d707f-107">no A seção de dados cujo comprimento será recuperado.</span><span class="sxs-lookup"><span data-stu-id="d707f-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="d707f-108">fora O comprimento retornado da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="d707f-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d707f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d707f-109">Remarks</span></span>  
 <span data-ttu-id="d707f-110">Chame `GetSectionDataLen` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="d707f-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d707f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d707f-111">Requirements</span></span>  
 <span data-ttu-id="d707f-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d707f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d707f-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d707f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d707f-114">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d707f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d707f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d707f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d707f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d707f-116">See also</span></span>

- [<span data-ttu-id="d707f-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="d707f-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
