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
ms.openlocfilehash: d752d6dbe8a6b7a23faae498f9118c8d89e92929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447691"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="1cb37-102">Método IMetaDataImport::IsValidToken</span><span class="sxs-lookup"><span data-stu-id="1cb37-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="1cb37-103">Obtém um valor que indica se o token especificado contém uma referência válida para um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="1cb37-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cb37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cb37-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cb37-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cb37-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1cb37-106">[in] O token para verificar a validade de referência para.</span><span class="sxs-lookup"><span data-stu-id="1cb37-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cb37-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1cb37-107">Return Value</span></span>  
 <span data-ttu-id="1cb37-108">`true` Se `tk` é um token de metadados válido dentro do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="1cb37-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="1cb37-109">Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="1cb37-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cb37-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cb37-110">Requirements</span></span>  
 <span data-ttu-id="1cb37-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cb37-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cb37-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1cb37-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cb37-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1cb37-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1cb37-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cb37-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb37-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cb37-115">See Also</span></span>  
 [<span data-ttu-id="1cb37-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1cb37-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1cb37-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1cb37-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
