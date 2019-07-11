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
ms.openlocfilehash: 1ac724db000f84e37995a34e808d3df4b1e7a960
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765412"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="e25d7-102">Método ICorProfilerInfo3::GetStringLayout2</span><span class="sxs-lookup"><span data-stu-id="e25d7-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="e25d7-103">Obtém informações sobre o layout de um objeto de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e25d7-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="e25d7-104">Esse método substitui o [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e25d7-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e25d7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e25d7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e25d7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e25d7-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="e25d7-107">[out] Um ponteiro para o deslocamento do local, relativo a `ObjectID` ponteiro, que armazena o comprimento da cadeia de caracteres em si.</span><span class="sxs-lookup"><span data-stu-id="e25d7-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="e25d7-108">O comprimento é armazenado como um `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e25d7-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e25d7-109">[out] Um ponteiro para o deslocamento do buffer, em relação ao `ObjectID` ponteiro, que armazena a cadeia de caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="e25d7-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e25d7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e25d7-110">Remarks</span></span>  
 <span data-ttu-id="e25d7-111">Cadeias de caracteres podem ou não ser terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e25d7-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e25d7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e25d7-112">Requirements</span></span>  
 <span data-ttu-id="e25d7-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e25d7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e25d7-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e25d7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e25d7-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e25d7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e25d7-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e25d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25d7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e25d7-117">See also</span></span>

- [<span data-ttu-id="e25d7-118">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="e25d7-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e25d7-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e25d7-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
