---
title: Função BeginMethodEnumeration (referência de API não gerenciada)
description: A função BeginMethodEnumeration inicia uma enumeração dos métodos do objeto
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ef53acdfa06b0c2be9d2aa55e89ce8fa34dfb0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761743"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="6b186-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="6b186-103">BeginEnumeration function</span></span>
<span data-ttu-id="6b186-104">Inicia uma enumeração dos métodos disponíveis para o objeto.</span><span class="sxs-lookup"><span data-stu-id="6b186-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6b186-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b186-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="6b186-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b186-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6b186-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="6b186-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6b186-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="6b186-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="6b186-109">[in] Zero (0) para todos os métodos, ou um sinalizador que especifica o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="6b186-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="6b186-110">Os seguintes sinalizadores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="6b186-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="6b186-111">Constante</span><span class="sxs-lookup"><span data-stu-id="6b186-111">Constant</span></span>  |<span data-ttu-id="6b186-112">Valor</span><span class="sxs-lookup"><span data-stu-id="6b186-112">Value</span></span>  |<span data-ttu-id="6b186-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b186-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="6b186-114">0x10</span><span class="sxs-lookup"><span data-stu-id="6b186-114">0x10</span></span> | <span data-ttu-id="6b186-115">Limite a enumeração para os métodos que são definidos na própria classe.</span><span class="sxs-lookup"><span data-stu-id="6b186-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="6b186-116">0x20</span><span class="sxs-lookup"><span data-stu-id="6b186-116">0x20</span></span> | <span data-ttu-id="6b186-117">Limite a enumeração para propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="6b186-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="6b186-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6b186-118">Return value</span></span>

<span data-ttu-id="6b186-119">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="6b186-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6b186-120">Constante</span><span class="sxs-lookup"><span data-stu-id="6b186-120">Constant</span></span>  |<span data-ttu-id="6b186-121">Valor</span><span class="sxs-lookup"><span data-stu-id="6b186-121">Value</span></span>  |<span data-ttu-id="6b186-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b186-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6b186-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6b186-123">0x80041008</span></span> | <span data-ttu-id="6b186-124">`lEnnumFlags` é diferente de zero e não é um dos sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="6b186-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6b186-125">0</span><span class="sxs-lookup"><span data-stu-id="6b186-125">0</span></span> | <span data-ttu-id="6b186-126">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6b186-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6b186-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b186-127">Remarks</span></span>

<span data-ttu-id="6b186-128">Essa função encapsula uma chamada para o [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) método.</span><span class="sxs-lookup"><span data-stu-id="6b186-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="6b186-129">Somente há suporte para esta chamada de método se o objeto atual é uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="6b186-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="6b186-130">Manipulação de método não está disponível no [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiros que apontam para as instâncias.</span><span class="sxs-lookup"><span data-stu-id="6b186-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="6b186-131">A ordem na qual os métodos são enumerados é garantida para ser invariável para uma determinada instância do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="6b186-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="6b186-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b186-132">Requirements</span></span>  
 <span data-ttu-id="6b186-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b186-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b186-134">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6b186-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6b186-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6b186-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b186-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b186-136">See also</span></span>

- [<span data-ttu-id="6b186-137">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="6b186-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
