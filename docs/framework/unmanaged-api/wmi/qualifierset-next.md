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
ms.openlocfilehash: c9c824b0158618848c13183d92f88604460d5099
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141715"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="8f03a-103">Função QualifierSet_Next</span><span class="sxs-lookup"><span data-stu-id="8f03a-103">QualifierSet_Next function</span></span>
<span data-ttu-id="8f03a-104">Recupera o próximo qualificador em uma enumeração que começou com uma chamada para a função [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8f03a-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8f03a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f03a-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="8f03a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f03a-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="8f03a-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="8f03a-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="8f03a-108">no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="8f03a-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="8f03a-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="8f03a-109">[in] Reserved.</span></span> <span data-ttu-id="8f03a-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="8f03a-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="8f03a-111">fora O nome do qualificador.</span><span class="sxs-lookup"><span data-stu-id="8f03a-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="8f03a-112">Se `null`, esse parâmetro será ignorado; caso contrário, `pstrName` não deve apontar para um `BSTR` válido ou ocorrerá um vazamento de memória.</span><span class="sxs-lookup"><span data-stu-id="8f03a-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="8f03a-113">Se não for NULL, a função sempre alocará um novo `BSTR` quando ele retornar `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="8f03a-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="8f03a-114">fora Quando for bem-sucedido, o valor do qualificador.</span><span class="sxs-lookup"><span data-stu-id="8f03a-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="8f03a-115">Se a função falhar, o `VARIANT` apontado por `pVal` não será modificado.</span><span class="sxs-lookup"><span data-stu-id="8f03a-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="8f03a-116">Se esse parâmetro for `null`, o parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="8f03a-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="8f03a-117">fora Um ponteiro para um longo que recebe o tipo de qualificador.</span><span class="sxs-lookup"><span data-stu-id="8f03a-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="8f03a-118">Se as informações do tipo não forem desejadas, esse parâmetro poderá ser `null`.</span><span class="sxs-lookup"><span data-stu-id="8f03a-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="8f03a-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8f03a-119">Return value</span></span>

<span data-ttu-id="8f03a-120">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="8f03a-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8f03a-121">Constante</span><span class="sxs-lookup"><span data-stu-id="8f03a-121">Constant</span></span>  |<span data-ttu-id="8f03a-122">Valor</span><span class="sxs-lookup"><span data-stu-id="8f03a-122">Value</span></span>  |<span data-ttu-id="8f03a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f03a-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8f03a-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8f03a-124">0x80041008</span></span> | <span data-ttu-id="8f03a-125">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="8f03a-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="8f03a-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="8f03a-126">0x8004101d</span></span> | <span data-ttu-id="8f03a-127">O chamador não chamou [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8f03a-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8f03a-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8f03a-128">0x80041006</span></span> | <span data-ttu-id="8f03a-129">Não há memória suficiente disponível para iniciar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="8f03a-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="8f03a-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="8f03a-130">0x40005</span></span> | <span data-ttu-id="8f03a-131">Nenhum qualificador mais é deixado na enumeração.</span><span class="sxs-lookup"><span data-stu-id="8f03a-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8f03a-132">0</span><span class="sxs-lookup"><span data-stu-id="8f03a-132">0</span></span> | <span data-ttu-id="8f03a-133">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8f03a-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8f03a-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f03a-134">Remarks</span></span>

<span data-ttu-id="8f03a-135">Essa função encapsula uma chamada para o método [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) .</span><span class="sxs-lookup"><span data-stu-id="8f03a-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="8f03a-136">Você chama a função `QualifierSet_Next` repetidamente para enumerar todos os qualificadores até que a função retorne `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="8f03a-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="8f03a-137">Para encerrar a enumeração antecipadamente, chame a função [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8f03a-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="8f03a-138">A ordem dos qualificadores retornados durante a enumeração é indefinida.</span><span class="sxs-lookup"><span data-stu-id="8f03a-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f03a-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f03a-139">Requirements</span></span>  
 <span data-ttu-id="8f03a-140">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f03a-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f03a-141">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="8f03a-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8f03a-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8f03a-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f03a-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f03a-143">See also</span></span>

- [<span data-ttu-id="8f03a-144">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="8f03a-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
