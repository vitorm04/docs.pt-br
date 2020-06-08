---
title: Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 861b31e5621e9a7b40403d249c6a5c8c4ac25db8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501034"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="6602b-102">Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="6602b-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="6602b-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="6602b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6602b-104">Fornece ao Common Language Runtime informações sobre uma referência de assembly que deve ser considerada ao realizar um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="6602b-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6602b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6602b-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6602b-106">Membros</span><span class="sxs-lookup"><span data-stu-id="6602b-106">Members</span></span>  
  
|<span data-ttu-id="6602b-107">Membro</span><span class="sxs-lookup"><span data-stu-id="6602b-107">Member</span></span>|<span data-ttu-id="6602b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="6602b-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="6602b-109">Um ponteiro para a chave pública ou token do assembly.</span><span class="sxs-lookup"><span data-stu-id="6602b-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="6602b-110">O número de bytes na chave pública ou token.</span><span class="sxs-lookup"><span data-stu-id="6602b-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="6602b-111">O nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="6602b-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="6602b-112">Um ponteiro para os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="6602b-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="6602b-113">Um ponteiro para um BLOB (objeto binário grande) de hash.</span><span class="sxs-lookup"><span data-stu-id="6602b-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="6602b-114">O número de bytes no BLOB de hash.</span><span class="sxs-lookup"><span data-stu-id="6602b-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="6602b-115">Os sinalizadores do assembly.</span><span class="sxs-lookup"><span data-stu-id="6602b-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6602b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6602b-116">Remarks</span></span>  
 <span data-ttu-id="6602b-117">A estrutura `COR_PRF_EX_CLAUSE_INFO` é preenchida pelo criador de perfil ao declarar as referências adicionais de assembly que o Common Language Runtime deve considerar quando realiza um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="6602b-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="6602b-118">Se o criador de perfil se registrar para o método de retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , o tempo de execução passará o caminho e o nome do assembly a ser carregado, juntamente com um ponteiro para um objeto de interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) para esse método.</span><span class="sxs-lookup"><span data-stu-id="6602b-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="6602b-119">O criador de perfil pode então chamar o método [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) com um `COR_PRF_ASSEMBLY_REFERENCE_INFO` objeto para cada assembly de destino que planeja fazer referência a partir do assembly especificado no retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6602b-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6602b-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6602b-120">Requirements</span></span>  
 <span data-ttu-id="6602b-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6602b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6602b-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6602b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6602b-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6602b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6602b-124">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6602b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6602b-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="6602b-125">See also</span></span>

- [<span data-ttu-id="6602b-126">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6602b-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="6602b-127">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="6602b-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="6602b-128">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="6602b-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
