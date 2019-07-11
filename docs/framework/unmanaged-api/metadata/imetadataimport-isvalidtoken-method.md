---
title: Método IMetaDataImport::IsValidToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 753449924f3415eb826b59d3a887eb69b9efba39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778788"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="02c22-102">Método IMetaDataImport::IsValidToken</span><span class="sxs-lookup"><span data-stu-id="02c22-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="02c22-103">Obtém um valor que indica se o token especificado mantém uma referência válida para um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="02c22-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02c22-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02c22-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02c22-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="02c22-106">[in] O token para verificar a validade de referência para.</span><span class="sxs-lookup"><span data-stu-id="02c22-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02c22-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="02c22-107">Return Value</span></span>  
 <span data-ttu-id="02c22-108">`true` Se `tk` é um token de metadados válido dentro do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="02c22-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="02c22-109">Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="02c22-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02c22-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02c22-110">Requirements</span></span>  
 <span data-ttu-id="02c22-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02c22-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02c22-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02c22-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02c22-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="02c22-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02c22-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02c22-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c22-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02c22-115">See also</span></span>

- [<span data-ttu-id="02c22-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="02c22-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="02c22-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="02c22-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
