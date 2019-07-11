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
ms.openlocfilehash: b076c39ccf40ca5b613cab94ecc75716158d97a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780123"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="2cd2d-102">Função StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="2cd2d-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="2cd2d-103">Obtém uma representação binária da imagem do assembly no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="2cd2d-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-104">This function has been deprecated.</span></span> <span data-ttu-id="2cd2d-105">Use o [iclrstrongname:: Strongnamegetblobfromimage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd2d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cd2d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cd2d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cd2d-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="2cd2d-108">[in] O endereço de memória do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2cd2d-109">[in] O tamanho, em bytes, da imagem no `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="2cd2d-110">[in] Um buffer que conterá a representação binária da imagem.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="2cd2d-111">[no, out] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="2cd2d-112">Após o retorno, o tamanho real, em bytes, do `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cd2d-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2cd2d-113">Return Value</span></span>  
 <span data-ttu-id="2cd2d-114">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cd2d-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cd2d-115">Remarks</span></span>  
 <span data-ttu-id="2cd2d-116">Se o `StrongNameGetBlobFromImage` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="2cd2d-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd2d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cd2d-117">Requirements</span></span>  
 <span data-ttu-id="2cd2d-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd2d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd2d-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2cd2d-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2cd2d-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2cd2d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cd2d-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd2d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd2d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cd2d-122">See also</span></span>

- [<span data-ttu-id="2cd2d-123">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="2cd2d-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="2cd2d-124">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="2cd2d-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="2cd2d-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2cd2d-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
