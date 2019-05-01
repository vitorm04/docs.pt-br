---
title: Função StrongNameHashSize
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e807b502e0905f9ae785203289447c71d25e04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041009"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="0949c-102">Função StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="0949c-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="0949c-103">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="0949c-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="0949c-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="0949c-104">This function has been deprecated.</span></span> <span data-ttu-id="0949c-105">Use o [iclrstrongname:: Strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0949c-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0949c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0949c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0949c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0949c-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="0949c-108">[in] O algoritmo de hash usado para calcular o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="0949c-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="0949c-109">[out] O tamanho do buffer retornado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="0949c-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0949c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0949c-110">Return Value</span></span>  
 <span data-ttu-id="0949c-111">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0949c-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0949c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="0949c-112">Remarks</span></span>  
 <span data-ttu-id="0949c-113">Se o `StrongNameHashSize` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="0949c-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0949c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0949c-114">Requirements</span></span>  
 <span data-ttu-id="0949c-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0949c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0949c-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0949c-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0949c-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0949c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0949c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0949c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0949c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0949c-119">See also</span></span>

- [<span data-ttu-id="0949c-120">Método StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="0949c-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="0949c-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0949c-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
