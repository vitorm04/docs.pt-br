---
title: Obter função (referência de API não gerenciada)
description: A função Get recupera o valor da propriedade especificada.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69312030689ab1b87e3aadd040395f06e1c94ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="get-function"></a><span data-ttu-id="9a477-103">Função Get</span><span class="sxs-lookup"><span data-stu-id="9a477-103">Get function</span></span>
<span data-ttu-id="9a477-104">Recupera o valor da propriedade especificado se ele existir.</span><span class="sxs-lookup"><span data-stu-id="9a477-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="9a477-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a477-105">Syntax</span></span>  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="9a477-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a477-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9a477-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="9a477-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9a477-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="9a477-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="9a477-109">[in] O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a477-109">[in] The name of the property.</span></span>

<span data-ttu-id="9a477-110">`lFlags`[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="9a477-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="9a477-111">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="9a477-111">This parameter must be 0.</span></span>

<span data-ttu-id="9a477-112">`pVal`[out] Se a função retornar com êxito, contém o valor de `wszName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a477-112">`pVal` [out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="9a477-113">O `pval` argumento recebe o tipo correto e o valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="9a477-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

<span data-ttu-id="9a477-114">`pvtType`[out] Se a função retornar com êxito, contém um [constante do tipo CIM](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) que indica o tipo de propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a477-114">`pvtType` [out] If the function returns successfully, contains a [CIM-type constant](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) that indicates the property type.</span></span> <span data-ttu-id="9a477-115">O valor também pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="9a477-115">Its value can also be `null`.</span></span> 

<span data-ttu-id="9a477-116">`plFlavor`[out] Se a função retornar com êxito, recebe informações sobre a origem da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9a477-116">`plFlavor` [out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="9a477-117">Seu valor pode ser `null`, ou uma das seguintes constantes WBEM_FLAVOR_TYPE definidas no *WbemCli.h* arquivo de cabeçalho:</span><span class="sxs-lookup"><span data-stu-id="9a477-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="9a477-118">Constante</span><span class="sxs-lookup"><span data-stu-id="9a477-118">Constant</span></span>  |<span data-ttu-id="9a477-119">Valor</span><span class="sxs-lookup"><span data-stu-id="9a477-119">Value</span></span>  |<span data-ttu-id="9a477-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a477-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="9a477-121">0x40</span><span class="sxs-lookup"><span data-stu-id="9a477-121">0x40</span></span> | <span data-ttu-id="9a477-122">A propriedade é uma propriedade de sistema padrão.</span><span class="sxs-lookup"><span data-stu-id="9a477-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="9a477-123">0x20</span><span class="sxs-lookup"><span data-stu-id="9a477-123">0x20</span></span> | <span data-ttu-id="9a477-124">Para uma classe: A propriedade é herdada da classe pai.</span><span class="sxs-lookup"><span data-stu-id="9a477-124">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="9a477-125">Para uma instância: A propriedade, enquanto herdada da classe pai, não foi modificada pela instância.</span><span class="sxs-lookup"><span data-stu-id="9a477-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="9a477-126">0</span><span class="sxs-lookup"><span data-stu-id="9a477-126">0</span></span> | <span data-ttu-id="9a477-127">Para uma classe: A propriedade pertence à classe derivada.</span><span class="sxs-lookup"><span data-stu-id="9a477-127">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="9a477-128">Para uma instância: A propriedade é modificada pela instância; ou seja, foi fornecido um valor ou um qualificador foi adicionado ou modificado.</span><span class="sxs-lookup"><span data-stu-id="9a477-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="9a477-129">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9a477-129">Return value</span></span>

<span data-ttu-id="9a477-130">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9a477-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9a477-131">Constante</span><span class="sxs-lookup"><span data-stu-id="9a477-131">Constant</span></span>  |<span data-ttu-id="9a477-132">Valor</span><span class="sxs-lookup"><span data-stu-id="9a477-132">Value</span></span>  |<span data-ttu-id="9a477-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a477-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="9a477-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9a477-134">0x80041001</span></span> | <span data-ttu-id="9a477-135">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="9a477-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9a477-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9a477-136">0x80041008</span></span> | <span data-ttu-id="9a477-137">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="9a477-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="9a477-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9a477-138">0x80041002</span></span> | <span data-ttu-id="9a477-139">A propriedade especificada não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="9a477-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9a477-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9a477-140">0x80041006</span></span> | <span data-ttu-id="9a477-141">Não há memória suficiente está disponível para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9a477-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9a477-142">0</span><span class="sxs-lookup"><span data-stu-id="9a477-142">0</span></span> | <span data-ttu-id="9a477-143">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9a477-143">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9a477-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a477-144">Remarks</span></span>

<span data-ttu-id="9a477-145">Essa função encapsula uma chamada para o [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="9a477-145">This function wraps a call to the [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="9a477-146">O `Get` função também pode retornar propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="9a477-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="9a477-147">O `pVal` argumento recebe o tipo correto e o valor para o qualificador e o COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) função</span><span class="sxs-lookup"><span data-stu-id="9a477-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) function</span></span>

## <a name="requirements"></a><span data-ttu-id="9a477-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a477-148">Requirements</span></span>  
 <span data-ttu-id="9a477-149">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a477-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a477-150">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9a477-150">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9a477-151">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9a477-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a477-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a477-152">See also</span></span>  
[<span data-ttu-id="9a477-153">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9a477-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
