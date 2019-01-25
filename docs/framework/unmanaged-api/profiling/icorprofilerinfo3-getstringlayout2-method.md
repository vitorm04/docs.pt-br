---
title: Método ICorProfilerInfo3::GetStringLayout2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ca40a0a172563368f971a83035c5dead66c70a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552002"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="bd35c-102">Método ICorProfilerInfo3::GetStringLayout2</span><span class="sxs-lookup"><span data-stu-id="bd35c-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="bd35c-103">Obtém informações sobre o layout de um objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bd35c-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="bd35c-104">Esse método substitui o [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bd35c-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd35c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd35c-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd35c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd35c-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="bd35c-107">[out] Um ponteiro para o deslocamento do local, relativo a `ObjectID` ponteiro, que armazena o comprimento da cadeia de caracteres em si.</span><span class="sxs-lookup"><span data-stu-id="bd35c-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="bd35c-108">O comprimento é armazenado como um `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bd35c-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="bd35c-109">[out] Um ponteiro para o deslocamento do buffer, em relação ao `ObjectID` ponteiro, que armazena a cadeia de caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="bd35c-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd35c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd35c-110">Remarks</span></span>  
 <span data-ttu-id="bd35c-111">Cadeias de caracteres podem ou não ser terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="bd35c-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd35c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd35c-112">Requirements</span></span>  
 <span data-ttu-id="bd35c-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd35c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd35c-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd35c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd35c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd35c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd35c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd35c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd35c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd35c-117">See also</span></span>
- [<span data-ttu-id="bd35c-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="bd35c-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bd35c-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bd35c-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
