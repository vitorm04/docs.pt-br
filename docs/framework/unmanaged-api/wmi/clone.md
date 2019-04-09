---
title: Função clone (referência de API não gerenciada)
description: A função de Clone retorna um novo objeto que é um clone completo da atual.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf9cca10a580af7991889de6993e931347fc27ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120947"
---
# <a name="clone-function"></a><span data-ttu-id="bb537-103">Função Clone</span><span class="sxs-lookup"><span data-stu-id="bb537-103">Clone function</span></span>
<span data-ttu-id="bb537-104">Retorna um novo objeto que é uma cópia completa do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="bb537-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bb537-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb537-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="bb537-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb537-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bb537-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="bb537-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bb537-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="bb537-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="bb537-109">[out] Um novo objeto que é uma completa solitário de `ptr`.</span><span class="sxs-lookup"><span data-stu-id="bb537-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="bb537-110">Esse argumento não pode ser `null` se ela recebe a cópia do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="bb537-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb537-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bb537-111">Return value</span></span>

<span data-ttu-id="bb537-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="bb537-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bb537-113">Constante</span><span class="sxs-lookup"><span data-stu-id="bb537-113">Constant</span></span>  |<span data-ttu-id="bb537-114">Valor</span><span class="sxs-lookup"><span data-stu-id="bb537-114">Value</span></span>  |<span data-ttu-id="bb537-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb537-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="bb537-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bb537-116">0x80041001</span></span> | <span data-ttu-id="bb537-117">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="bb537-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bb537-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bb537-118">0x80041008</span></span> | `null` <span data-ttu-id="bb537-119">foi especificado como um parâmetro, e não é permitido nesse uso.</span><span class="sxs-lookup"><span data-stu-id="bb537-119">was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bb537-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bb537-120">0x80041006</span></span> | <span data-ttu-id="bb537-121">Não há memória suficiente está disponível para clonar o objeto.</span><span class="sxs-lookup"><span data-stu-id="bb537-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bb537-122">0</span><span class="sxs-lookup"><span data-stu-id="bb537-122">0</span></span> | <span data-ttu-id="bb537-123">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bb537-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bb537-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb537-124">Remarks</span></span>

<span data-ttu-id="bb537-125">Essa função encapsula uma chamada para o [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) método.</span><span class="sxs-lookup"><span data-stu-id="bb537-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="bb537-126">O objeto clonado é um objeto COM que tem uma contagem de referência de 1.</span><span class="sxs-lookup"><span data-stu-id="bb537-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb537-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb537-127">Requirements</span></span>  
 <span data-ttu-id="bb537-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb537-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb537-129">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bb537-129">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="bb537-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bb537-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb537-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb537-131">See also</span></span>

- [<span data-ttu-id="bb537-132">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bb537-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
