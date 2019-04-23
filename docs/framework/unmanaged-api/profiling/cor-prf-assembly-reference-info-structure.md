---
title: Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fa1cc05ee583cf1bd59235fcd9821d1c92d21f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101426"
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="2410f-102">Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="2410f-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="2410f-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="2410f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2410f-104">Fornece ao Common Language Runtime informações sobre uma referência de assembly que deve ser considerada ao realizar um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="2410f-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2410f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2410f-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2410f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="2410f-106">Members</span></span>  
  
|<span data-ttu-id="2410f-107">Membro</span><span class="sxs-lookup"><span data-stu-id="2410f-107">Member</span></span>|<span data-ttu-id="2410f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2410f-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="2410f-109">Um ponteiro para a chave pública ou token do assembly.</span><span class="sxs-lookup"><span data-stu-id="2410f-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="2410f-110">O número de bytes na chave pública ou token.</span><span class="sxs-lookup"><span data-stu-id="2410f-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="2410f-111">O nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="2410f-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="2410f-112">Um ponteiro para os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="2410f-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="2410f-113">Um ponteiro para um BLOB (objeto binário grande) de hash.</span><span class="sxs-lookup"><span data-stu-id="2410f-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="2410f-114">O número de bytes no BLOB de hash.</span><span class="sxs-lookup"><span data-stu-id="2410f-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="2410f-115">Os sinalizadores do assembly.</span><span class="sxs-lookup"><span data-stu-id="2410f-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2410f-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="2410f-116">Remarks</span></span>  
 <span data-ttu-id="2410f-117">A estrutura `COR_PRF_EX_CLAUSE_INFO` é preenchida pelo criador de perfil ao declarar as referências adicionais de assembly que o Common Language Runtime deve considerar quando realiza um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="2410f-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="2410f-118">Se o criador de perfil for registrado para o [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) método de retorno de chamada, o tempo de execução passa o caminho e o nome do assembly a ser carregado, juntamente com um ponteiro para um [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) o objeto de interface para esse método.</span><span class="sxs-lookup"><span data-stu-id="2410f-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="2410f-119">O criador de perfil, em seguida, pode chamar o [icorprofilerassemblyreferenceprovider:: Addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) método com um `COR_PRF_ASSEMBLY_REFERENCE_INFO` objeto para cada assembly de destino que planejar referenciar a partir do assembly especificado no [ ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="2410f-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2410f-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2410f-120">Requirements</span></span>  
 <span data-ttu-id="2410f-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2410f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2410f-122">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2410f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2410f-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2410f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2410f-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2410f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2410f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2410f-125">See also</span></span>

- [<span data-ttu-id="2410f-126">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2410f-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="2410f-127">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="2410f-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="2410f-128">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="2410f-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
