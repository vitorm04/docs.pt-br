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
ms.openlocfilehash: 190bcacc84646cfd9294cf2b6b53b0474f38758f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177210"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="9fad2-102">Método IMetaDataImport::GetRVA</span><span class="sxs-lookup"><span data-stu-id="9fad2-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="9fad2-103">Obtém o endereço virtual relativo (RVA) e os sinalizadores de implementação do método ou campo representados pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="9fad2-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fad2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fad2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fad2-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fad2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9fad2-106">[em] Um token de metadados MethodDef ou FieldDef que representa o objeto de código para retornar o RVA.</span><span class="sxs-lookup"><span data-stu-id="9fad2-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="9fad2-107">Se o token é um FieldDef, o campo deve ser uma variável global.</span><span class="sxs-lookup"><span data-stu-id="9fad2-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="9fad2-108">[fora] Um ponteiro para o endereço virtual relativo do objeto de código representado pelo token.</span><span class="sxs-lookup"><span data-stu-id="9fad2-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="9fad2-109">[fora] Um ponteiro para as bandeiras de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="9fad2-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="9fad2-110">Este valor é uma máscara de bitda da enumeração [CorMethodImpl.](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="9fad2-110">This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="9fad2-111">O valor `pdwImplFlags` do é `tk` válido apenas se for um token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="9fad2-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fad2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fad2-112">Requirements</span></span>  
 <span data-ttu-id="9fad2-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fad2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fad2-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fad2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fad2-115">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fad2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fad2-116">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fad2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fad2-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9fad2-117">See also</span></span>

- [<span data-ttu-id="9fad2-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9fad2-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9fad2-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9fad2-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
