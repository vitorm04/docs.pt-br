---
title: "Função StrongNameGetBlob"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1948a0d8a8536ebe9b0531eecaf3df446252b0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="7ca5b-102">Função StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="7ca5b-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="7ca5b-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="7ca5b-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-104">This function has been deprecated.</span></span> <span data-ttu-id="7ca5b-105">Use o [Strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca5b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ca5b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ca5b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ca5b-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7ca5b-108">[in] Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="7ca5b-109">[in] O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="7ca5b-110">[out no] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="7ca5b-111">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ca5b-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7ca5b-112">Return Value</span></span>  
 <span data-ttu-id="7ca5b-113">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ca5b-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ca5b-114">Remarks</span></span>  
 <span data-ttu-id="7ca5b-115">Se o `StrongNameGetBlob` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="7ca5b-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca5b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ca5b-116">Requirements</span></span>  
 <span data-ttu-id="7ca5b-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca5b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca5b-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="7ca5b-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7ca5b-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7ca5b-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ca5b-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca5b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca5b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ca5b-121">See Also</span></span>  
 [<span data-ttu-id="7ca5b-122">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="7ca5b-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="7ca5b-123">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="7ca5b-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="7ca5b-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7ca5b-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
