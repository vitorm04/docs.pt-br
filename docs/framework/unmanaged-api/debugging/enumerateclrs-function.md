---
title: "Função EnumerateCLRs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EnumerateCLRs
api_location: dbgshim.dll
api_type: COM
f1_keywords: EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4d4c9502b52f521b9faa8e8d352f0721af68314
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="0b70e-102">Função EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="0b70e-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="0b70e-103">Fornece um mecanismo para enumerar CLRs em um processo.</span><span class="sxs-lookup"><span data-stu-id="0b70e-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b70e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b70e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b70e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b70e-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="0b70e-106">[in] Identificador de processo do processo do qual serão enumeradas CLRs carregados.</span><span class="sxs-lookup"><span data-stu-id="0b70e-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="0b70e-107">[out] Ponteiro para uma matriz que contém os identificadores de eventos que são usados para continuar a inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="0b70e-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="0b70e-108">Não há garantia de que cada alça na matriz de ser válido.</span><span class="sxs-lookup"><span data-stu-id="0b70e-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="0b70e-109">Se é válido, o identificador é a ser usado como o evento de inicialização de continuar para o tempo de execução correspondente localizado no mesmo índice de `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="0b70e-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="0b70e-110">[out] Ponteiro para uma matriz de cadeias de caracteres que especificam caminhos completos para CLRs carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="0b70e-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="0b70e-111">[out] Ponteiro para uma DWORD que contém o comprimento de tamanho igual `ppHandleArrayOut` e `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="0b70e-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b70e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0b70e-112">Return Value</span></span>  
 <span data-ttu-id="0b70e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b70e-113">S_OK</span></span>  
 <span data-ttu-id="0b70e-114">O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.</span><span class="sxs-lookup"><span data-stu-id="0b70e-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="0b70e-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0b70e-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="0b70e-116">O `ppHandleArrayOut` ou `ppStringArrayOut` é nulo, ou `pdwArrayLengthOut` é nulo.</span><span class="sxs-lookup"><span data-stu-id="0b70e-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="0b70e-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b70e-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="0b70e-118">A função é não é possível alocar memória suficiente para as matrizes de identificador e o caminho.</span><span class="sxs-lookup"><span data-stu-id="0b70e-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="0b70e-119">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="0b70e-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0b70e-120">Não é possível enumerar CLRs carregados.</span><span class="sxs-lookup"><span data-stu-id="0b70e-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b70e-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b70e-121">Remarks</span></span>  
 <span data-ttu-id="0b70e-122">Para um processo de destino que é identificado pelo `debuggeePID`, a função retorna uma matriz de caminhos, `ppStringArrayOut`, CLRs carregados no processo; uma matriz de identificadores de evento, `ppHandleArrayOut`, que pode conter um evento de inicialização de continuar para o CLR no mesmo índice; e o tamanho das matrizes, `pdwArrayLengthOut`, que especifica o número de CLRs que são carregados.</span><span class="sxs-lookup"><span data-stu-id="0b70e-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="0b70e-123">No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="0b70e-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="0b70e-124">A memória para `ppHandleArrayOut` e `ppStringArrayOut` são alocados por essa função.</span><span class="sxs-lookup"><span data-stu-id="0b70e-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="0b70e-125">Para liberar a memória alocada, você deve chamar [função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="0b70e-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="0b70e-126">Esta função pode ser chamada com ambos os parâmetros de matriz definidos como null para retornar a contagem de CLRs no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0b70e-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="0b70e-127">Essa contagem, um chamador pode inferir o tamanho do buffer que será criado: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="0b70e-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b70e-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b70e-128">Requirements</span></span>  
 <span data-ttu-id="0b70e-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b70e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b70e-130">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="0b70e-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="0b70e-131">**Biblioteca:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="0b70e-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="0b70e-132">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="0b70e-132">**.NET Framework Versions:** 3.5 SP1</span></span>
