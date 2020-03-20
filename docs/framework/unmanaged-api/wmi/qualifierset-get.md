---
title: QualifierSet_Get função (referência de API não gerenciada)
description: A função QualifierSet_Get recebe um qualificador nomeado.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174882"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="31b58-103">Função QualifierSet_Get</span><span class="sxs-lookup"><span data-stu-id="31b58-103">QualifierSet_Get function</span></span>
<span data-ttu-id="31b58-104">Obtém o qualificador nomeado especificado.</span><span class="sxs-lookup"><span data-stu-id="31b58-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="31b58-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31b58-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="31b58-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="31b58-106">Parameters</span></span>

<span data-ttu-id="31b58-107">`vFunc`[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="31b58-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="31b58-108">`ptr`[em] Um ponteiro para uma instância [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="31b58-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="31b58-109">`wszName`[em] O nome do qualificador cujo valor é solicitado.</span><span class="sxs-lookup"><span data-stu-id="31b58-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="31b58-110">`lFlags`[em] Reservados.</span><span class="sxs-lookup"><span data-stu-id="31b58-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="31b58-111">Este parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="31b58-111">This parameter must be 0.</span></span>

<span data-ttu-id="31b58-112">`pVal`[fora] Quando bem sucedido, o tipo e valor corretos para o qualificador.</span><span class="sxs-lookup"><span data-stu-id="31b58-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="31b58-113">Se a função `VARIANT` falhar, `pVal` o apontado por não é modificado.</span><span class="sxs-lookup"><span data-stu-id="31b58-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="31b58-114">Se este parâmetro `null`for, o parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="31b58-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="31b58-115">`plFlavor`[fora] Um ponteiro para um LONG que recebe os bits de sabor qualificador para o qualificador solicitado.</span><span class="sxs-lookup"><span data-stu-id="31b58-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="31b58-116">Se a informação do sabor não for `null`desejada, este parâmetro pode ser .</span><span class="sxs-lookup"><span data-stu-id="31b58-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="31b58-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="31b58-117">Return value</span></span>

<span data-ttu-id="31b58-118">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="31b58-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="31b58-119">Constante</span><span class="sxs-lookup"><span data-stu-id="31b58-119">Constant</span></span>  |<span data-ttu-id="31b58-120">Valor</span><span class="sxs-lookup"><span data-stu-id="31b58-120">Value</span></span>  |<span data-ttu-id="31b58-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="31b58-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="31b58-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="31b58-122">0x80041008</span></span> | <span data-ttu-id="31b58-123">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="31b58-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="31b58-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="31b58-124">0x80041002</span></span> | <span data-ttu-id="31b58-125">O qualificador especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="31b58-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="31b58-126">0</span><span class="sxs-lookup"><span data-stu-id="31b58-126">0</span></span> | <span data-ttu-id="31b58-127">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="31b58-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="31b58-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="31b58-128">Remarks</span></span>

<span data-ttu-id="31b58-129">Esta função envolve uma chamada para o método [IWbemQualifierSet::Get.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)</span><span class="sxs-lookup"><span data-stu-id="31b58-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="31b58-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31b58-130">Requirements</span></span>  
 <span data-ttu-id="31b58-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31b58-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31b58-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="31b58-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="31b58-133">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="31b58-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b58-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="31b58-134">See also</span></span>

- [<span data-ttu-id="31b58-135">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="31b58-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
