---
title: Método IMetaDataImport::FindTypeDefByName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d2d7f9b459e5a46793d44728a9fea269ca47887
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492381"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="56bf3-102">Método IMetaDataImport::FindTypeDefByName</span><span class="sxs-lookup"><span data-stu-id="56bf3-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="56bf3-103">Obtém um ponteiro para os metadados de TypeDef token para o <xref:System.Type> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="56bf3-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56bf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56bf3-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56bf3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56bf3-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="56bf3-106">[in] O nome do tipo para o qual obter o token de TypeDef.</span><span class="sxs-lookup"><span data-stu-id="56bf3-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="56bf3-107">[in] Um token de TypeDef ou TypeRef que representa a classe delimitadora.</span><span class="sxs-lookup"><span data-stu-id="56bf3-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="56bf3-108">Se o tipo para localizar não é uma classe aninhada, defina esse valor como NULL.</span><span class="sxs-lookup"><span data-stu-id="56bf3-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="56bf3-109">[out] Um ponteiro para o token de TypeDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="56bf3-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56bf3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56bf3-110">Requirements</span></span>  
 <span data-ttu-id="56bf3-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56bf3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56bf3-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56bf3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56bf3-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="56bf3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56bf3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56bf3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bf3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56bf3-115">See also</span></span>
- [<span data-ttu-id="56bf3-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="56bf3-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="56bf3-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="56bf3-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
