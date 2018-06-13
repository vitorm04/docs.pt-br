---
title: Função StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d562aef58c1e3b5bbbe690b54eb08384052c657
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456769"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="8505e-102">Função StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="8505e-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="8505e-103">Obtém uma representação binária da imagem do assembly no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8505e-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="8505e-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="8505e-104">This function has been deprecated.</span></span> <span data-ttu-id="8505e-105">Use o [Strongnamegetblobfromimage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8505e-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8505e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8505e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8505e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8505e-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="8505e-108">[in] O endereço de memória do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="8505e-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8505e-109">[in] O tamanho, em bytes, da imagem no `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="8505e-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="8505e-110">[in] Um buffer para conter a representação binária da imagem.</span><span class="sxs-lookup"><span data-stu-id="8505e-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="8505e-111">[out no] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="8505e-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="8505e-112">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="8505e-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8505e-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8505e-113">Return Value</span></span>  
 <span data-ttu-id="8505e-114">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="8505e-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8505e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8505e-115">Remarks</span></span>  
 <span data-ttu-id="8505e-116">Se o `StrongNameGetBlobFromImage` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="8505e-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8505e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8505e-117">Requirements</span></span>  
 <span data-ttu-id="8505e-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8505e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8505e-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="8505e-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8505e-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8505e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8505e-121">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8505e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8505e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8505e-122">See Also</span></span>  
 [<span data-ttu-id="8505e-123">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="8505e-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="8505e-124">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="8505e-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="8505e-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8505e-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
