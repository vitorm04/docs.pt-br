---
title: Método ICLRStrongName::StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: f08006c532d2778de67a4bab09623d248362535c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937435"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="7e3b3-102">Método ICLRStrongName::StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="7e3b3-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="7e3b3-103">Cria um token de nome forte a partir do arquivo de assembly especificado e retorna a chave pública que o token representa.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e3b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e3b3-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e3b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e3b3-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7e3b3-106">no O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="7e3b3-107">fora O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="7e3b3-108">fora O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="7e3b3-109">fora A chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="7e3b3-110">fora O tamanho, em bytes, da chave pública.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e3b3-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7e3b3-111">Return Value</span></span>  
 <span data-ttu-id="7e3b3-112">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="7e3b3-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e3b3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e3b3-113">Remarks</span></span>  
 <span data-ttu-id="7e3b3-114">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="7e3b3-115">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="7e3b3-116">O token é uma parte do nome forte para o assembly e pode ser lido nos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="7e3b3-117">Depois que a chave é recuperada e o token é criado, você deve chamar o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="7e3b3-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e3b3-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7e3b3-118">Requirements</span></span>  
 <span data-ttu-id="7e3b3-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e3b3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e3b3-120">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7e3b3-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7e3b3-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7e3b3-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e3b3-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e3b3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3b3-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="7e3b3-123">See also</span></span>

- [<span data-ttu-id="7e3b3-124">Método StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="7e3b3-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="7e3b3-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7e3b3-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
