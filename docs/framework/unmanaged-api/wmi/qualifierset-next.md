---
title: "Função QualifierSet_Next (referência de API não gerenciada)"
description: "A função QualifierSet_Next recupera o próximo qualificador em uma enumeração."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="10993-103">Função QualifierSet_Next</span><span class="sxs-lookup"><span data-stu-id="10993-103">QualifierSet_Next function</span></span>
<span data-ttu-id="10993-104">Recupera o próximo qualificador em uma enumeração que foi iniciado com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="10993-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="10993-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10993-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="10993-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10993-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="10993-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="10993-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="10993-108">[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="10993-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="10993-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="10993-109">[in] Reserved.</span></span> <span data-ttu-id="10993-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="10993-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="10993-111">[out] O nome do qualificador de.</span><span class="sxs-lookup"><span data-stu-id="10993-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="10993-112">Se `null`, este parâmetro é ignorado; caso contrário, `pstrName` não deve apontar para um válida `BSTR` ou ocorre um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="10993-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="10993-113">Se não nulo, a função sempre aloca um novo `BSTR` quando ele retorna `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="10993-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="10993-114">[out] Quando obtiver êxito, o valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="10993-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="10993-115">Se a função falhar, o `VARIANT` apontada pelo `pVal` não é modificado.</span><span class="sxs-lookup"><span data-stu-id="10993-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="10993-116">Se esse parâmetro for `null`, o parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="10993-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="10993-117">[out] Um ponteiro para um longo que recebe o tipo de qualificador.</span><span class="sxs-lookup"><span data-stu-id="10993-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="10993-118">Se as informações de tipo não for desejadas, esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="10993-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="10993-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="10993-119">Return value</span></span>

<span data-ttu-id="10993-120">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="10993-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="10993-121">Constante</span><span class="sxs-lookup"><span data-stu-id="10993-121">Constant</span></span>  |<span data-ttu-id="10993-122">Valor</span><span class="sxs-lookup"><span data-stu-id="10993-122">Value</span></span>  |<span data-ttu-id="10993-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="10993-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="10993-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="10993-124">0x80041008</span></span> | <span data-ttu-id="10993-125">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="10993-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="10993-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="10993-126">0x8004101d</span></span> | <span data-ttu-id="10993-127">O chamador não chamou [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="10993-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="10993-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="10993-128">0x80041006</span></span> | <span data-ttu-id="10993-129">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="10993-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="10993-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="10993-130">0x40005</span></span> | <span data-ttu-id="10993-131">Não há mais qualificadores são deixadas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="10993-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="10993-132">0</span><span class="sxs-lookup"><span data-stu-id="10993-132">0</span></span> | <span data-ttu-id="10993-133">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="10993-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="10993-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="10993-134">Remarks</span></span>

<span data-ttu-id="10993-135">Essa função encapsula uma chamada para o [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="10993-135">This function wraps a call to the [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="10993-136">Você chama o `QualifierSet_Next` função repetidamente para enumerar todos os qualificadores até que a função de retorno `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="10993-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="10993-137">Para encerrar a enumeração no início, chame o [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="10993-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="10993-138">A ordem dos qualificadores retornado durante a enumeração é indefinida.</span><span class="sxs-lookup"><span data-stu-id="10993-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="10993-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10993-139">Requirements</span></span>  
 <span data-ttu-id="10993-140">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10993-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10993-141">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="10993-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="10993-142">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="10993-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10993-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10993-143">See also</span></span>  
[<span data-ttu-id="10993-144">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="10993-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
