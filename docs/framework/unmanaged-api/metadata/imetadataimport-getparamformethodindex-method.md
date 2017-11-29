---
title: "Método IMetaDataImport::GetParamForMethodIndex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamForMethodIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda4ffde7d38d74ddf7a81b6f0af4a556693094d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="2e695-102">Método IMetaDataImport::GetParamForMethodIndex</span><span class="sxs-lookup"><span data-stu-id="2e695-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="2e695-103">Obtém o token que representa um parâmetro especificado do método representado pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="2e695-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e695-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e695-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e695-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e695-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="2e695-106">[in] Um token que representa o método para retornar o token do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2e695-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="2e695-107">[in] A posição ordinal na lista de parâmetros onde ocorre o parâmetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="2e695-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="2e695-108">Parâmetros são numerados a partir de um, com o valor de retorno do método na posição zero.</span><span class="sxs-lookup"><span data-stu-id="2e695-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="2e695-109">[out] Um ponteiro para um token de ParamDef que representa o parâmetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="2e695-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e695-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e695-110">Requirements</span></span>  
 <span data-ttu-id="2e695-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e695-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e695-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e695-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e695-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2e695-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e695-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e695-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e695-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e695-115">See Also</span></span>  
 [<span data-ttu-id="2e695-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2e695-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2e695-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2e695-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
