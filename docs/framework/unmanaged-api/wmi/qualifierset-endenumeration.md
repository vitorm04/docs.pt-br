---
title: "Função QualifierSet_EndEnumeration (referência de API não gerenciada)"
description: "A função QualifierSet_EndEnumeration encerra uma enumeração."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_EndEnumeration
helpviewer_keywords: QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7868a0c0ba5abb880af201ce73b35f5ffed6f223
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="835a8-103">Função QualifierSet_EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="835a8-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="835a8-104">Finaliza a enumeração iniciada com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função.</span><span class="sxs-lookup"><span data-stu-id="835a8-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="835a8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="835a8-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="835a8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="835a8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="835a8-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="835a8-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="835a8-108">[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="835a8-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="835a8-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="835a8-109">Return value</span></span>

<span data-ttu-id="835a8-110">O seguinte valor retornado por essa função é definido no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-la como uma constante em seu código:</span><span class="sxs-lookup"><span data-stu-id="835a8-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="835a8-111">Constante</span><span class="sxs-lookup"><span data-stu-id="835a8-111">Constant</span></span>  |<span data-ttu-id="835a8-112">Valor</span><span class="sxs-lookup"><span data-stu-id="835a8-112">Value</span></span>  |<span data-ttu-id="835a8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="835a8-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="835a8-114">0</span><span class="sxs-lookup"><span data-stu-id="835a8-114">0</span></span> | <span data-ttu-id="835a8-115">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="835a8-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="835a8-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="835a8-116">Remarks</span></span>

<span data-ttu-id="835a8-117">Essa função encapsula uma chamada para o [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="835a8-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="835a8-118">Esta chamada é recomendada, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="835a8-118">This call is recommended, but not required.</span></span> <span data-ttu-id="835a8-119">Imediatamente, ele libera recursos associados com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="835a8-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="835a8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="835a8-120">Requirements</span></span>  

<span data-ttu-id="835a8-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="835a8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="835a8-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="835a8-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="835a8-123">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="835a8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835a8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="835a8-124">See also</span></span>  
[<span data-ttu-id="835a8-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="835a8-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
