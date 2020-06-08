---
title: Método ICorProfilerInfo::GetModuleInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: 751f2ac44e543fed76c7031791bb57d75ed0fd48
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498096"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="80e43-102">Método ICorProfilerInfo::GetModuleInfo</span><span class="sxs-lookup"><span data-stu-id="80e43-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="80e43-103">Dada uma ID de módulo, retorna o nome do arquivo do módulo e a ID do assembly pai do módulo.</span><span class="sxs-lookup"><span data-stu-id="80e43-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80e43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80e43-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="80e43-106">no A ID do módulo para o qual as informações serão recuperadas.</span><span class="sxs-lookup"><span data-stu-id="80e43-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="80e43-107">fora O endereço base no qual o módulo é carregado.</span><span class="sxs-lookup"><span data-stu-id="80e43-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="80e43-108">no O comprimento, em caracteres, do `szName` buffer de retorno.</span><span class="sxs-lookup"><span data-stu-id="80e43-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="80e43-109">fora Um ponteiro para o comprimento total do caractere do nome de arquivo do módulo que é retornado.</span><span class="sxs-lookup"><span data-stu-id="80e43-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="80e43-110">fora Um buffer de caracteres largo fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="80e43-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="80e43-111">Quando o método retorna, esse buffer contém o nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="80e43-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="80e43-112">fora Um ponteiro para a ID do assembly pai do módulo.</span><span class="sxs-lookup"><span data-stu-id="80e43-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80e43-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="80e43-113">Remarks</span></span>  
 <span data-ttu-id="80e43-114">Para módulos dinâmicos, o `szName` parâmetro é uma cadeia de caracteres vazia e o endereço base é 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="80e43-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="80e43-115">Embora o `GetModuleInfo` método possa ser chamado assim que a ID do módulo existir, a ID do assembly pai não estará disponível até que o criador de perfil receba o retorno de chamada [ICorProfilerCallback:: ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="80e43-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="80e43-116">Quando `GetModuleInfo` retorna, você deve verificar se o `szName` buffer foi grande o suficiente para conter o nome de arquivo completo do módulo.</span><span class="sxs-lookup"><span data-stu-id="80e43-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="80e43-117">Para fazer isso, compare o valor que `pcchName` aponta com o valor do `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="80e43-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="80e43-118">Se `pcchName` apontar para um valor maior que `cchName` , aloque um `szName` buffer maior, atualize `cchName` com o tamanho novo, maior e chame `GetModuleInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="80e43-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="80e43-119">Como alternativa, você pode primeiro chamar `GetModuleInfo` com um buffer de comprimento zero `szName` para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="80e43-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="80e43-120">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetModuleInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="80e43-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e43-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80e43-121">Requirements</span></span>  
 <span data-ttu-id="80e43-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e43-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e43-123">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="80e43-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80e43-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80e43-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e43-125">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e43-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e43-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="80e43-126">See also</span></span>

- [<span data-ttu-id="80e43-127">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="80e43-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="80e43-128">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="80e43-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="80e43-129">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="80e43-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="80e43-130">Método GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="80e43-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
