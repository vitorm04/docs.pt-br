---
title: Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: ac7ddeed5694ad0ae6ef3d4a11fcb1fb23755b8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123224"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="11cb7-102">Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="11cb7-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="11cb7-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="11cb7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="11cb7-104">Fornece ao Common Language Runtime informações sobre uma referência de assembly que deve ser considerada ao realizar um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="11cb7-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11cb7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11cb7-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="11cb7-106">Membros</span><span class="sxs-lookup"><span data-stu-id="11cb7-106">Members</span></span>  
  
|<span data-ttu-id="11cb7-107">Membro</span><span class="sxs-lookup"><span data-stu-id="11cb7-107">Member</span></span>|<span data-ttu-id="11cb7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="11cb7-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="11cb7-109">Um ponteiro para a chave pública ou token do assembly.</span><span class="sxs-lookup"><span data-stu-id="11cb7-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="11cb7-110">O número de bytes na chave pública ou token.</span><span class="sxs-lookup"><span data-stu-id="11cb7-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="11cb7-111">O nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="11cb7-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="11cb7-112">Um ponteiro para os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="11cb7-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="11cb7-113">Um ponteiro para um BLOB (objeto binário grande) de hash.</span><span class="sxs-lookup"><span data-stu-id="11cb7-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="11cb7-114">O número de bytes no BLOB de hash.</span><span class="sxs-lookup"><span data-stu-id="11cb7-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="11cb7-115">Os sinalizadores do assembly.</span><span class="sxs-lookup"><span data-stu-id="11cb7-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11cb7-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="11cb7-116">Remarks</span></span>  
 <span data-ttu-id="11cb7-117">A estrutura `COR_PRF_EX_CLAUSE_INFO` é preenchida pelo criador de perfil ao declarar as referências adicionais de assembly que o Common Language Runtime deve considerar quando realiza um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="11cb7-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="11cb7-118">Se o criador de perfil se registrar para o método de retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , o tempo de execução passará o caminho e o nome do assembly a ser carregado, juntamente com um ponteiro para um [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objeto de interface para esse método.</span><span class="sxs-lookup"><span data-stu-id="11cb7-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="11cb7-119">O criador de perfil pode então chamar o método [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) com um objeto `COR_PRF_ASSEMBLY_REFERENCE_INFO` para cada assembly de destino que planeja fazer referência a partir do assembly especificado no [ICorProfilerCallback6:: ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)Retorno de chamada GetAssemblyReferences.</span><span class="sxs-lookup"><span data-stu-id="11cb7-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11cb7-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11cb7-120">Requirements</span></span>  
 <span data-ttu-id="11cb7-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11cb7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11cb7-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="11cb7-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11cb7-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11cb7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11cb7-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11cb7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11cb7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11cb7-125">See also</span></span>

- [<span data-ttu-id="11cb7-126">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="11cb7-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="11cb7-127">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="11cb7-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="11cb7-128">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="11cb7-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
