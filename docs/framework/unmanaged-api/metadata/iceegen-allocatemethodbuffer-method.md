---
title: Método ICeeGen::AllocateMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 8dc7f439cac56c2d55916ff8631ec3095c67680d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008879"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="9fec9-102">Método ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="9fec9-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="9fec9-103">Cria um buffer do tamanho especificado para um método e Obtém o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="9fec9-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="9fec9-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="9fec9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fec9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fec9-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fec9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fec9-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="9fec9-107">no O comprimento do buffer a ser criado.</span><span class="sxs-lookup"><span data-stu-id="9fec9-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="9fec9-108">fora O buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="9fec9-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="9fec9-109">fora O endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="9fec9-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fec9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fec9-110">Requirements</span></span>  
 <span data-ttu-id="9fec9-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fec9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fec9-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9fec9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fec9-113">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9fec9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fec9-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fec9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fec9-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="9fec9-115">See also</span></span>

- [<span data-ttu-id="9fec9-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="9fec9-116">ICeeGen Interface</span></span>](iceegen-interface.md)
