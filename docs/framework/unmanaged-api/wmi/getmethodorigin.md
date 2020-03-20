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
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176793"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="fc1a7-103">Função GetMethodOrigin</span><span class="sxs-lookup"><span data-stu-id="fc1a7-103">GetMethodOrigin function</span></span>
<span data-ttu-id="fc1a7-104">Determina a classe na qual um método é declarado.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fc1a7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc1a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="fc1a7-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc1a7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fc1a7-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fc1a7-108">[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="fc1a7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="fc1a7-109">[em] O nome do método para o objeto cuja classe de possuir está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="fc1a7-110">[fora] Recebe o nome da classe que possui o método.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc1a7-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fc1a7-111">Return value</span></span>

<span data-ttu-id="fc1a7-112">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="fc1a7-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fc1a7-113">Constante</span><span class="sxs-lookup"><span data-stu-id="fc1a7-113">Constant</span></span>  |<span data-ttu-id="fc1a7-114">Valor</span><span class="sxs-lookup"><span data-stu-id="fc1a7-114">Value</span></span>  |<span data-ttu-id="fc1a7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc1a7-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="fc1a7-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="fc1a7-116">0x80041002</span></span> | <span data-ttu-id="fc1a7-117">O método especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fc1a7-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fc1a7-118">0x80041008</span></span> | <span data-ttu-id="fc1a7-119">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fc1a7-120">0</span><span class="sxs-lookup"><span data-stu-id="fc1a7-120">0</span></span> | <span data-ttu-id="fc1a7-121">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fc1a7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc1a7-122">Remarks</span></span>

<span data-ttu-id="fc1a7-123">Esta função envolve uma chamada para o método [IWbemClassObject::GetMethodOrigin.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)</span><span class="sxs-lookup"><span data-stu-id="fc1a7-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="fc1a7-124">Como uma classe pode herdar métodos de uma ou mais classes básicas, os desenvolvedores muitas vezes querem determinar a classe na qual um determinado método é definido.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="fc1a7-125">O `pstrClassName` parâmetro não deve apontar `BSTR` para um válido antes `out` que a função seja chamada porque este é um parâmetro; este ponteiro não é desalocado após o retorno da função.</span><span class="sxs-lookup"><span data-stu-id="fc1a7-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc1a7-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc1a7-126">Requirements</span></span>  
<span data-ttu-id="fc1a7-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc1a7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc1a7-128">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fc1a7-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fc1a7-129">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fc1a7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1a7-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc1a7-130">See also</span></span>

- [<span data-ttu-id="fc1a7-131">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="fc1a7-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
