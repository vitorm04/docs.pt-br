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
ms.openlocfilehash: d87627b8bb3414860d994273396dbb4e64acdea7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="beginenumeration-function"></a><span data-ttu-id="502f2-103">Função BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="502f2-103">BeginEnumeration function</span></span>
<span data-ttu-id="502f2-104">Inicia uma enumeração dos métodos disponíveis para o objeto.</span><span class="sxs-lookup"><span data-stu-id="502f2-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="502f2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="502f2-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="502f2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="502f2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="502f2-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="502f2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="502f2-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="502f2-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="502f2-109">[in] Zero (0) para todos os métodos, ou um sinalizador que especifica o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="502f2-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="502f2-110">Os seguintes sinalizadores são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="502f2-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="502f2-111">Constante</span><span class="sxs-lookup"><span data-stu-id="502f2-111">Constant</span></span>  |<span data-ttu-id="502f2-112">Valor</span><span class="sxs-lookup"><span data-stu-id="502f2-112">Value</span></span>  |<span data-ttu-id="502f2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="502f2-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="502f2-114">0x10</span><span class="sxs-lookup"><span data-stu-id="502f2-114">0x10</span></span> | <span data-ttu-id="502f2-115">Limite de enumeração para os métodos que estão definidos na classe em si.</span><span class="sxs-lookup"><span data-stu-id="502f2-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="502f2-116">0x20</span><span class="sxs-lookup"><span data-stu-id="502f2-116">0x20</span></span> | <span data-ttu-id="502f2-117">Limite a enumeração de propriedades que são herdadas de classes base.</span><span class="sxs-lookup"><span data-stu-id="502f2-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="502f2-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="502f2-118">Return value</span></span>

<span data-ttu-id="502f2-119">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="502f2-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="502f2-120">Constante</span><span class="sxs-lookup"><span data-stu-id="502f2-120">Constant</span></span>  |<span data-ttu-id="502f2-121">Valor</span><span class="sxs-lookup"><span data-stu-id="502f2-121">Value</span></span>  |<span data-ttu-id="502f2-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="502f2-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="502f2-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="502f2-123">0x80041008</span></span> | <span data-ttu-id="502f2-124">`lEnnumFlags` é diferente de zero e não é um dos sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="502f2-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="502f2-125">0</span><span class="sxs-lookup"><span data-stu-id="502f2-125">0</span></span> | <span data-ttu-id="502f2-126">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="502f2-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="502f2-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="502f2-127">Remarks</span></span>

<span data-ttu-id="502f2-128">Essa função encapsula uma chamada para o [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="502f2-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="502f2-129">Somente há suporte para esta chamada de método se o objeto atual é uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="502f2-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="502f2-130">Manipulação de método não está disponível no [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponteiros que apontam para as instâncias.</span><span class="sxs-lookup"><span data-stu-id="502f2-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="502f2-131">A ordem na qual os métodos são enumerados é garantida para ser invariável para uma determinada instância do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="502f2-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="502f2-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="502f2-132">Requirements</span></span>  
 <span data-ttu-id="502f2-133">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="502f2-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="502f2-134">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="502f2-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="502f2-135">**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="502f2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502f2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="502f2-136">See also</span></span>  
[<span data-ttu-id="502f2-137">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="502f2-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
