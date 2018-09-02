---
title: Função QualifierSet_Next (referência de API não gerenciada)
description: A função QualifierSet_Next recupera o próximo qualificador em uma enumeração.
ms.date: 11/06/2017
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
ms.openlocfilehash: 938044a4e932139eb8a4d0a5d2f998cbc6f193cb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405521"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="129ee-103">Função QualifierSet_Next</span><span class="sxs-lookup"><span data-stu-id="129ee-103">QualifierSet_Next function</span></span>
<span data-ttu-id="129ee-104">Recupera o próximo qualificador em uma enumeração que foi iniciado com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="129ee-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="129ee-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="129ee-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="129ee-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="129ee-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="129ee-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="129ee-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="129ee-108">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="129ee-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="129ee-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="129ee-109">[in] Reserved.</span></span> <span data-ttu-id="129ee-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="129ee-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="129ee-111">[out] O nome do qualificador.</span><span class="sxs-lookup"><span data-stu-id="129ee-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="129ee-112">Se `null`, esse parâmetro é ignorado; caso contrário, `pstrName` não deve apontar para um válido `BSTR` ou ocorre um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="129ee-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="129ee-113">Se não nulo, a função sempre aloca um novo `BSTR` quando ele retorna `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="129ee-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="129ee-114">[out] Quando obtiver êxito, o valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="129ee-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="129ee-115">Se a função falhar, o `VARIANT` apontado por `pVal` não será modificado.</span><span class="sxs-lookup"><span data-stu-id="129ee-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="129ee-116">Se esse parâmetro for `null`, o parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="129ee-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="129ee-117">[out] Um ponteiro para um longo que recebe o tipo de qualificador.</span><span class="sxs-lookup"><span data-stu-id="129ee-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="129ee-118">Se as informações de tipo não for desejadas, esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="129ee-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="129ee-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="129ee-119">Return value</span></span>

<span data-ttu-id="129ee-120">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="129ee-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="129ee-121">Constante</span><span class="sxs-lookup"><span data-stu-id="129ee-121">Constant</span></span>  |<span data-ttu-id="129ee-122">Valor</span><span class="sxs-lookup"><span data-stu-id="129ee-122">Value</span></span>  |<span data-ttu-id="129ee-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="129ee-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="129ee-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="129ee-124">0x80041008</span></span> | <span data-ttu-id="129ee-125">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="129ee-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="129ee-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="129ee-126">0x8004101d</span></span> | <span data-ttu-id="129ee-127">O chamador não chamou [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="129ee-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="129ee-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="129ee-128">0x80041006</span></span> | <span data-ttu-id="129ee-129">Não há memória suficiente está disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="129ee-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="129ee-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="129ee-130">0x40005</span></span> | <span data-ttu-id="129ee-131">Não há mais qualificadores são deixadas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="129ee-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="129ee-132">0</span><span class="sxs-lookup"><span data-stu-id="129ee-132">0</span></span> | <span data-ttu-id="129ee-133">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="129ee-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="129ee-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="129ee-134">Remarks</span></span>

<span data-ttu-id="129ee-135">Essa função encapsula uma chamada para o [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) método.</span><span class="sxs-lookup"><span data-stu-id="129ee-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="129ee-136">Você chama o `QualifierSet_Next` função repetidamente para enumerar todos os qualificadores até o retorno da função `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="129ee-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="129ee-137">Para encerrar a enumeração no início, chame o [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="129ee-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="129ee-138">A ordem dos qualificadores retornado durante a enumeração é indefinida.</span><span class="sxs-lookup"><span data-stu-id="129ee-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="129ee-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="129ee-139">Requirements</span></span>  
 <span data-ttu-id="129ee-140">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="129ee-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="129ee-141">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="129ee-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="129ee-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="129ee-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="129ee-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="129ee-143">See also</span></span>  
[<span data-ttu-id="129ee-144">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="129ee-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
