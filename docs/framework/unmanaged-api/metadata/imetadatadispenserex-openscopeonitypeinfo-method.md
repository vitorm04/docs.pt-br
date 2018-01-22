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
ms.openlocfilehash: 45c65d0194ed44122a87dcd000359187fc020d0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="2d06b-102">Método IMetaDataDispenserEx::OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="2d06b-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="2d06b-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="2d06b-103">This method is not implemented.</span></span> <span data-ttu-id="2d06b-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2d06b-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d06b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d06b-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d06b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d06b-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="2d06b-107">[in] Ponteiro para um [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680) interface que fornece as informações de tipo no qual abrir o escopo.</span><span class="sxs-lookup"><span data-stu-id="2d06b-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="2d06b-108">[in] Os sinalizadores de modo de abertura.</span><span class="sxs-lookup"><span data-stu-id="2d06b-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="2d06b-109">[in] A interface desejada.</span><span class="sxs-lookup"><span data-stu-id="2d06b-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="2d06b-110">[out] Ponteiro para um ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="2d06b-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d06b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d06b-111">Requirements</span></span>  
 <span data-ttu-id="2d06b-112">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d06b-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d06b-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2d06b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d06b-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2d06b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d06b-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d06b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d06b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d06b-116">See Also</span></span>  
 [<span data-ttu-id="2d06b-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="2d06b-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="2d06b-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="2d06b-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
