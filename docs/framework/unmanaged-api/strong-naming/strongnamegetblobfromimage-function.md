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
ms.openlocfilehash: 41226cd909900bd2da7bdcf9b9a49567d3042b01
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094889"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="95670-102">Função StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="95670-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="95670-103">Obtém uma representação binária da imagem do assembly no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="95670-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="95670-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="95670-104">This function has been deprecated.</span></span> <span data-ttu-id="95670-105">Em vez disso, use o método [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="95670-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95670-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95670-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95670-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95670-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="95670-108">no O endereço de memória do manifesto do assembly mapeado.</span><span class="sxs-lookup"><span data-stu-id="95670-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="95670-109">no O tamanho, em bytes, da imagem em `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="95670-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="95670-110">no Um buffer para conter a representação binária da imagem.</span><span class="sxs-lookup"><span data-stu-id="95670-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="95670-111">[entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="95670-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="95670-112">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="95670-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95670-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="95670-113">Return Value</span></span>  
 <span data-ttu-id="95670-114">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="95670-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95670-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="95670-115">Remarks</span></span>  
 <span data-ttu-id="95670-116">Se a função `StrongNameGetBlobFromImage` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="95670-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95670-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95670-117">Requirements</span></span>  
 <span data-ttu-id="95670-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95670-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95670-119">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="95670-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="95670-120">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95670-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95670-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95670-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95670-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95670-122">See also</span></span>

- [<span data-ttu-id="95670-123">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="95670-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="95670-124">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="95670-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="95670-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="95670-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
