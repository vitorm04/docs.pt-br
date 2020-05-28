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
ms.openlocfilehash: 1855c73849c35bf709b0af261a88e6cd7a40abfb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008294"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="0b42a-102">Método ICeeGen::GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="0b42a-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="0b42a-103">Obtém o comprimento da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="0b42a-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="0b42a-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="0b42a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b42a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b42a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b42a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b42a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="0b42a-107">no A seção de dados cujo comprimento será recuperado.</span><span class="sxs-lookup"><span data-stu-id="0b42a-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="0b42a-108">fora O comprimento retornado da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="0b42a-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b42a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b42a-109">Remarks</span></span>  
 <span data-ttu-id="0b42a-110">Chame `GetSectionDataLen` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="0b42a-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b42a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b42a-111">Requirements</span></span>  
 <span data-ttu-id="0b42a-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b42a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b42a-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b42a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b42a-114">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b42a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b42a-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b42a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b42a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="0b42a-116">See also</span></span>

- [<span data-ttu-id="0b42a-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="0b42a-117">ICeeGen Interface</span></span>](iceegen-interface.md)
