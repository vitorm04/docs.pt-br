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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008775"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="2d2e4-102">Método IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="2d2e4-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="2d2e4-103">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="2d2e4-104">A opção controla como as chamadas para o escopo de metadados atual são tratadas.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2e4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d2e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d2e4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d2e4-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="2d2e4-107">no Um ponteiro para um GUID que especifica a opção a ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="2d2e4-108">Consulte a seção comentários para obter uma lista de GUIDs com suporte.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2d2e4-109">fora O valor da opção retornada.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-109">[out] The value of the returned option.</span></span> <span data-ttu-id="2d2e4-110">O tipo desse valor será uma variante do tipo da opção especificada.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d2e4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d2e4-111">Remarks</span></span>  
 <span data-ttu-id="2d2e4-112">A lista a seguir mostra os GUIDs que têm suporte para esse método.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="2d2e4-113">Para obter descrições, consulte o método [IMetaDataDispenserEx:: SetOption](imetadatadispenserex-setoption-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2d2e4-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="2d2e4-114">Se `optionId` não estiver nessa lista, esse método retornará HRESULT `E_INVALIDARG` , indicando um parâmetro incorreto.</span><span class="sxs-lookup"><span data-stu-id="2d2e4-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="2d2e4-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="2d2e4-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="2d2e4-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="2d2e4-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="2d2e4-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="2d2e4-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="2d2e4-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="2d2e4-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="2d2e4-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="2d2e4-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="2d2e4-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="2d2e4-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="2d2e4-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="2d2e4-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d2e4-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d2e4-122">Requirements</span></span>  
 <span data-ttu-id="2d2e4-123">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d2e4-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d2e4-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d2e4-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d2e4-125">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d2e4-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d2e4-126">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d2e4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2e4-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="2d2e4-127">See also</span></span>

- [<span data-ttu-id="2d2e4-128">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="2d2e4-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="2d2e4-129">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="2d2e4-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
