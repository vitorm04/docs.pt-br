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
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177727"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="b19fb-102">Método IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="b19fb-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="b19fb-103">Obtém o valor da opção especificada para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="b19fb-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="b19fb-104">A opção controla como as chamadas para o escopo de metadados atuais são tratadas.</span><span class="sxs-lookup"><span data-stu-id="b19fb-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19fb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b19fb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b19fb-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b19fb-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="b19fb-107">[em] Um ponteiro para um GUID que especifica a opção a ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="b19fb-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="b19fb-108">Consulte a seção Observações para obter uma lista de GUIDs suportados.</span><span class="sxs-lookup"><span data-stu-id="b19fb-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b19fb-109">[fora] O valor da opção devolvida.</span><span class="sxs-lookup"><span data-stu-id="b19fb-109">[out] The value of the returned option.</span></span> <span data-ttu-id="b19fb-110">O tipo deste valor será uma variante do tipo da opção especificada.</span><span class="sxs-lookup"><span data-stu-id="b19fb-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b19fb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b19fb-111">Remarks</span></span>  
 <span data-ttu-id="b19fb-112">A lista a seguir mostra os GUIDs que são suportados para este método.</span><span class="sxs-lookup"><span data-stu-id="b19fb-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="b19fb-113">Para obter descrições, consulte o método [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)</span><span class="sxs-lookup"><span data-stu-id="b19fb-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="b19fb-114">Se `optionId` não estiver nesta lista, este `E_INVALIDARG`método retorna HRESULT , indicando um parâmetro incorreto.</span><span class="sxs-lookup"><span data-stu-id="b19fb-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="b19fb-115">MetaDadosVerificandoduplicadosPara</span><span class="sxs-lookup"><span data-stu-id="b19fb-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="b19fb-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="b19fb-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="b19fb-117">MetaDataNotificationToKenMovement</span><span class="sxs-lookup"><span data-stu-id="b19fb-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="b19fb-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="b19fb-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="b19fb-119">MetaDataErrorItItOutOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="b19fb-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="b19fb-120">MetaDataGeraradaptados DESEGURANÇA</span><span class="sxs-lookup"><span data-stu-id="b19fb-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="b19fb-121">Opções de MetaDataLinker</span><span class="sxs-lookup"><span data-stu-id="b19fb-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b19fb-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b19fb-122">Requirements</span></span>  
 <span data-ttu-id="b19fb-123">**Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b19fb-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19fb-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b19fb-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b19fb-125">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b19fb-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b19fb-126">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19fb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19fb-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="b19fb-127">See also</span></span>

- [<span data-ttu-id="b19fb-128">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="b19fb-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="b19fb-129">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="b19fb-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
