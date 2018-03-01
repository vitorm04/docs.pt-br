---
title: "Método IMetaDataDispenserEx::GetOption"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1fd59fa20e95de8486eaa7f18a63333459361ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="5ffd2-102">Método IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="5ffd2-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="5ffd2-103">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="5ffd2-104">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffd2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ffd2-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ffd2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ffd2-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="5ffd2-107">[in] Um ponteiro para um GUID que especifica a opção a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="5ffd2-108">Consulte a seção de comentários para obter uma lista de GUIDs com suporte.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="5ffd2-109">[out] O valor da opção retornado.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-109">[out] The value of the returned option.</span></span> <span data-ttu-id="5ffd2-110">O tipo desse valor será uma variante do tipo da opção especificada.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ffd2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ffd2-111">Remarks</span></span>  
 <span data-ttu-id="5ffd2-112">A lista a seguir mostra os GUIDs que têm suporte para esse método.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="5ffd2-113">Para obter descrições, consulte o [Imetadatadispenserex](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="5ffd2-114">Se `optionId` é ausentes nesta lista, esse método retorna o HRESULT `E_INVALIDARG`, que indica um parâmetro incorreto.</span><span class="sxs-lookup"><span data-stu-id="5ffd2-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="5ffd2-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="5ffd2-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="5ffd2-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="5ffd2-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="5ffd2-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="5ffd2-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="5ffd2-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="5ffd2-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="5ffd2-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="5ffd2-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="5ffd2-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="5ffd2-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="5ffd2-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="5ffd2-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffd2-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ffd2-122">Requirements</span></span>  
 <span data-ttu-id="5ffd2-123">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ffd2-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffd2-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5ffd2-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ffd2-125">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5ffd2-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ffd2-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ffd2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffd2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ffd2-127">See Also</span></span>  
 [<span data-ttu-id="5ffd2-128">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="5ffd2-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="5ffd2-129">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="5ffd2-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
