---
title: Função CreateVersionStringFromModule
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ed8b85475dc7327c1aac6f920aba627215e27c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492017"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="d6ab4-102">Função CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="d6ab4-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="d6ab4-103">Cria uma cadeia de caracteres de versão de um caminho de runtime (CLR) de linguagem comum em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ab4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6ab4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d6ab4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6ab4-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="d6ab4-106">[in] Identificador do processo no qual o CLR de destino é carregado.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="d6ab4-107">[in] Caminho completo ou relativo para o CLR que é carregado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="d6ab4-108">[out] Retorne o buffer para armazenar a cadeia de caracteres de versão para o CLR de destino.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d6ab4-109">[in] Tamanho de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="d6ab4-110">[out] Comprimento da cadeia de caracteres de versão retornada pelo `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6ab4-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6ab4-111">Return Value</span></span>  
 <span data-ttu-id="d6ab4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6ab4-112">S_OK</span></span>  
 <span data-ttu-id="d6ab4-113">A cadeia de caracteres de versão para o CLR de destino foi retornada com êxito no `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="d6ab4-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d6ab4-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="d6ab4-115">`szModuleName` é null ou uma `pBuffer` ou `cchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="d6ab4-116">`pBuffer` e `cchBuffer` devem ser ambos nulos ou não nulo.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="d6ab4-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="d6ab4-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="d6ab4-118">`pdwLength` é maior que `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="d6ab4-119">Isso pode ser um resultado esperado se você passar null para ambos `pBuffer` e `cchBuffer`e consultou o tamanho do buffer necessário usando `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="d6ab4-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="d6ab4-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="d6ab4-121">`szModuleName` não contém um caminho para um CLR válido no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="d6ab4-122">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="d6ab4-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d6ab4-123">`pidDebuggee` não faz referência a um processo válido ou outra falha.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6ab4-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6ab4-124">Remarks</span></span>  
 <span data-ttu-id="d6ab4-125">Essa função aceita um processo CLR é identificado por `pidDebuggee` e um caminho de cadeia de caracteres que é especificado pelo `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="d6ab4-126">A cadeia de caracteres de versão é retornada no buffer que `pBuffer` aponta.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="d6ab4-127">Essa cadeia de caracteres é opaca para o usuário de função; ou seja, não há nenhum significado intrínseco na cadeia de versão em si.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="d6ab4-128">Ele é usado somente no contexto dessa função e o [função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="d6ab4-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="d6ab4-129">Essa função deve ser chamada duas vezes.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-129">This function should be called twice.</span></span> <span data-ttu-id="d6ab4-130">Quando você chamá-lo na primeira vez, passar null para ambos `pBuffer` e `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="d6ab4-131">Quando você fizer isso, o tamanho do buffer necessário para `pBuffer` será retornado em `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="d6ab4-132">Em seguida, você pode chamar a função uma segunda vez e passar o buffer no `pBuffer` e seu tamanho em `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6ab4-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ab4-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6ab4-133">Requirements</span></span>  
 <span data-ttu-id="d6ab4-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ab4-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ab4-135">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="d6ab4-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="d6ab4-136">**Biblioteca:** dbgshim</span><span class="sxs-lookup"><span data-stu-id="d6ab4-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="d6ab4-137">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d6ab4-137">**.NET Framework Versions:** 3.5 SP1</span></span>
