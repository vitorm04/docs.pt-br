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
ms.openlocfilehash: 91ef9eaa855ed841bc75bfaeead462f045eb1d8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007449"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="3dbe8-102">Método IMetaDataDispenserEx::OpenScopeOnITypeInfo</span><span class="sxs-lookup"><span data-stu-id="3dbe8-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="3dbe8-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="3dbe8-103">This method is not implemented.</span></span> <span data-ttu-id="3dbe8-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3dbe8-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dbe8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dbe8-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dbe8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3dbe8-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="3dbe8-107">no Ponteiro para uma interface [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) que fornece as informações de tipo nas quais abrir o escopo.</span><span class="sxs-lookup"><span data-stu-id="3dbe8-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3dbe8-108">no Os sinalizadores de modo aberto.</span><span class="sxs-lookup"><span data-stu-id="3dbe8-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="3dbe8-109">no A interface desejada.</span><span class="sxs-lookup"><span data-stu-id="3dbe8-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="3dbe8-110">fora Ponteiro para um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="3dbe8-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dbe8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dbe8-111">Requirements</span></span>  
 <span data-ttu-id="3dbe8-112">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dbe8-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dbe8-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3dbe8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3dbe8-114">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3dbe8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3dbe8-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dbe8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dbe8-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="3dbe8-116">See also</span></span>

- [<span data-ttu-id="3dbe8-117">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="3dbe8-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="3dbe8-118">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="3dbe8-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
