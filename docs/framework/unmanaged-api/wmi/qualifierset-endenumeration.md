---
title: Função QualifierSet_EndEnumeration (referência de API não gerenciada)
description: A função de QualifierSet_EndEnumeration encerra uma enumeração.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9d3f8966f6333487631a0e155c7be49075a6992
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734669"
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="b710a-103">Função QualifierSet_EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="b710a-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="b710a-104">Finaliza a enumeração começada com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="b710a-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b710a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b710a-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="b710a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b710a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b710a-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="b710a-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="b710a-108">[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.</span><span class="sxs-lookup"><span data-stu-id="b710a-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="b710a-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b710a-109">Return value</span></span>

<span data-ttu-id="b710a-110">O seguinte valor retornado por essa função é definido na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-la como uma constante em seu código:</span><span class="sxs-lookup"><span data-stu-id="b710a-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="b710a-111">Constante</span><span class="sxs-lookup"><span data-stu-id="b710a-111">Constant</span></span>  |<span data-ttu-id="b710a-112">Valor</span><span class="sxs-lookup"><span data-stu-id="b710a-112">Value</span></span>  |<span data-ttu-id="b710a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b710a-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b710a-114">0</span><span class="sxs-lookup"><span data-stu-id="b710a-114">0</span></span> | <span data-ttu-id="b710a-115">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b710a-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b710a-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="b710a-116">Remarks</span></span>

<span data-ttu-id="b710a-117">Essa função encapsula uma chamada para o [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) método.</span><span class="sxs-lookup"><span data-stu-id="b710a-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="b710a-118">Essa chamada é recomendada, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="b710a-118">This call is recommended, but not required.</span></span> <span data-ttu-id="b710a-119">Ele libera imediatamente os recursos associados com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="b710a-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="b710a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b710a-120">Requirements</span></span>  

<span data-ttu-id="b710a-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b710a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="b710a-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b710a-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="b710a-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b710a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b710a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b710a-124">See also</span></span>
- [<span data-ttu-id="b710a-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b710a-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
