---
title: Método ICorProfilerInfo::GetAppDomainInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 5e5510ec098b2c1aa3b768830b812328287fd31a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503023"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="733b4-102">Método ICorProfilerInfo::GetAppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="733b4-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="733b4-103">Aceita uma ID de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="733b4-103">Accepts an application domain ID.</span></span> <span data-ttu-id="733b4-104">Retorna um nome de domínio de aplicativo e a ID do processo que o contém.</span><span class="sxs-lookup"><span data-stu-id="733b4-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733b4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="733b4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="733b4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="733b4-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="733b4-107">no A ID do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="733b4-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="733b4-108">no O comprimento, em caracteres, do `szName` buffer de retorno.</span><span class="sxs-lookup"><span data-stu-id="733b4-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="733b4-109">fora Um ponteiro para o tamanho total do caractere do nome de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="733b4-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="733b4-110">fora Um buffer de caracteres largo fornecido pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="733b4-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="733b4-111">Quando o método retornar, `szName` conterá o nome de domínio do aplicativo completo ou parcial.</span><span class="sxs-lookup"><span data-stu-id="733b4-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="733b4-112">fora Um ponteiro para a ID do processo que contém o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="733b4-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="733b4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="733b4-113">Remarks</span></span>  
 <span data-ttu-id="733b4-114">Depois que esse método retornar, você deverá verificar se o `szName` buffer era grande o suficiente para conter o nome completo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="733b4-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="733b4-115">Para fazer isso, compare o valor que `pcchName` aponta com o valor do `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="733b4-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="733b4-116">Se `pcchName` apontar para um valor maior que `cchName` , aloque um `szName` buffer maior, atualize `cchName` com o tamanho novo, maior e chame `GetAppDomainInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="733b4-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="733b4-117">Como alternativa, você pode primeiro chamar `GetAppDomainInfo` com um buffer de comprimento zero `szName` para obter o tamanho de buffer correto.</span><span class="sxs-lookup"><span data-stu-id="733b4-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="733b4-118">Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetAppDomainInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="733b4-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="733b4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="733b4-119">Requirements</span></span>  
 <span data-ttu-id="733b4-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="733b4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="733b4-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="733b4-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="733b4-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="733b4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="733b4-123">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733b4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733b4-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="733b4-124">See also</span></span>

- [<span data-ttu-id="733b4-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="733b4-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="733b4-126">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="733b4-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="733b4-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="733b4-127">Profiling</span></span>](index.md)
