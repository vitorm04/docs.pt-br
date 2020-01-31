---
title: Método ICorDebugMetaDataLocator::GetMetaData
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
ms.openlocfilehash: 43f3c1dd866b98bff51b375a11e28727e41d3ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793045"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="2f349-102">Método ICorDebugMetaDataLocator::GetMetaData</span><span class="sxs-lookup"><span data-stu-id="2f349-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="2f349-103">Solicita que o depurador retorne o caminho completo para um módulo cujos metadados são necessários para concluir uma operação solicitada pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="2f349-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f349-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f349-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="2f349-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f349-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="2f349-106">no Uma cadeia de caracteres terminada em nulo que representa o caminho completo para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f349-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="2f349-107">Se o caminho completo não estiver disponível, o nome e a extensão do arquivo (*filename*. *extensão*).</span><span class="sxs-lookup"><span data-stu-id="2f349-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="2f349-108">no O carimbo de data/hora dos cabeçalhos de arquivo PE da imagem.</span><span class="sxs-lookup"><span data-stu-id="2f349-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="2f349-109">Esse parâmetro pode potencialmente ser usado para uma pesquisa de servidor de símbolo ([symsrv](/windows/desktop/debug/using-symsrv)).</span><span class="sxs-lookup"><span data-stu-id="2f349-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="2f349-110">no O tamanho da imagem dos cabeçalhos de arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="2f349-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="2f349-111">Esse parâmetro pode potencialmente ser usado para uma pesquisa SymSrv.</span><span class="sxs-lookup"><span data-stu-id="2f349-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="2f349-112">no A contagem de caracteres em `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2f349-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="2f349-113">fora A contagem de `WCHAR`s gravados em `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2f349-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="2f349-114">Se o método retornar E_NOT_SUFFICIENT_BUFFER, conterá a contagem de `WCHAR`s necessários para armazenar o caminho.</span><span class="sxs-lookup"><span data-stu-id="2f349-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="2f349-115">fora Ponteiro para um buffer no qual o depurador irá copiar o caminho completo do arquivo que contém os metadados solicitados.</span><span class="sxs-lookup"><span data-stu-id="2f349-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="2f349-116">O sinalizador de `ofReadOnly` da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) é usado para solicitar acesso somente leitura aos metadados nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="2f349-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f349-117">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2f349-117">Return Value</span></span>  
 <span data-ttu-id="2f349-118">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="2f349-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="2f349-119">Todos os outros HRESULTs de falha indicam que o arquivo não é recuperável.</span><span class="sxs-lookup"><span data-stu-id="2f349-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="2f349-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f349-120">HRESULT</span></span>|<span data-ttu-id="2f349-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f349-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f349-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f349-122">S_OK</span></span>|<span data-ttu-id="2f349-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="2f349-123">The method completed successfully.</span></span> <span data-ttu-id="2f349-124">`wszPathBuffer` contém o caminho completo para o arquivo e é encerrado em nulo.</span><span class="sxs-lookup"><span data-stu-id="2f349-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="2f349-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2f349-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2f349-126">O tamanho atual de `wszPathBuffer` não é suficiente para manter o caminho completo.</span><span class="sxs-lookup"><span data-stu-id="2f349-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="2f349-127">Nesse caso, `pcchPathBuffer` contém a contagem necessária de `WCHAR`s, incluindo o caractere nulo de terminação e `GetMetaData` é chamado uma segunda vez com o tamanho do buffer solicitado.</span><span class="sxs-lookup"><span data-stu-id="2f349-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f349-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2f349-128">Remarks</span></span>  
 <span data-ttu-id="2f349-129">Se `wszImagePath` contiver um caminho completo para um módulo de um despejo, ele especificará o caminho do computador em que o despejo foi coletado.</span><span class="sxs-lookup"><span data-stu-id="2f349-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="2f349-130">O arquivo pode não existir neste local ou um arquivo incorreto com o mesmo nome pode ser armazenado no caminho.</span><span class="sxs-lookup"><span data-stu-id="2f349-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f349-131">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2f349-131">Requirements</span></span>  
 <span data-ttu-id="2f349-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f349-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f349-133">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f349-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f349-134">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f349-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f349-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f349-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f349-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="2f349-136">See also</span></span>

- [<span data-ttu-id="2f349-137">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="2f349-137">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="2f349-138">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2f349-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2f349-139">Depuração</span><span class="sxs-lookup"><span data-stu-id="2f349-139">Debugging</span></span>](index.md)
