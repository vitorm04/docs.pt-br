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
ms.openlocfilehash: 5485f43afe08fafa559d0418327a8f4f186860e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491505"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="ce806-102">Método IMetaDataImport::FindTypeDefByName</span><span class="sxs-lookup"><span data-stu-id="ce806-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="ce806-103">Obtém um ponteiro para o token de metadados de TypeDef para o <xref:System.Type> com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ce806-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce806-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce806-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce806-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce806-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="ce806-106">no O nome do tipo para o qual obter o token de TypeDef.</span><span class="sxs-lookup"><span data-stu-id="ce806-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="ce806-107">no Um token TypeDef ou TypeRef que representa a classe delimitadora.</span><span class="sxs-lookup"><span data-stu-id="ce806-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="ce806-108">Se o tipo a ser localizado não for uma classe aninhada, defina esse valor como NULL.</span><span class="sxs-lookup"><span data-stu-id="ce806-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="ce806-109">fora Um ponteiro para o token de TypeDef correspondente.</span><span class="sxs-lookup"><span data-stu-id="ce806-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce806-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce806-110">Requirements</span></span>  
 <span data-ttu-id="ce806-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce806-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce806-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ce806-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce806-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce806-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce806-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce806-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce806-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce806-115">See also</span></span>

- [<span data-ttu-id="ce806-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ce806-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ce806-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ce806-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
