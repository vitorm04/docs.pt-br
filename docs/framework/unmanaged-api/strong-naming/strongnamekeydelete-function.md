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
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141592"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="66f35-102">Função StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="66f35-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="66f35-103">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="66f35-103">Deletes the specified key container.</span></span>

<span data-ttu-id="66f35-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="66f35-104">This function has been deprecated.</span></span> <span data-ttu-id="66f35-105">Em vez disso, use o método [ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="66f35-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="66f35-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66f35-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="66f35-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66f35-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="66f35-108">no O nome do contêiner de chave a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="66f35-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="66f35-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="66f35-109">Return Value</span></span>

<span data-ttu-id="66f35-110">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="66f35-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="66f35-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="66f35-111">Remarks</span></span>

<span data-ttu-id="66f35-112">Use a função [StrongNameKeyInstall](strongnamekeyinstall-function.md) para importar um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="66f35-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="66f35-113">Se a função `StrongNameKeyDelete` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="66f35-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="66f35-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66f35-114">Requirements</span></span>

<span data-ttu-id="66f35-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66f35-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="66f35-116">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="66f35-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="66f35-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66f35-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="66f35-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66f35-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="66f35-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66f35-119">See also</span></span>

- [<span data-ttu-id="66f35-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="66f35-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="66f35-121">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="66f35-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="66f35-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="66f35-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
