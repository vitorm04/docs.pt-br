---
title: Função NextMethod (referência de API não gerenciada)
description: A função NextMethod recupera o próximo método em uma enumeração.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1c20fe5b4a081bd41f51365a36ab5f8f8cfb71ed
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127370"
---
# <a name="nextmethod-function"></a><span data-ttu-id="49e02-103">Função NextMethod</span><span class="sxs-lookup"><span data-stu-id="49e02-103">NextMethod function</span></span>
<span data-ttu-id="49e02-104">Recupera o próximo método em uma enumeração que começa com uma chamada para [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="49e02-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="49e02-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49e02-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="49e02-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49e02-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="49e02-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="49e02-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="49e02-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="49e02-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="49e02-109">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="49e02-109">[in] Reserved.</span></span> <span data-ttu-id="49e02-110">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="49e02-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="49e02-111">fora Um ponteiro que aponta para `null` antes da chamada.</span><span class="sxs-lookup"><span data-stu-id="49e02-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="49e02-112">Quando a função retorna, o endereço de um novo `BSTR` que contém o nome do método.</span><span class="sxs-lookup"><span data-stu-id="49e02-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="49e02-113">fora Um ponteiro que recebe um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que contém os parâmetros de `in` para o método.</span><span class="sxs-lookup"><span data-stu-id="49e02-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="49e02-114">fora Um ponteiro que recebe um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que contém os parâmetros de `out` para o método.</span><span class="sxs-lookup"><span data-stu-id="49e02-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="49e02-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="49e02-115">Return value</span></span>

<span data-ttu-id="49e02-116">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="49e02-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="49e02-117">Constante</span><span class="sxs-lookup"><span data-stu-id="49e02-117">Constant</span></span>  |<span data-ttu-id="49e02-118">Valor</span><span class="sxs-lookup"><span data-stu-id="49e02-118">Value</span></span>  |<span data-ttu-id="49e02-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="49e02-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="49e02-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="49e02-120">0x8004101d</span></span> | <span data-ttu-id="49e02-121">Não havia nenhuma chamada para a função [`BeginEnumeration`](beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="49e02-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="49e02-122">0</span><span class="sxs-lookup"><span data-stu-id="49e02-122">0</span></span> | <span data-ttu-id="49e02-123">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="49e02-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="49e02-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="49e02-124">0x40005</span></span> | <span data-ttu-id="49e02-125">Não há mais propriedades na enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e02-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="49e02-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="49e02-126">Remarks</span></span>

<span data-ttu-id="49e02-127">Essa função encapsula uma chamada para o método [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .</span><span class="sxs-lookup"><span data-stu-id="49e02-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="49e02-128">O chamador começa a sequência de enumeração chamando a função [BeginMethodEnumeration](beginmethodenumeration.md) e, em seguida, chama a função [NextMethod] até que a função retorne `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="49e02-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="49e02-129">Opcionalmente, o chamador conclui a sequência chamando [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="49e02-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="49e02-130">O chamador pode encerrar a enumeração antecipadamente chamando [EndMethodEnumeration](endmethodenumeration.md) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="49e02-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="49e02-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49e02-131">Example</span></span>

<span data-ttu-id="49e02-132">Para obter C++ um exemplo, consulte o método [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .</span><span class="sxs-lookup"><span data-stu-id="49e02-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49e02-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49e02-133">Requirements</span></span>  
 <span data-ttu-id="49e02-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49e02-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49e02-135">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="49e02-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="49e02-136">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="49e02-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e02-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49e02-137">See also</span></span>

- [<span data-ttu-id="49e02-138">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="49e02-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
