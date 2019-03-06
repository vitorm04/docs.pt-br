---
title: Função StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364505"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="40bdc-102">Função StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="40bdc-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="40bdc-103">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="40bdc-103">Deletes the specified key container.</span></span>

<span data-ttu-id="40bdc-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="40bdc-104">This function has been deprecated.</span></span> <span data-ttu-id="40bdc-105">Use o [iclrstrongname:: Strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="40bdc-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="40bdc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40bdc-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="40bdc-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40bdc-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="40bdc-108">[in] O nome de excluir o contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="40bdc-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="40bdc-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="40bdc-109">Return Value</span></span>

<span data-ttu-id="40bdc-110">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="40bdc-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="40bdc-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="40bdc-111">Remarks</span></span>

<span data-ttu-id="40bdc-112">Use o [StrongNameKeyInstall](strongnamekeyinstall-function.md) função para importar um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="40bdc-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="40bdc-113">Se o `StrongNameKeyDelete` função não for concluída com êxito, chame o [StrongNameErrorInfo](strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="40bdc-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="40bdc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40bdc-114">Requirements</span></span>

<span data-ttu-id="40bdc-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40bdc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="40bdc-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="40bdc-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="40bdc-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="40bdc-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="40bdc-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40bdc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="40bdc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40bdc-119">See also</span></span>

- [<span data-ttu-id="40bdc-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="40bdc-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="40bdc-121">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="40bdc-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="40bdc-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="40bdc-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)