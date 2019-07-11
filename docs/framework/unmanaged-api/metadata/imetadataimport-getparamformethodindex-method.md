---
title: Método IMetaDataImport::GetParamForMethodIndex
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdb3def9574f4442a22b370323dfdf044170542b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778937"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="8713a-102">Método IMetaDataImport::GetParamForMethodIndex</span><span class="sxs-lookup"><span data-stu-id="8713a-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="8713a-103">Obtém o token que representa um parâmetro especificado do método representado pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="8713a-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8713a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8713a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8713a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8713a-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="8713a-106">[in] Um token que representa o método para retornar o token de parâmetro para.</span><span class="sxs-lookup"><span data-stu-id="8713a-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="8713a-107">[in] A posição ordinal na lista de parâmetros em que ocorre o parâmetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="8713a-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="8713a-108">Parâmetros são numerados a partir de um, com o valor de retorno do método na posição zero.</span><span class="sxs-lookup"><span data-stu-id="8713a-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="8713a-109">[out] Um ponteiro para um token de ParamDef que representa o parâmetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="8713a-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8713a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8713a-110">Requirements</span></span>  
 <span data-ttu-id="8713a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8713a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8713a-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8713a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8713a-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8713a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8713a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8713a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8713a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8713a-115">See also</span></span>

- [<span data-ttu-id="8713a-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="8713a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8713a-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="8713a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
