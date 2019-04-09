---
title: Função QualifierSet_Get (referência de API não gerenciada)
description: A função QualifierSet_Get obtém um qualificador nomeado.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0dc76a2732bf9c1e4f3a26fa2d045bfbcd837ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181084"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="859c6-103">Função QualifierSet_Get</span><span class="sxs-lookup"><span data-stu-id="859c6-103">QualifierSet_Get function</span></span>
<span data-ttu-id="859c6-104">Obtém o qualificador nomeado especificado.</span><span class="sxs-lookup"><span data-stu-id="859c6-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="859c6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="859c6-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="859c6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="859c6-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="859c6-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="859c6-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="859c6-108">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="859c6-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="859c6-109">[in] O nome do qualificador cujo valor é solicitado.</span><span class="sxs-lookup"><span data-stu-id="859c6-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="859c6-110">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="859c6-110">[in] Reserved.</span></span> <span data-ttu-id="859c6-111">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="859c6-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="859c6-112">[out] Quando obtiver êxito, o tipo correto e o valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="859c6-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="859c6-113">Se a função falhar, o `VARIANT` apontado por `pVal` não será modificado.</span><span class="sxs-lookup"><span data-stu-id="859c6-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="859c6-114">Se esse parâmetro for `null`, o parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="859c6-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="859c6-115">[out] Um ponteiro para um longo que recebe os bits de flavor qualificador para o qualificador solicitado.</span><span class="sxs-lookup"><span data-stu-id="859c6-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="859c6-116">Se as informações de tipo não for desejadas, esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="859c6-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="859c6-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="859c6-117">Return value</span></span>

<span data-ttu-id="859c6-118">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="859c6-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="859c6-119">Constante</span><span class="sxs-lookup"><span data-stu-id="859c6-119">Constant</span></span>  |<span data-ttu-id="859c6-120">Valor</span><span class="sxs-lookup"><span data-stu-id="859c6-120">Value</span></span>  |<span data-ttu-id="859c6-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="859c6-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="859c6-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="859c6-122">0x80041008</span></span> | <span data-ttu-id="859c6-123">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="859c6-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="859c6-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="859c6-124">0x80041002</span></span> | <span data-ttu-id="859c6-125">O qualificador especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="859c6-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="859c6-126">0</span><span class="sxs-lookup"><span data-stu-id="859c6-126">0</span></span> | <span data-ttu-id="859c6-127">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="859c6-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="859c6-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="859c6-128">Remarks</span></span>

<span data-ttu-id="859c6-129">Essa função encapsula uma chamada para o [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) método.</span><span class="sxs-lookup"><span data-stu-id="859c6-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="859c6-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="859c6-130">Requirements</span></span>  
 <span data-ttu-id="859c6-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="859c6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="859c6-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="859c6-132">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="859c6-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="859c6-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="859c6-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="859c6-134">See also</span></span>

- [<span data-ttu-id="859c6-135">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="859c6-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
