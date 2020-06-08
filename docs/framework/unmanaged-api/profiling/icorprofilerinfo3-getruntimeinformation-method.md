---
title: Método ICorProfilerInfo3::GetRuntimeInformation
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496393"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="306ad-102">Método ICorProfilerInfo3::GetRuntimeInformation</span><span class="sxs-lookup"><span data-stu-id="306ad-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="306ad-103">Fornece informações de versão sobre o Common Language Runtime (CLR) cujo perfil está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="306ad-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="306ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="306ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="306ad-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="306ad-106">fora A ID representativa de uma instância CLR em execução em um processo.</span><span class="sxs-lookup"><span data-stu-id="306ad-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="306ad-107">Isso é o mesmo que os `ClrInstanceID` relatórios de eventos de inicialização do ETW (rastreamento de eventos para Windows).</span><span class="sxs-lookup"><span data-stu-id="306ad-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="306ad-108">fora O tipo de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="306ad-108">[out] The runtime type.</span></span> <span data-ttu-id="306ad-109">Esse parâmetro retorna `COR_PRF_DESKTOP_CLR` para a versão de área de trabalho do CLR ou `COR_PRF_CORE_CLR` para a versão principal do CLR usado no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="306ad-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="306ad-110">fora O número de versão principal do CLR.</span><span class="sxs-lookup"><span data-stu-id="306ad-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="306ad-111">fora O número de versão secundária do CLR.</span><span class="sxs-lookup"><span data-stu-id="306ad-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="306ad-112">fora O número de versão de compilação do CLR.</span><span class="sxs-lookup"><span data-stu-id="306ad-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="306ad-113">fora O número de versão do CLR associado a uma atualização de software.</span><span class="sxs-lookup"><span data-stu-id="306ad-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="306ad-114">no O comprimento, em caracteres, do buffer que `szVersionString` aponta para.</span><span class="sxs-lookup"><span data-stu-id="306ad-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="306ad-115">fora O comprimento, em caracteres, de `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="306ad-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="306ad-116">fora A cadeia de caracteres da versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="306ad-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="306ad-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="306ad-117">Remarks</span></span>  
 <span data-ttu-id="306ad-118">Você pode passar NULL para qualquer parâmetro.</span><span class="sxs-lookup"><span data-stu-id="306ad-118">You may pass null for any parameter.</span></span> <span data-ttu-id="306ad-119">No entanto, `pcchVersionString` não pode ser nulo, a menos que `szVersionString` também seja nulo.</span><span class="sxs-lookup"><span data-stu-id="306ad-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="306ad-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="306ad-120">Requirements</span></span>  
 <span data-ttu-id="306ad-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="306ad-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="306ad-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="306ad-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="306ad-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="306ad-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="306ad-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="306ad-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306ad-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="306ad-125">See also</span></span>

- [<span data-ttu-id="306ad-126">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="306ad-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="306ad-127">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="306ad-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="306ad-128">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="306ad-128">Profiling</span></span>](index.md)
