---
title: "Método ICorDebugMetaDataLocator::GetMetaData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator.GetMetaData
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42c0548a626d43592184efa92619e74446058d58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="022fc-102">Método ICorDebugMetaDataLocator::GetMetaData</span><span class="sxs-lookup"><span data-stu-id="022fc-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="022fc-103">Solicita que o depurador para retornar o caminho completo para um módulo cujos metadados é necessária para concluir uma operação solicitado do depurador.</span><span class="sxs-lookup"><span data-stu-id="022fc-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="022fc-104">Syntax</span></span>  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="022fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="022fc-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="022fc-106">[in] Uma cadeia terminada em nulo que representa o caminho completo para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="022fc-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="022fc-107">Se o caminho completo não estiver disponível, o nome e a extensão do arquivo (*filename*. *extensão*).</span><span class="sxs-lookup"><span data-stu-id="022fc-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="022fc-108">[in] O carimbo de hora de cabeçalhos de arquivo PE da imagem.</span><span class="sxs-lookup"><span data-stu-id="022fc-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="022fc-109">Esse parâmetro potencialmente pode ser usado para um servidor de símbolos ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) pesquisa.</span><span class="sxs-lookup"><span data-stu-id="022fc-109">This parameter can potentially be used for a symbol server ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="022fc-110">[in] O tamanho da imagem de cabeçalhos de arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="022fc-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="022fc-111">Esse parâmetro potencialmente pode ser usado para uma pesquisa SymSrv.</span><span class="sxs-lookup"><span data-stu-id="022fc-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="022fc-112">[in] O caractere de contagem no `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="022fc-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="022fc-113">[out] A contagem de `WCHAR`s gravados `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="022fc-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="022fc-114">Se o método retornar E_NOT_SUFFICIENT_BUFFER, contém a contagem de `WCHAR`s necessários para o caminho do repositório.</span><span class="sxs-lookup"><span data-stu-id="022fc-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="022fc-115">[out] Ponteiro para um buffer no qual o depurador irá copiar o caminho completo do arquivo que contém os metadados solicitados.</span><span class="sxs-lookup"><span data-stu-id="022fc-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="022fc-116">O `ofReadOnly` sinalizador do [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração é usada para solicitar o acesso somente leitura para os metadados deste arquivo.</span><span class="sxs-lookup"><span data-stu-id="022fc-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="022fc-117">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="022fc-117">Return Value</span></span>  
 <span data-ttu-id="022fc-118">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="022fc-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="022fc-119">Todos os outros HRESULTs falha indicam que o arquivo não é recuperável.</span><span class="sxs-lookup"><span data-stu-id="022fc-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="022fc-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="022fc-120">HRESULT</span></span>|<span data-ttu-id="022fc-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="022fc-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="022fc-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="022fc-122">S_OK</span></span>|<span data-ttu-id="022fc-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="022fc-123">The method completed successfully.</span></span> <span data-ttu-id="022fc-124">`wszPathBuffer`contém o caminho completo para o arquivo e é terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="022fc-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="022fc-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="022fc-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="022fc-126">O tamanho atual de `wszPathBuffer` não é suficiente para conter o caminho completo.</span><span class="sxs-lookup"><span data-stu-id="022fc-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="022fc-127">Nesse caso, `pcchPathBuffer` contém a quantidade necessária de `WCHAR`s, incluindo o caractere null de terminação e `GetMetaData` é chamado uma segunda vez com o tamanho do buffer solicitado.</span><span class="sxs-lookup"><span data-stu-id="022fc-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="022fc-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="022fc-128">Remarks</span></span>  
 <span data-ttu-id="022fc-129">Se `wszImagePath` contém um caminho completo para um módulo de um despejo, especifica o caminho do computador onde o despejo de memória foi coletado.</span><span class="sxs-lookup"><span data-stu-id="022fc-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="022fc-130">O arquivo pode não existir neste local, ou um arquivo incorreto com o mesmo nome pode ser armazenado no caminho.</span><span class="sxs-lookup"><span data-stu-id="022fc-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="022fc-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="022fc-131">Requirements</span></span>  
 <span data-ttu-id="022fc-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="022fc-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="022fc-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="022fc-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="022fc-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="022fc-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="022fc-135">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="022fc-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="022fc-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="022fc-136">See Also</span></span>  
 [<span data-ttu-id="022fc-137">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="022fc-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="022fc-138">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="022fc-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="022fc-139">Depuração</span><span class="sxs-lookup"><span data-stu-id="022fc-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
