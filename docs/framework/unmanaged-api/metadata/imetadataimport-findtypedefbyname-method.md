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
ms.openlocfilehash: 2b4aad1cf1d3eb2dec249686f2897e6f393ab7e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445472"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="59247-102">Método IMetaDataImport::FindTypeDefByName</span><span class="sxs-lookup"><span data-stu-id="59247-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="59247-103">Obtém um ponteiro para os metadados de TypeDef token para o <xref:System.Type> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="59247-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59247-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59247-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59247-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59247-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="59247-106">[in] O nome do tipo para o qual obter o token de TypeDef.</span><span class="sxs-lookup"><span data-stu-id="59247-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="59247-107">[in] Um token de TypeDef ou TypeRef que representa a classe de delimitador.</span><span class="sxs-lookup"><span data-stu-id="59247-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="59247-108">Se o tipo de localização não é uma classe aninhada, defina esse valor como NULL.</span><span class="sxs-lookup"><span data-stu-id="59247-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="59247-109">[out] Um ponteiro para o token de TypeDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="59247-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59247-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59247-110">Requirements</span></span>  
 <span data-ttu-id="59247-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59247-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59247-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="59247-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59247-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="59247-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59247-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59247-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59247-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59247-115">See Also</span></span>  
 [<span data-ttu-id="59247-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="59247-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="59247-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="59247-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
