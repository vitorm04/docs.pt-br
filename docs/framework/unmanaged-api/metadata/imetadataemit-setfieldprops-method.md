---
title: "Método IMetaDataEmit::SetFieldProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f031e79deab57184043eaa44d2d8a3d369187c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="844ae-102">Método IMetaDataEmit::SetFieldProps</span><span class="sxs-lookup"><span data-stu-id="844ae-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="844ae-103">Define ou atualiza o valor padrão para o campo referenciado pelo token de campo especificado.</span><span class="sxs-lookup"><span data-stu-id="844ae-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="844ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="844ae-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="844ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="844ae-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="844ae-106">[in] O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="844ae-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="844ae-107">[in] Atributos de campo.</span><span class="sxs-lookup"><span data-stu-id="844ae-107">[in] Field attributes.</span></span> <span data-ttu-id="844ae-108">Esse é um bitmask de `CorFieldAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="844ae-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="844ae-109">[in] O `ELEMENT_TYPE_`  *\**  para o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="844ae-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="844ae-110">Este é um `CorElementType` valor.</span><span class="sxs-lookup"><span data-stu-id="844ae-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="844ae-111">Se uma constante não é definida, defina esse valor como `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="844ae-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="844ae-112">[in] O valor da constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="844ae-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="844ae-113">[in] O tamanho, em caracteres Unicode, de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="844ae-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="844ae-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="844ae-114">Requirements</span></span>  
 <span data-ttu-id="844ae-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="844ae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="844ae-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="844ae-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="844ae-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="844ae-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="844ae-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="844ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844ae-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="844ae-119">See Also</span></span>  
 [<span data-ttu-id="844ae-120">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="844ae-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="844ae-121">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="844ae-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
