---
title: "Método ICLRDebuggingLibraryProvider::ProvideLibrary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3a34579787e976022ffa8caf7c29d8a565a7c73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="1ef8a-102">Método ICLRDebuggingLibraryProvider::ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="1ef8a-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="1ef8a-103">Obtém um provedor de biblioteca de interface de retorno de chamada que permite common language runtime (CLR) específicos da versão depuração bibliotecas de ser localizada e carregada na demanda.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ef8a-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ef8a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ef8a-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="1ef8a-106">[in] O nome do módulo que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-106">[in] The name of the module being requested .</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="1ef8a-107">[in] O carimbo de hora de data armazenado no cabeçalho do arquivo COFF dos arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="1ef8a-108">[in] O `SizeOfImage` campo armazenado no cabeçalho COFF opcional de arquivo dos arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="1ef8a-109">[out] O identificador para o módulo solicitado.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ef8a-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1ef8a-110">Return Value</span></span>  
 <span data-ttu-id="1ef8a-111">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1ef8a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ef8a-112">HRESULT</span></span>|<span data-ttu-id="1ef8a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ef8a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ef8a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ef8a-114">S_OK</span></span>|<span data-ttu-id="1ef8a-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1ef8a-116">Exceções</span><span class="sxs-lookup"><span data-stu-id="1ef8a-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef8a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ef8a-117">Remarks</span></span>  
 <span data-ttu-id="1ef8a-118">`ProvideLibrary`permite que o depurador fornecer os módulos que são necessários para a depuração de arquivos específicos do CLR como mscordbi.dll e qual mscordacwks.dll.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="1ef8a-119">Os identificadores de módulo precisam permanecer válida até uma chamada para o [: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) método indica que eles podem ser liberados, no ponto em que é de responsabilidade do chamador para liberar os identificadores.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="1ef8a-120">O depurador pode usar qualquer meio disponível para localizar ou adquirir o módulo de depuração.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1ef8a-121">Esse recurso permite que o chamador de API fornecer os módulos que contêm código executável e possivelmente mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="1ef8a-122">Como uma precaução de segurança, o chamador não deve usar `ProvideLibrary` para distribuir qualquer código que não está disposto a execute em si.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="1ef8a-123">Se for detectado um problema sério de segurança em uma biblioteca já lançada, como mscordbi.dll ou qual mscordacwks.dll, a correção poderá ser corrigida para reconhecer as versões incorretas dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="1ef8a-124">O shim pode emitir solicitações para as versões com patch dos arquivos e rejeitar as versões incorretas se eles são fornecidos em resposta a qualquer solicitação.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="1ef8a-125">Isso pode ocorrer somente se o usuário tem o patch para uma nova versão do shim.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="1ef8a-126">Versões sem patch permanecerá vulneráveis.</span><span class="sxs-lookup"><span data-stu-id="1ef8a-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef8a-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ef8a-127">Requirements</span></span>  
 <span data-ttu-id="1ef8a-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef8a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef8a-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ef8a-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ef8a-130">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef8a-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef8a-131">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef8a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef8a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ef8a-132">See Also</span></span>  
 [<span data-ttu-id="1ef8a-133">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="1ef8a-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1ef8a-134">Depuração</span><span class="sxs-lookup"><span data-stu-id="1ef8a-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
