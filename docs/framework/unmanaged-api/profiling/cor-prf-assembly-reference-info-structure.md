---
title: Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867328"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="50af5-102">Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="50af5-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="50af5-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="50af5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="50af5-104">Fornece ao Common Language Runtime informações sobre uma referência de assembly que deve ser considerada ao realizar um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="50af5-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50af5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50af5-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="50af5-106">Membros</span><span class="sxs-lookup"><span data-stu-id="50af5-106">Members</span></span>  
  
|<span data-ttu-id="50af5-107">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="50af5-107">Member</span></span>|<span data-ttu-id="50af5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="50af5-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="50af5-109">Um ponteiro para a chave pública ou token do assembly.</span><span class="sxs-lookup"><span data-stu-id="50af5-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="50af5-110">O número de bytes na chave pública ou token.</span><span class="sxs-lookup"><span data-stu-id="50af5-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="50af5-111">O nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="50af5-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="50af5-112">Um ponteiro para os metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="50af5-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="50af5-113">Um ponteiro para um BLOB (objeto binário grande) de hash.</span><span class="sxs-lookup"><span data-stu-id="50af5-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="50af5-114">O número de bytes no BLOB de hash.</span><span class="sxs-lookup"><span data-stu-id="50af5-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="50af5-115">Os sinalizadores do assembly.</span><span class="sxs-lookup"><span data-stu-id="50af5-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50af5-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="50af5-116">Remarks</span></span>  
 <span data-ttu-id="50af5-117">A estrutura `COR_PRF_EX_CLAUSE_INFO` é preenchida pelo criador de perfil ao declarar as referências adicionais de assembly que o Common Language Runtime deve considerar quando realiza um exame de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="50af5-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="50af5-118">Se o criador de perfil se registrar para o método de retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , o tempo de execução passará o caminho e o nome do assembly a ser carregado, juntamente com um ponteiro para um objeto de interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) para esse método.</span><span class="sxs-lookup"><span data-stu-id="50af5-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="50af5-119">O criador de perfil pode então chamar o método [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) com um objeto `COR_PRF_ASSEMBLY_REFERENCE_INFO` para cada assembly de destino que planeja fazer referência a partir do assembly especificado no retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50af5-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50af5-120">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="50af5-120">Requirements</span></span>  
 <span data-ttu-id="50af5-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50af5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50af5-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="50af5-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50af5-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50af5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50af5-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50af5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50af5-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="50af5-125">See also</span></span>

- [<span data-ttu-id="50af5-126">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="50af5-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="50af5-127">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="50af5-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="50af5-128">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="50af5-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
