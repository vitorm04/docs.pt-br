---
title: Função StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176884"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="591f0-102">Função StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="591f0-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="591f0-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="591f0-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="591f0-104">`StrongNameSignatureSize`é normalmente usado por compiladores para determinar quanto espaço reservar no arquivo ao criar um conjunto assinado por atraso.</span><span class="sxs-lookup"><span data-stu-id="591f0-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="591f0-105">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="591f0-105">This function has been deprecated.</span></span> <span data-ttu-id="591f0-106">Use o método [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="591f0-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="591f0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="591f0-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="591f0-108">parâmetros</span><span class="sxs-lookup"><span data-stu-id="591f0-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="591f0-109">[em] Uma estrutura do tipo [PublicKeyBlob](publickeyblob-structure.md) que contém a parte pública do par de chaves usada para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="591f0-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="591f0-110">[em] O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="591f0-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="591f0-111">[em] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="591f0-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="591f0-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="591f0-112">Return Value</span></span>  
 <span data-ttu-id="591f0-113">`true`em conclusão bem sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="591f0-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="591f0-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="591f0-114">Remarks</span></span>  
 <span data-ttu-id="591f0-115">Se `StrongNameSignatureSize` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="591f0-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="591f0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="591f0-116">Requirements</span></span>  
 <span data-ttu-id="591f0-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="591f0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="591f0-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="591f0-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="591f0-119">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="591f0-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="591f0-120">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="591f0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="591f0-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="591f0-121">See also</span></span>

- [<span data-ttu-id="591f0-122">Método StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="591f0-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="591f0-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="591f0-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
