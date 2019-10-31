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
ms.openlocfilehash: a27787052757098d4edb2d8516e22d8a03b7009a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138787"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="c6bc4-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="c6bc4-103">BeginEnumeration function</span></span>
<span data-ttu-id="c6bc4-104">Inicia uma enumeração dos métodos disponíveis para o objeto.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="c6bc4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6bc4-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="c6bc4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6bc4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c6bc4-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c6bc4-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="c6bc4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="c6bc4-109">no Zero (0) para todos os métodos ou um sinalizador que especifica o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="c6bc4-110">Os sinalizadores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c6bc4-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="c6bc4-111">Constante</span><span class="sxs-lookup"><span data-stu-id="c6bc4-111">Constant</span></span>  |<span data-ttu-id="c6bc4-112">Valor</span><span class="sxs-lookup"><span data-stu-id="c6bc4-112">Value</span></span>  |<span data-ttu-id="c6bc4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6bc4-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c6bc4-114">0x10</span><span class="sxs-lookup"><span data-stu-id="c6bc4-114">0x10</span></span> | <span data-ttu-id="c6bc4-115">Limitar a enumeração a métodos que são definidos na própria classe.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="c6bc4-116">0x20</span><span class="sxs-lookup"><span data-stu-id="c6bc4-116">0x20</span></span> | <span data-ttu-id="c6bc4-117">Limite a enumeração a propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="c6bc4-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c6bc4-118">Return value</span></span>

<span data-ttu-id="c6bc4-119">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c6bc4-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c6bc4-120">Constante</span><span class="sxs-lookup"><span data-stu-id="c6bc4-120">Constant</span></span>  |<span data-ttu-id="c6bc4-121">Valor</span><span class="sxs-lookup"><span data-stu-id="c6bc4-121">Value</span></span>  |<span data-ttu-id="c6bc4-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6bc4-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c6bc4-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c6bc4-123">0x80041008</span></span> | <span data-ttu-id="c6bc4-124">`lEnnumFlags` não é zero e não é um dos sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c6bc4-125">0</span><span class="sxs-lookup"><span data-stu-id="c6bc4-125">0</span></span> | <span data-ttu-id="c6bc4-126">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c6bc4-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6bc4-127">Remarks</span></span>

<span data-ttu-id="c6bc4-128">Essa função encapsula uma chamada para o método [IWbemClassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="c6bc4-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="c6bc4-129">Essa chamada de método só terá suporte se o objeto atual for uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="c6bc4-130">A manipulação de método não está disponível em ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias.</span><span class="sxs-lookup"><span data-stu-id="c6bc4-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="c6bc4-131">A ordem na qual os métodos são enumerados é garantida como invariável para uma determinada instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="c6bc4-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="c6bc4-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6bc4-132">Requirements</span></span>  
 <span data-ttu-id="c6bc4-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6bc4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6bc4-134">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="c6bc4-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c6bc4-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c6bc4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6bc4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6bc4-136">See also</span></span>

- [<span data-ttu-id="c6bc4-137">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c6bc4-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
