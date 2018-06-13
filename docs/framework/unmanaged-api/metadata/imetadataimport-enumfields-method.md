---
title: Método IMetaDataImport::EnumFields
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd8a2d373b801bd8238d50eecb388ef511bc34bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446196"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="c3433-102">Método IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="c3433-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="c3433-103">Enumera FieldDef tokens para o tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="c3433-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3433-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3433-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3433-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3433-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c3433-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="c3433-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="c3433-107">[in] O token de TypeDef da classe cujos campos são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="c3433-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="c3433-108">[out] A lista de tokens de FieldDef.</span><span class="sxs-lookup"><span data-stu-id="c3433-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c3433-109">[in] O tamanho máximo da `rFields` matriz.</span><span class="sxs-lookup"><span data-stu-id="c3433-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c3433-110">[out] O número real de tokens FieldDef retornado em `rFields`.</span><span class="sxs-lookup"><span data-stu-id="c3433-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3433-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c3433-111">Return Value</span></span>  
  
|<span data-ttu-id="c3433-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3433-112">HRESULT</span></span>|<span data-ttu-id="c3433-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3433-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c3433-114">`EnumFields` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c3433-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c3433-115">Não há nenhum campo para enumerar.</span><span class="sxs-lookup"><span data-stu-id="c3433-115">There are no fields to enumerate.</span></span> <span data-ttu-id="c3433-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="c3433-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3433-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3433-117">Requirements</span></span>  
 <span data-ttu-id="c3433-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3433-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3433-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3433-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3433-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c3433-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3433-121">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3433-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3433-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3433-122">See Also</span></span>  
 [<span data-ttu-id="c3433-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c3433-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c3433-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c3433-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
