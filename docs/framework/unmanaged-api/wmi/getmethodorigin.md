---
title: Função GetMethodOrigin (referência de API não gerenciada)
description: A função GetMethodOrigin determina a classe em que um método é declarado.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1cc754fcf7d1defa815bb0a74b7c2b4a6909478
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539322"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="5281a-103">Função GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="5281a-103">GetMethodOrigin function</span></span>
<span data-ttu-id="5281a-104">Determina a classe na qual um método é declarado.</span><span class="sxs-lookup"><span data-stu-id="5281a-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="5281a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5281a-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="5281a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5281a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5281a-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="5281a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5281a-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="5281a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="5281a-109">[in] O nome do método para o objeto cuja classe proprietária está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="5281a-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="5281a-110">[out] Recebe o nome da classe que possui o método.</span><span class="sxs-lookup"><span data-stu-id="5281a-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="5281a-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5281a-111">Return value</span></span>

<span data-ttu-id="5281a-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="5281a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5281a-113">Constante</span><span class="sxs-lookup"><span data-stu-id="5281a-113">Constant</span></span>  |<span data-ttu-id="5281a-114">Valor</span><span class="sxs-lookup"><span data-stu-id="5281a-114">Value</span></span>  |<span data-ttu-id="5281a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5281a-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="5281a-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5281a-116">0x80041002</span></span> | <span data-ttu-id="5281a-117">O método especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="5281a-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5281a-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5281a-118">0x80041008</span></span> | <span data-ttu-id="5281a-119">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="5281a-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5281a-120">0</span><span class="sxs-lookup"><span data-stu-id="5281a-120">0</span></span> | <span data-ttu-id="5281a-121">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5281a-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5281a-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5281a-122">Remarks</span></span>

<span data-ttu-id="5281a-123">Essa função encapsula uma chamada para o [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) método.</span><span class="sxs-lookup"><span data-stu-id="5281a-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="5281a-124">Porque uma classe pode herdar a métodos de uma ou mais classes base, os desenvolvedores geralmente querem determinar a classe na qual um determinado método está definido.</span><span class="sxs-lookup"><span data-stu-id="5281a-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="5281a-125">O `pstrClassName` parâmetro não deve apontar para um válido `BSTR` antes da função é chamada como esta é uma `out` parâmetro; esse ponteiro não é desalocado depois que a função retorna.</span><span class="sxs-lookup"><span data-stu-id="5281a-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="5281a-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5281a-126">Requirements</span></span>  
<span data-ttu-id="5281a-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5281a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5281a-128">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5281a-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5281a-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5281a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5281a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5281a-130">See also</span></span>  
[<span data-ttu-id="5281a-131">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="5281a-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
