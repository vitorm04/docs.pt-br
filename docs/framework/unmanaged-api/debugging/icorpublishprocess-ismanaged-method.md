---
title: Método ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421092"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="48ab6-102">Método ICorPublishProcess::IsManaged</span><span class="sxs-lookup"><span data-stu-id="48ab6-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="48ab6-103">Obtém um valor que indica se o processo referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md) é conhecido por ter código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="48ab6-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ab6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48ab6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48ab6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48ab6-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="48ab6-106">fora Um ponteiro para um valor booliano que indica se o processo tem código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="48ab6-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="48ab6-107">O valor é `true` se o processo tiver código gerenciado; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="48ab6-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48ab6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="48ab6-108">Remarks</span></span>  
 <span data-ttu-id="48ab6-109">Como a versão atual do `ICorPublishProcess` permite acesso apenas a processos que têm código gerenciado, o `IsManaged` sempre retorna `true` .</span><span class="sxs-lookup"><span data-stu-id="48ab6-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48ab6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48ab6-110">Requirements</span></span>  
 <span data-ttu-id="48ab6-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48ab6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48ab6-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="48ab6-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="48ab6-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48ab6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48ab6-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48ab6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ab6-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="48ab6-115">See also</span></span>

- [<span data-ttu-id="48ab6-116">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="48ab6-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
