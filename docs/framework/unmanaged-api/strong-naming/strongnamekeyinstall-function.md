---
title: Função StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 9e441d4da64e9704fbda2368d2b07289aaea610a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125204"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="d2214-102">Função StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="d2214-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="d2214-103">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="d2214-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="d2214-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="d2214-104">This function has been deprecated.</span></span> <span data-ttu-id="d2214-105">Em vez disso, use o método [ICLRStrongName:: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d2214-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2214-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2214-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="d2214-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2214-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="d2214-108">no O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="d2214-108">[in] The name of the key container.</span></span> <span data-ttu-id="d2214-109">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="d2214-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="d2214-110">no O par de chaves binárias.</span><span class="sxs-lookup"><span data-stu-id="d2214-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="d2214-111">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="d2214-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2214-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d2214-112">Return Value</span></span>

<span data-ttu-id="d2214-113">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="d2214-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2214-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2214-114">Remarks</span></span>

<span data-ttu-id="d2214-115">Use a função [StrongNameKeyDelete](strongnamekeydelete-function.md) para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="d2214-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="d2214-116">Se a função `StrongNameKeyInstall` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="d2214-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2214-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2214-117">Requirements</span></span>

<span data-ttu-id="d2214-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2214-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d2214-119">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="d2214-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="d2214-120">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2214-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="d2214-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2214-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d2214-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2214-122">See also</span></span>

- [<span data-ttu-id="d2214-123">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="d2214-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="d2214-124">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="d2214-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="d2214-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d2214-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
