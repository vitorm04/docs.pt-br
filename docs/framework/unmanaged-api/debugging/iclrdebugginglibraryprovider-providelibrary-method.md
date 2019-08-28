---
title: Método ICLRDebuggingLibraryProvider::ProvideLibrary
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b02bb74a61e64a3ed9875fcf88e018de9f6317
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041436"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="2edaf-102">Método ICLRDebuggingLibraryProvider::ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="2edaf-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="2edaf-103">Obtém uma interface de retorno de chamada do provedor de biblioteca que permite que bibliotecas de depuração específicas à versão Common Language Runtime (CLR) sejam localizadas e carregadas sob demanda.</span><span class="sxs-lookup"><span data-stu-id="2edaf-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="2edaf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2edaf-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="2edaf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2edaf-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="2edaf-106">no O nome do módulo que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="2edaf-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="2edaf-107">no O carimbo de data/hora armazenado no cabeçalho de arquivo COFF de arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="2edaf-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="2edaf-108">no O `SizeOfImage` campo armazenado no cabeçalho de arquivo opcional COFF de arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="2edaf-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="2edaf-109">fora O identificador para o módulo solicitado.</span><span class="sxs-lookup"><span data-stu-id="2edaf-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="2edaf-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2edaf-110">Return Value</span></span>

<span data-ttu-id="2edaf-111">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="2edaf-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="2edaf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2edaf-112">HRESULT</span></span>|<span data-ttu-id="2edaf-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2edaf-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="2edaf-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2edaf-114">S_OK</span></span>|<span data-ttu-id="2edaf-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="2edaf-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="2edaf-116">Exceções</span><span class="sxs-lookup"><span data-stu-id="2edaf-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="2edaf-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="2edaf-117">Remarks</span></span>

<span data-ttu-id="2edaf-118">`ProvideLibrary`permite que o depurador forneça módulos que são necessários para depurar arquivos CLR específicos, como MSCorDbi. dll e Mscordacwks. dll.</span><span class="sxs-lookup"><span data-stu-id="2edaf-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="2edaf-119">Os identificadores de módulo precisam permanecer válidos até que uma chamada para o método [ICLRDebugging:: CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) indique que eles podem ser liberados. nesse ponto, é responsabilidade do chamador liberar os identificadores.</span><span class="sxs-lookup"><span data-stu-id="2edaf-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="2edaf-120">O depurador pode usar qualquer meio disponível para localizar ou adquirir o módulo de depuração.</span><span class="sxs-lookup"><span data-stu-id="2edaf-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2edaf-121">Esse recurso permite que o chamador da API forneça módulos que contêm um código executável e possivelmente mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="2edaf-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="2edaf-122">Como uma precaução de segurança, o chamador não deve `ProvideLibrary` usar o para distribuir nenhum código que não esteja disposto a ser executado.</span><span class="sxs-lookup"><span data-stu-id="2edaf-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="2edaf-123">Se um problema de segurança sério for descoberto em uma biblioteca já liberada, como MSCorDbi. dll ou Mscordacwks. dll, o Shim poderá ser corrigido para reconhecer as versões inadequadas dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="2edaf-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="2edaf-124">O Shim pode emitir solicitações para as versões com patches dos arquivos e rejeitar as versões inadequadas se elas forem fornecidas em resposta a qualquer solicitação.</span><span class="sxs-lookup"><span data-stu-id="2edaf-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="2edaf-125">Isso só poderá ocorrer se o usuário tiver corrigido o patch para uma nova versão do Shim.</span><span class="sxs-lookup"><span data-stu-id="2edaf-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="2edaf-126">As versões sem patch continuarão vulneráveis.</span><span class="sxs-lookup"><span data-stu-id="2edaf-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="2edaf-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2edaf-127">Requirements</span></span>

<span data-ttu-id="2edaf-128">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2edaf-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="2edaf-129">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2edaf-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2edaf-130">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2edaf-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2edaf-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2edaf-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2edaf-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2edaf-132">See also</span></span>

- [<span data-ttu-id="2edaf-133">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2edaf-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2edaf-134">Depuração</span><span class="sxs-lookup"><span data-stu-id="2edaf-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
