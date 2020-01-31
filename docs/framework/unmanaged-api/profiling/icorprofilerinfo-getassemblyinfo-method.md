---
title: Método ICorProfilerInfo::GetAssemblyInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 1e08d246136b33ffaaea91367d428e0bf2db99c1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864122"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="c4e17-102">Método ICorProfilerInfo::GetAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="c4e17-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="c4e17-103">Aceita uma ID de assembly e retorna o nome do assembly e a ID do seu módulo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="c4e17-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4e17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4e17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4e17-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="c4e17-106">no O identificador do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4e17-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c4e17-107">no O comprimento, em caracteres, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c4e17-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c4e17-108">fora Um ponteiro para o comprimento total do caractere do nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4e17-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4e17-109">fora Um buffer de caracteres largo fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="c4e17-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="c4e17-110">Quando a função retornar, ela conterá o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4e17-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="c4e17-111">fora Um ponteiro para a ID do domínio do aplicativo que contém o assembly.</span><span class="sxs-lookup"><span data-stu-id="c4e17-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="c4e17-112">fora Um ponteiro para a ID do módulo de manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4e17-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4e17-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4e17-113">Remarks</span></span>  
 <span data-ttu-id="c4e17-114">Após esse método retornar, você deve verificar se o buffer de `szName` era grande o suficiente para conter o nome completo do assembly.</span><span class="sxs-lookup"><span data-stu-id="c4e17-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="c4e17-115">Para fazer isso, compare o valor que `pcchName` aponta com o valor do parâmetro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="c4e17-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="c4e17-116">Se `pcchName` apontar para um valor maior que `cchName`, aloque um buffer de `szName` maior, atualize `cchName` com o tamanho novo, maior e chame `GetAssemblyInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="c4e17-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="c4e17-117">Como alternativa, você pode primeiro chamar `GetAssemblyInfo` com um buffer de `szName` de comprimento zero para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="c4e17-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c4e17-118">Em seguida, você pode ajustar o tamanho do buffer com base no valor retornado em `pcchName` e chamar `GetAssemblyInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="c4e17-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e17-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c4e17-119">Requirements</span></span>  
 <span data-ttu-id="c4e17-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e17-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e17-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4e17-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4e17-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4e17-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4e17-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e17-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e17-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="c4e17-124">See also</span></span>

- [<span data-ttu-id="c4e17-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c4e17-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c4e17-126">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c4e17-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c4e17-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="c4e17-127">Profiling</span></span>](index.md)
