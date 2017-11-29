---
title: "Método IMetaDataImport::IsValidToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsValidToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c916e71518ded93c90b270205dd975201762846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="065af-102">Método IMetaDataImport::IsValidToken</span><span class="sxs-lookup"><span data-stu-id="065af-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="065af-103">Obtém um valor que indica se o token especificado contém uma referência válida para um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="065af-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="065af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="065af-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="065af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="065af-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="065af-106">[in] O token para verificar a validade de referência para.</span><span class="sxs-lookup"><span data-stu-id="065af-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="065af-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="065af-107">Return Value</span></span>  
 <span data-ttu-id="065af-108">`true`Se `tk` é um token de metadados válido dentro do escopo atual.</span><span class="sxs-lookup"><span data-stu-id="065af-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="065af-109">Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="065af-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="065af-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="065af-110">Requirements</span></span>  
 <span data-ttu-id="065af-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="065af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="065af-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="065af-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="065af-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="065af-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="065af-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="065af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065af-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="065af-115">See Also</span></span>  
 [<span data-ttu-id="065af-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="065af-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="065af-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="065af-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
