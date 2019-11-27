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
ms.openlocfilehash: ab74b02df959fe6e6457273e67ba3b82ae6a015c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435999"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="9d87b-102">Método IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="9d87b-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="9d87b-103">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="9d87b-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="9d87b-104">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="9d87b-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d87b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d87b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d87b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d87b-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="9d87b-107">no Um ponteiro para um GUID que especifica a opção a ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="9d87b-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="9d87b-108">Consulte a seção comentários para obter uma lista de GUIDs com suporte.</span><span class="sxs-lookup"><span data-stu-id="9d87b-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9d87b-109">fora O valor da opção retornada.</span><span class="sxs-lookup"><span data-stu-id="9d87b-109">[out] The value of the returned option.</span></span> <span data-ttu-id="9d87b-110">O tipo desse valor será uma variante do tipo da opção especificada.</span><span class="sxs-lookup"><span data-stu-id="9d87b-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d87b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d87b-111">Remarks</span></span>  
 <span data-ttu-id="9d87b-112">A lista a seguir mostra os GUIDs que têm suporte para esse método.</span><span class="sxs-lookup"><span data-stu-id="9d87b-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="9d87b-113">Para obter descrições, consulte o método [IMetaDataDispenserEx:: SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d87b-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="9d87b-114">Se `optionId` não estiver nessa lista, esse método retornará o HRESULT `E_INVALIDARG`, indicando um parâmetro incorreto.</span><span class="sxs-lookup"><span data-stu-id="9d87b-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="9d87b-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="9d87b-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="9d87b-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="9d87b-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="9d87b-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="9d87b-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="9d87b-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="9d87b-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="9d87b-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="9d87b-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="9d87b-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="9d87b-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="9d87b-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="9d87b-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d87b-122">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9d87b-122">Requirements</span></span>  
 <span data-ttu-id="9d87b-123">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d87b-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d87b-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9d87b-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d87b-125">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d87b-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d87b-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d87b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d87b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d87b-127">See also</span></span>

- [<span data-ttu-id="9d87b-128">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9d87b-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="9d87b-129">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="9d87b-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
