---
title: Método IMetaDataDispenserEx::GetOption
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8717a1eafebf24366c35848dbe285943c107ed51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777727"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="92a89-102">Método IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="92a89-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="92a89-103">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="92a89-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="92a89-104">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="92a89-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a89-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92a89-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92a89-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92a89-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="92a89-107">[in] Um ponteiro para um GUID que especifica a opção a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="92a89-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="92a89-108">Consulte a seção de comentários para obter uma lista de GUIDs com suporte.</span><span class="sxs-lookup"><span data-stu-id="92a89-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="92a89-109">[out] O valor da opção retornado.</span><span class="sxs-lookup"><span data-stu-id="92a89-109">[out] The value of the returned option.</span></span> <span data-ttu-id="92a89-110">O tipo desse valor será uma variante do tipo da opção especificada.</span><span class="sxs-lookup"><span data-stu-id="92a89-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92a89-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="92a89-111">Remarks</span></span>  
 <span data-ttu-id="92a89-112">A lista a seguir mostra os GUIDs que têm suporte para esse método.</span><span class="sxs-lookup"><span data-stu-id="92a89-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="92a89-113">Para obter descrições, consulte o [imetadatadispenserex:: SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="92a89-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="92a89-114">Se `optionId` é não esteja na lista, esse método retornará o HRESULT `E_INVALIDARG`, indicando um parâmetro incorreto.</span><span class="sxs-lookup"><span data-stu-id="92a89-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="92a89-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="92a89-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="92a89-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="92a89-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="92a89-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="92a89-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="92a89-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="92a89-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="92a89-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="92a89-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="92a89-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="92a89-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="92a89-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="92a89-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92a89-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92a89-122">Requirements</span></span>  
 <span data-ttu-id="92a89-123">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92a89-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92a89-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="92a89-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92a89-125">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="92a89-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92a89-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92a89-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a89-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92a89-127">See also</span></span>

- [<span data-ttu-id="92a89-128">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="92a89-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="92a89-129">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="92a89-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
