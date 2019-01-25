---
title: Função StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe15b855044a7bf45ea172f42436c3557b562037
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687057"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="72657-102">Função StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="72657-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="72657-103">Cria um token de nome forte do arquivo do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="72657-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="72657-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="72657-104">This function has been deprecated.</span></span> <span data-ttu-id="72657-105">Use o [iclrstrongname:: Strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="72657-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72657-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72657-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72657-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72657-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="72657-108">[in] O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="72657-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="72657-109">[out] O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="72657-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="72657-110">[out] O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="72657-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72657-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="72657-111">Return Value</span></span>  
 <span data-ttu-id="72657-112">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="72657-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72657-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="72657-113">Remarks</span></span>  
 <span data-ttu-id="72657-114">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="72657-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="72657-115">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="72657-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="72657-116">O token é uma parte do nome forte para o assembly e os metadados do assembly pode ser lido.</span><span class="sxs-lookup"><span data-stu-id="72657-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="72657-117">Depois que o token é criado, você deve chamar o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="72657-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="72657-118">Se o `StrongNameTokenFromAssembly` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="72657-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72657-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72657-119">Requirements</span></span>  
 <span data-ttu-id="72657-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72657-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72657-121">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="72657-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="72657-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="72657-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="72657-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72657-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72657-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72657-124">See also</span></span>
- [<span data-ttu-id="72657-125">Método StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="72657-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="72657-126">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="72657-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="72657-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="72657-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
