---
title: "Método IMetaDataImport::FindTypeDefByName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeDefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b3a5f9ff15e2b94e6d5c5e885605d8eabae711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="2e95c-102">Método IMetaDataImport::FindTypeDefByName</span><span class="sxs-lookup"><span data-stu-id="2e95c-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="2e95c-103">Obtém um ponteiro para os metadados de TypeDef token para o <xref:System.Type> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2e95c-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e95c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e95c-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e95c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e95c-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="2e95c-106">[in] O nome do tipo para o qual obter o token de TypeDef.</span><span class="sxs-lookup"><span data-stu-id="2e95c-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="2e95c-107">[in] Um token de TypeDef ou TypeRef que representa a classe de delimitador.</span><span class="sxs-lookup"><span data-stu-id="2e95c-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="2e95c-108">Se o tipo de localização não é uma classe aninhada, defina esse valor como NULL.</span><span class="sxs-lookup"><span data-stu-id="2e95c-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="2e95c-109">[out] Um ponteiro para o token de TypeDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="2e95c-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e95c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e95c-110">Requirements</span></span>  
 <span data-ttu-id="2e95c-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e95c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e95c-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e95c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e95c-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2e95c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e95c-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e95c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e95c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e95c-115">See Also</span></span>  
 [<span data-ttu-id="2e95c-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2e95c-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2e95c-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2e95c-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
