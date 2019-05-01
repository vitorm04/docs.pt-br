---
title: Função StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e23232b55a841672ee193b980c310995ba688e00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049356"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="652da-102">Função StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="652da-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="652da-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="652da-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="652da-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="652da-104">This function has been deprecated.</span></span> <span data-ttu-id="652da-105">Use o [iclrstrongname:: Strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="652da-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="652da-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="652da-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="652da-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="652da-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="652da-108">[in] Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="652da-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="652da-109">[in] O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="652da-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="652da-110">[no, out] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="652da-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="652da-111">Após o retorno, o tamanho real, em bytes, do `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="652da-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="652da-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="652da-112">Return Value</span></span>  
 <span data-ttu-id="652da-113">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="652da-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="652da-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="652da-114">Remarks</span></span>  
 <span data-ttu-id="652da-115">Se o `StrongNameGetBlob` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="652da-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="652da-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="652da-116">Requirements</span></span>  
 <span data-ttu-id="652da-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="652da-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="652da-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="652da-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="652da-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="652da-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="652da-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="652da-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="652da-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="652da-121">See also</span></span>

- [<span data-ttu-id="652da-122">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="652da-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="652da-123">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="652da-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="652da-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="652da-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
