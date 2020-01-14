---
title: Método StrongNameSignatureVerificationEx2
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
ms.openlocfilehash: 81640e8e34335898f4dd7f4f43eafbd3ef191d19
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938163"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="43320-102">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="43320-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="43320-103">Verifica a assinatura de um assembly com nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="43320-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43320-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43320-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43320-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43320-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="43320-106">no O caminho para o arquivo executável portátil (. exe ou. dll) para o assembly a ser verificado.</span><span class="sxs-lookup"><span data-stu-id="43320-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="43320-107">[in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="43320-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="43320-108">no Um ponteiro para o mapeamento da chave pública ECMA para a chave real usada para verificação.</span><span class="sxs-lookup"><span data-stu-id="43320-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="43320-109">no O comprimento da chave pública ECMA real.</span><span class="sxs-lookup"><span data-stu-id="43320-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="43320-110">[fora] `true` se a assinatura de nome forte foi verificada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="43320-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="43320-111">Esse parâmetro também é definido como `false` se a verificação foi bem-sucedida devido a configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="43320-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43320-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43320-112">Return Value</span></span>  
 <span data-ttu-id="43320-113">`S_OK` se a verificação foi bem-sucedida; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="43320-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43320-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="43320-114">Requirements</span></span>  
 <span data-ttu-id="43320-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43320-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43320-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="43320-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="43320-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="43320-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43320-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43320-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43320-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="43320-119">See also</span></span>

- [<span data-ttu-id="43320-120">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="43320-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="43320-121">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="43320-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="43320-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="43320-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
