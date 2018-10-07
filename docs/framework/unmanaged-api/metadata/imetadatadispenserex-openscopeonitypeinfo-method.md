---
title: Método IMetaDataDispenserEx::OpenScopeOnITypeInfo
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5fd96f390b0bba60d1b95d20273bbf670208d41
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836649"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="fcdb2-102">Método IMetaDataDispenserEx::OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="fcdb2-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="fcdb2-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="fcdb2-103">This method is not implemented.</span></span> <span data-ttu-id="fcdb2-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="fcdb2-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcdb2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcdb2-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcdb2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fcdb2-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="fcdb2-107">[in] Ponteiro para um [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface que fornece as informações de tipo no qual abrir o escopo.</span><span class="sxs-lookup"><span data-stu-id="fcdb2-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="fcdb2-108">[in] Os sinalizadores de modo de abertura.</span><span class="sxs-lookup"><span data-stu-id="fcdb2-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="fcdb2-109">[in] A interface desejada.</span><span class="sxs-lookup"><span data-stu-id="fcdb2-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="fcdb2-110">[out] Ponteiro para um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="fcdb2-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcdb2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcdb2-111">Requirements</span></span>  
 <span data-ttu-id="fcdb2-112">**Plataforma:** ver [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcdb2-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcdb2-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fcdb2-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcdb2-114">**Biblioteca:** usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fcdb2-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcdb2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcdb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdb2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcdb2-116">See Also</span></span>  
 [<span data-ttu-id="fcdb2-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="fcdb2-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="fcdb2-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="fcdb2-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
