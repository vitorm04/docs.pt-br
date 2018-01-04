---
title: "Método IMetaDataDispenserEx::OpenScopeOnITypeInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e13211a43c42d66fccd88473c8f881b9edd071d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="9fa2e-102">Método IMetaDataDispenserEx::OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="9fa2e-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="9fa2e-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-103">This method is not implemented.</span></span> <span data-ttu-id="9fa2e-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa2e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fa2e-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fa2e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fa2e-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="9fa2e-107">[in] Ponteiro para um [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interface que fornece as informações de tipo no qual abrir o escopo.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="9fa2e-108">[in] Os sinalizadores de modo de abertura.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="9fa2e-109">[in] A interface desejada.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="9fa2e-110">[out] Ponteiro para um ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="9fa2e-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa2e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fa2e-111">Requirements</span></span>  
 <span data-ttu-id="9fa2e-112">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa2e-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa2e-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fa2e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fa2e-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9fa2e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9fa2e-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa2e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa2e-116">See Also</span></span>  
 [<span data-ttu-id="9fa2e-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9fa2e-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="9fa2e-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="9fa2e-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
