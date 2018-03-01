---
title: "Função QualifierSet_Get (referência de API não gerenciada)"
description: "A função QualifierSet_Get obtém um qualificador nomeado."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 93ba4e59dda4806931ba085f8c63b63a1d8bd797
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="9968e-103">Função QualifierSet_Get</span><span class="sxs-lookup"><span data-stu-id="9968e-103">QualifierSet_Get function</span></span>
<span data-ttu-id="9968e-104">Obtém o qualificador nomeado especificado.</span><span class="sxs-lookup"><span data-stu-id="9968e-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9968e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9968e-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="9968e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9968e-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="9968e-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="9968e-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="9968e-108">[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="9968e-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="9968e-109">[in] O nome do qualificador de cujo valor é solicitado.</span><span class="sxs-lookup"><span data-stu-id="9968e-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="9968e-110">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="9968e-110">[in] Reserved.</span></span> <span data-ttu-id="9968e-111">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="9968e-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="9968e-112">[out] Quando obtiver êxito, o tipo correto e o valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="9968e-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="9968e-113">Se a função falhar, o `VARIANT` apontada pelo `pVal` não é modificado.</span><span class="sxs-lookup"><span data-stu-id="9968e-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="9968e-114">Se esse parâmetro for `null`, o parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="9968e-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="9968e-115">[out] Um ponteiro para um longo que recebe os bits de tipo de qualificador para o qualificador solicitado.</span><span class="sxs-lookup"><span data-stu-id="9968e-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="9968e-116">Se as informações de tipo não for desejadas, esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="9968e-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="9968e-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9968e-117">Return value</span></span>

<span data-ttu-id="9968e-118">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9968e-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9968e-119">Constante</span><span class="sxs-lookup"><span data-stu-id="9968e-119">Constant</span></span>  |<span data-ttu-id="9968e-120">Valor</span><span class="sxs-lookup"><span data-stu-id="9968e-120">Value</span></span>  |<span data-ttu-id="9968e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9968e-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9968e-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9968e-122">0x80041008</span></span> | <span data-ttu-id="9968e-123">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="9968e-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="9968e-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9968e-124">0x80041002</span></span> | <span data-ttu-id="9968e-125">O qualificador especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="9968e-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9968e-126">0</span><span class="sxs-lookup"><span data-stu-id="9968e-126">0</span></span> | <span data-ttu-id="9968e-127">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9968e-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9968e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9968e-128">Remarks</span></span>

<span data-ttu-id="9968e-129">Essa função encapsula uma chamada para o [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="9968e-129">This function wraps a call to the [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9968e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9968e-130">Requirements</span></span>  
 <span data-ttu-id="9968e-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9968e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9968e-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9968e-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9968e-133">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9968e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9968e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9968e-134">See also</span></span>  
[<span data-ttu-id="9968e-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9968e-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
