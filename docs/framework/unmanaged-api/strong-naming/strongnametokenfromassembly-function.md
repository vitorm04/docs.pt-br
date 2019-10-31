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
ms.openlocfilehash: 6b9eca3f2f0267870866874ea27dc65812795f41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121126"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="07cf7-102">Função StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="07cf7-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="07cf7-103">Cria um token de nome forte do arquivo do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="07cf7-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="07cf7-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="07cf7-104">This function has been deprecated.</span></span> <span data-ttu-id="07cf7-105">Em vez disso, use o método [ICLRStrongName:: StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="07cf7-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cf7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07cf7-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07cf7-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07cf7-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="07cf7-108">no O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="07cf7-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="07cf7-109">fora O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="07cf7-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="07cf7-110">fora O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="07cf7-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07cf7-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="07cf7-111">Return Value</span></span>  
 <span data-ttu-id="07cf7-112">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="07cf7-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cf7-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="07cf7-113">Remarks</span></span>  
 <span data-ttu-id="07cf7-114">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="07cf7-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="07cf7-115">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="07cf7-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="07cf7-116">O token é uma parte do nome forte para o assembly e pode ser lido nos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="07cf7-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="07cf7-117">Depois que o token é criado, você deve chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="07cf7-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="07cf7-118">Se a função `StrongNameTokenFromAssembly` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="07cf7-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07cf7-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07cf7-119">Requirements</span></span>  
 <span data-ttu-id="07cf7-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07cf7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07cf7-121">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="07cf7-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="07cf7-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="07cf7-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="07cf7-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07cf7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cf7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07cf7-124">See also</span></span>

- [<span data-ttu-id="07cf7-125">Método StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="07cf7-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="07cf7-126">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="07cf7-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="07cf7-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="07cf7-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
