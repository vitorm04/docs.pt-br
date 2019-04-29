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
ms.openlocfilehash: 193caa894b8697a65e8821c01a63dde9cc5b5ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608938"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="2ea30-103">Função GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="2ea30-103">GetMethodOrigin function</span></span>
<span data-ttu-id="2ea30-104">Determina a classe na qual um método é declarado.</span><span class="sxs-lookup"><span data-stu-id="2ea30-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="2ea30-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ea30-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="2ea30-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ea30-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2ea30-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="2ea30-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2ea30-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="2ea30-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="2ea30-109">[in] O nome do método para o objeto cuja classe proprietária está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="2ea30-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="2ea30-110">[out] Recebe o nome da classe que possui o método.</span><span class="sxs-lookup"><span data-stu-id="2ea30-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ea30-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2ea30-111">Return value</span></span>

<span data-ttu-id="2ea30-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2ea30-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2ea30-113">Constante</span><span class="sxs-lookup"><span data-stu-id="2ea30-113">Constant</span></span>  |<span data-ttu-id="2ea30-114">Valor</span><span class="sxs-lookup"><span data-stu-id="2ea30-114">Value</span></span>  |<span data-ttu-id="2ea30-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ea30-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="2ea30-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2ea30-116">0x80041002</span></span> | <span data-ttu-id="2ea30-117">O método especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="2ea30-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2ea30-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2ea30-118">0x80041008</span></span> | <span data-ttu-id="2ea30-119">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="2ea30-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2ea30-120">0</span><span class="sxs-lookup"><span data-stu-id="2ea30-120">0</span></span> | <span data-ttu-id="2ea30-121">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2ea30-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2ea30-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ea30-122">Remarks</span></span>

<span data-ttu-id="2ea30-123">Essa função encapsula uma chamada para o [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) método.</span><span class="sxs-lookup"><span data-stu-id="2ea30-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="2ea30-124">Porque uma classe pode herdar a métodos de uma ou mais classes base, os desenvolvedores geralmente querem determinar a classe na qual um determinado método está definido.</span><span class="sxs-lookup"><span data-stu-id="2ea30-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="2ea30-125">O `pstrClassName` parâmetro não deve apontar para um válido `BSTR` antes da função é chamada como esta é uma `out` parâmetro; esse ponteiro não é desalocado depois que a função retorna.</span><span class="sxs-lookup"><span data-stu-id="2ea30-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ea30-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ea30-126">Requirements</span></span>  
<span data-ttu-id="2ea30-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea30-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea30-128">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2ea30-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2ea30-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea30-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea30-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ea30-130">See also</span></span>

- [<span data-ttu-id="2ea30-131">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2ea30-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
