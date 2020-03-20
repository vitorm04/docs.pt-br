---
title: QualifierSet_Next função (referência de API não gerenciada)
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
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174869"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="0d6c3-103">Função QualifierSet_Next</span><span class="sxs-lookup"><span data-stu-id="0d6c3-103">QualifierSet_Next function</span></span>
<span data-ttu-id="0d6c3-104">Recupera o próximo qualificador em uma enumeração que começou com uma chamada para a função [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0d6c3-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0d6c3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d6c3-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="0d6c3-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d6c3-106">Parameters</span></span>

<span data-ttu-id="0d6c3-107">`vFunc`[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="0d6c3-108">`ptr`[em] Um ponteiro para uma instância [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="0d6c3-109">`lFlags`[em] Reservados.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="0d6c3-110">Este parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-110">This parameter must be 0.</span></span>

<span data-ttu-id="0d6c3-111">`pstrName`[fora] O nome da qualificatória.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="0d6c3-112">Se `null`, este parâmetro é ignorado; caso contrário, `pstrName` não deve `BSTR` apontar para um vazamento válido ou de memória.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="0d6c3-113">Se não for nula, a `BSTR` função `WBEM_S_NO_ERROR`sempre aloca um novo quando retorna .</span><span class="sxs-lookup"><span data-stu-id="0d6c3-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="0d6c3-114">`pVal`[fora] Quando bem sucedido, o valor para o qualificador.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="0d6c3-115">Se a função `VARIANT` falhar, `pVal` o apontado por não é modificado.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="0d6c3-116">Se este parâmetro `null`for, o parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="0d6c3-117">`plFlavor`[fora] Um ponteiro para um LONG que recebe o sabor qualificado.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="0d6c3-118">Se a informação do sabor não for `null`desejada, este parâmetro pode ser .</span><span class="sxs-lookup"><span data-stu-id="0d6c3-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d6c3-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0d6c3-119">Return value</span></span>

<span data-ttu-id="0d6c3-120">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0d6c3-121">Constante</span><span class="sxs-lookup"><span data-stu-id="0d6c3-121">Constant</span></span>  |<span data-ttu-id="0d6c3-122">Valor</span><span class="sxs-lookup"><span data-stu-id="0d6c3-122">Value</span></span>  |<span data-ttu-id="0d6c3-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d6c3-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0d6c3-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0d6c3-124">0x80041008</span></span> | <span data-ttu-id="0d6c3-125">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="0d6c3-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="0d6c3-126">0x8004101d</span></span> | <span data-ttu-id="0d6c3-127">O interlocutor não [ligou para QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0d6c3-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0d6c3-128">0x80041006</span></span> | <span data-ttu-id="0d6c3-129">Não há memória suficiente disponível para começar uma nova enumeração.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="0d6c3-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="0d6c3-130">0x40005</span></span> | <span data-ttu-id="0d6c3-131">Não restam mais qualificações na enumeração.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0d6c3-132">0</span><span class="sxs-lookup"><span data-stu-id="0d6c3-132">0</span></span> | <span data-ttu-id="0d6c3-133">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0d6c3-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d6c3-134">Remarks</span></span>

<span data-ttu-id="0d6c3-135">Esta função envolve uma chamada para o [método IWbemQualifierSet:::Next.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="0d6c3-136">Você chama `QualifierSet_Next` a função repetidamente para enumerar todas `WBEM_S_NO_MORE_DATA`as qualificações até que a função retorne .</span><span class="sxs-lookup"><span data-stu-id="0d6c3-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="0d6c3-137">Para encerrar a enumeração mais cedo, chame a função [QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="0d6c3-138">A ordem das qualificatórias devolvidas durante a enumeração é indefinida.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d6c3-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d6c3-139">Requirements</span></span>  
 <span data-ttu-id="0d6c3-140">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6c3-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6c3-141">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0d6c3-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0d6c3-142">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6c3-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6c3-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d6c3-143">See also</span></span>

- [<span data-ttu-id="0d6c3-144">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
