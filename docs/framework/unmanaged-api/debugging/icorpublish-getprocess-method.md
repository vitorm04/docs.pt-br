---
title: Método ICorPublish::GetProcess
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: 2cd2238ac67713564922be440ce64a2ebc4bbf44
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396328"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="a17e0-102">Método ICorPublish::GetProcess</span><span class="sxs-lookup"><span data-stu-id="a17e0-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="a17e0-103">Obtém uma instância de [ICorPublishProcess](icorpublishprocess-interface.md) que representa o processo com o identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="a17e0-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a17e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a17e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a17e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a17e0-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="a17e0-106">no O identificador do processo.</span><span class="sxs-lookup"><span data-stu-id="a17e0-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a17e0-107">fora Um ponteiro para o endereço de uma `ICorPublishProcess` instância que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="a17e0-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a17e0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a17e0-108">Remarks</span></span>  
 <span data-ttu-id="a17e0-109">`GetProcess`falhará se o processo não existir ou não for um processo gerenciado que possa ser depurado pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="a17e0-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a17e0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a17e0-110">Requirements</span></span>  
 <span data-ttu-id="a17e0-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a17e0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a17e0-112">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a17e0-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a17e0-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a17e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a17e0-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17e0-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="a17e0-115">See also</span></span>

- [<span data-ttu-id="a17e0-116">Interface ICorPublish</span><span class="sxs-lookup"><span data-stu-id="a17e0-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
