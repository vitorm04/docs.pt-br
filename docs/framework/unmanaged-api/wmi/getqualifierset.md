---
title: Função getqualifierset (referência de API não gerenciada)
description: A função getqualificador recupera o qualificador definido para uma classe ou instância.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 845d5ea93a06859840c87c65b415ead0f846d538
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798468"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="53570-103">Função getqualifierset</span><span class="sxs-lookup"><span data-stu-id="53570-103">GetQualifierSet function</span></span>
<span data-ttu-id="53570-104">Recupera o qualificador definido para uma instância da classe ou uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="53570-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="53570-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53570-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="53570-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53570-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="53570-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="53570-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="53570-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="53570-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="53570-109">fora Recebe o ponteiro de interface que permite o acesso aos qualificadores do objeto de classe.</span><span class="sxs-lookup"><span data-stu-id="53570-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="53570-110">`ppQualSet` não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="53570-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="53570-111">Se ocorrer um erro, um novo objeto não será retornado e o ponteiro será deixado como não modificado.</span><span class="sxs-lookup"><span data-stu-id="53570-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="53570-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="53570-112">Return value</span></span>

<span data-ttu-id="53570-113">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="53570-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="53570-114">Constante</span><span class="sxs-lookup"><span data-stu-id="53570-114">Constant</span></span>  |<span data-ttu-id="53570-115">Valor</span><span class="sxs-lookup"><span data-stu-id="53570-115">Value</span></span>  |<span data-ttu-id="53570-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="53570-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="53570-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="53570-117">0x80041001</span></span> | <span data-ttu-id="53570-118">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="53570-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="53570-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="53570-119">0x80041002</span></span> | <span data-ttu-id="53570-120">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="53570-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="53570-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="53570-121">0x80041006</span></span> | <span data-ttu-id="53570-122">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="53570-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="53570-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="53570-123">0x80041008</span></span> | <span data-ttu-id="53570-124">Um parâmetro é `null`.</span><span class="sxs-lookup"><span data-stu-id="53570-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="53570-125">0</span><span class="sxs-lookup"><span data-stu-id="53570-125">0</span></span> | <span data-ttu-id="53570-126">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="53570-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="53570-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="53570-127">Remarks</span></span>

<span data-ttu-id="53570-128">Essa função encapsula uma chamada para o método [IWbemClassObject:: Getqualifierset](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="53570-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="53570-129">O [ponteiro IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permite que o chamador adicione, edite ou exclua esses qualificadores.</span><span class="sxs-lookup"><span data-stu-id="53570-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="53570-130">Esses qualificadores adicionados, editados ou excluídos se aplicam a toda a definição de instância ou classe.</span><span class="sxs-lookup"><span data-stu-id="53570-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="53570-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53570-131">Requirements</span></span>  
<span data-ttu-id="53570-132">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53570-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53570-133">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="53570-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="53570-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53570-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53570-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53570-135">See also</span></span>

- [<span data-ttu-id="53570-136">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="53570-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
