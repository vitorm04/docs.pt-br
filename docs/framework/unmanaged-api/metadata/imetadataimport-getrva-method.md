---
title: Método IMetaDataImport::GetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96c013cd3e45e4ede0cbc9f42bf511a2eb3fc12d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777541"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="edbdf-102">Método IMetaDataImport::GetRVA</span><span class="sxs-lookup"><span data-stu-id="edbdf-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="edbdf-103">Obtém o endereço virtual relativo (RVA) e os sinalizadores de implementação do método ou campo representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="edbdf-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edbdf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edbdf-104">Syntax</span></span>  
  
```  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edbdf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edbdf-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="edbdf-106">[in] Um token de metadados MethodDef ou FieldDef que representa o objeto de código para retornar o RVA para.</span><span class="sxs-lookup"><span data-stu-id="edbdf-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="edbdf-107">Se o token for uma FieldDef, o campo deve ser uma variável global.</span><span class="sxs-lookup"><span data-stu-id="edbdf-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="edbdf-108">[out] Um ponteiro para o endereço virtual relativo do código objeto representado pelo token.</span><span class="sxs-lookup"><span data-stu-id="edbdf-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="edbdf-109">[out] Um ponteiro para os sinalizadores de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="edbdf-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="edbdf-110">Esse valor é um bitmask do [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="edbdf-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="edbdf-111">O valor de `pdwImplFlags` é válido somente se `tk` é um token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="edbdf-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edbdf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edbdf-112">Requirements</span></span>  
 <span data-ttu-id="edbdf-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edbdf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edbdf-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="edbdf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edbdf-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="edbdf-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edbdf-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edbdf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbdf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edbdf-117">See also</span></span>

- [<span data-ttu-id="edbdf-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="edbdf-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="edbdf-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="edbdf-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
