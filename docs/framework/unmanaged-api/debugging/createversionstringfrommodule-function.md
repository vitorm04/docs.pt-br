---
title: "Função CreateVersionStringFromModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d7d545256393cfbe37216f0d6db064d5e7cb410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="00728-102">Função CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="00728-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="00728-103">Cria uma cadeia de caracteres de versão de um caminho de runtime (CLR) de linguagem comum em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="00728-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00728-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00728-104">Syntax</span></span>  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00728-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00728-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="00728-106">[in] Identificador do processo no qual o destino CLR é carregado.</span><span class="sxs-lookup"><span data-stu-id="00728-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="00728-107">[in] Caminho completo ou relativo para o CLR que é carregado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="00728-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="00728-108">[out] Retorna o buffer para armazenar a cadeia de caracteres de versão do CLR de destino.</span><span class="sxs-lookup"><span data-stu-id="00728-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="00728-109">[in] Tamanho de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="00728-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="00728-110">[out] Comprimento da cadeia de caracteres de versão retornado por `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="00728-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00728-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="00728-111">Return Value</span></span>  
 <span data-ttu-id="00728-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00728-112">S_OK</span></span>  
 <span data-ttu-id="00728-113">A cadeia de caracteres de versão para o destino do CLR foi retornada com êxito no `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="00728-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="00728-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00728-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="00728-115">`szModuleName`é null ou uma `pBuffer` ou `cchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="00728-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="00728-116">`pBuffer`e `cchBuffer` devem ser nulos ou não nulo.</span><span class="sxs-lookup"><span data-stu-id="00728-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="00728-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="00728-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="00728-118">`pdwLength` é maior que `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="00728-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="00728-119">Isso pode ser um resultado esperado se você passar null para ambos `pBuffer` e `cchBuffer`e consultar o tamanho do buffer necessário usando `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="00728-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="00728-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="00728-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="00728-121">`szModuleName`não contém um caminho para um CLR válido no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="00728-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="00728-122">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="00728-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="00728-123">`pidDebuggee`não faz referência a um processo válido ou outra falha.</span><span class="sxs-lookup"><span data-stu-id="00728-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00728-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="00728-124">Remarks</span></span>  
 <span data-ttu-id="00728-125">Essa função aceita um processo CLR que é identificado pelo `pidDebuggee` e um caminho de cadeia de caracteres que é especificado pelo `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="00728-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="00728-126">A cadeia de caracteres de versão é retornada no buffer que `pBuffer` aponta para.</span><span class="sxs-lookup"><span data-stu-id="00728-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="00728-127">Essa cadeia de caracteres é opaca para o usuário de função; ou seja, não há nenhum significado intrínseco na cadeia de versão em si.</span><span class="sxs-lookup"><span data-stu-id="00728-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="00728-128">Ele é usado somente no contexto dessa função e o [função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="00728-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="00728-129">Essa função deve ser chamada duas vezes.</span><span class="sxs-lookup"><span data-stu-id="00728-129">This function should be called twice.</span></span> <span data-ttu-id="00728-130">Quando você chamá-lo na primeira vez, passar null para ambos `pBuffer` e `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="00728-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="00728-131">Quando você fizer isso, o tamanho do buffer necessário para `pBuffer` será retornado no `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="00728-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="00728-132">Em seguida, você pode chamar a função uma segunda vez e passar o buffer no `pBuffer` e seu tamanho no `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="00728-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00728-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00728-133">Requirements</span></span>  
 <span data-ttu-id="00728-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00728-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00728-135">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="00728-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="00728-136">**Biblioteca:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="00728-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="00728-137">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="00728-137">**.NET Framework Versions:** 3.5 SP1</span></span>
