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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3fc69b2edf611383402b13555cf33be10dbad3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000383"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="47113-102">Função StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="47113-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="47113-103">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="47113-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="47113-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="47113-104">This function has been deprecated.</span></span> <span data-ttu-id="47113-105">Use o [iclrstrongname:: Strongnamekeyinstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="47113-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="47113-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47113-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="47113-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47113-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="47113-108">[in] O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="47113-108">[in] The name of the key container.</span></span> <span data-ttu-id="47113-109">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="47113-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="47113-110">[in] O par de chaves binário.</span><span class="sxs-lookup"><span data-stu-id="47113-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="47113-111">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="47113-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="47113-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47113-112">Return Value</span></span>

<span data-ttu-id="47113-113">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="47113-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="47113-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="47113-114">Remarks</span></span>

<span data-ttu-id="47113-115">Use o [StrongNameKeyDelete](strongnamekeydelete-function.md) função para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="47113-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="47113-116">Se o `StrongNameKeyInstall` função não for concluída com êxito, chame o [StrongNameErrorInfo](strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="47113-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="47113-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47113-117">Requirements</span></span>

<span data-ttu-id="47113-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47113-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="47113-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="47113-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="47113-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="47113-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="47113-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47113-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="47113-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47113-122">See also</span></span>

- [<span data-ttu-id="47113-123">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="47113-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="47113-124">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="47113-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="47113-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="47113-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)