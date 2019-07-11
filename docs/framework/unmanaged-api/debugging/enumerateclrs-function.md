---
title: Função EnumerateCLRs
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae668a40ba1510e0e3d4f509643022ebe822a4f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738943"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="fe285-102">Função EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="fe285-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="fe285-103">Fornece um mecanismo para enumerar os CLRs em um processo.</span><span class="sxs-lookup"><span data-stu-id="fe285-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe285-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe285-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe285-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe285-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="fe285-106">[in] Identificador de processo do processo do qual serão enumeradas CLRs carregados.</span><span class="sxs-lookup"><span data-stu-id="fe285-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="fe285-107">[out] Ponteiro para uma matriz que contém os identificadores de eventos que são usados para continuar a inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="fe285-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="fe285-108">Cada alça na matriz não é garantida para ser válido.</span><span class="sxs-lookup"><span data-stu-id="fe285-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="fe285-109">Se é válido, o identificador é a ser usado como o evento de inicialização de continuar para o tempo de execução correspondente localizado no mesmo índice de `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="fe285-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="fe285-110">[out] Ponteiro para uma matriz de cadeias de caracteres que especificam caminhos completos para CLRs carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="fe285-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="fe285-111">[out] Ponteiro para um DWORD que contém o comprimento de tamanhos iguais `ppHandleArrayOut` e `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="fe285-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe285-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fe285-112">Return Value</span></span>  
 <span data-ttu-id="fe285-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe285-113">S_OK</span></span>  
 <span data-ttu-id="fe285-114">O número de CLRs no processo com êxito foi determinado e o identificador correspondente e matrizes de caminho foram preenchidos corretamente.</span><span class="sxs-lookup"><span data-stu-id="fe285-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="fe285-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fe285-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="fe285-116">Tanto `ppHandleArrayOut` ou `ppStringArrayOut` for nulo, ou `pdwArrayLengthOut` é nulo.</span><span class="sxs-lookup"><span data-stu-id="fe285-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="fe285-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fe285-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="fe285-118">A função não é possível alocar memória suficiente para as matrizes de identificador e o caminho.</span><span class="sxs-lookup"><span data-stu-id="fe285-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="fe285-119">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="fe285-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fe285-120">Não é possível enumerar CLRs carregados.</span><span class="sxs-lookup"><span data-stu-id="fe285-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe285-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe285-121">Remarks</span></span>  
 <span data-ttu-id="fe285-122">Para um processo de destino que é identificado por `debuggeePID`, a função retorna uma matriz de caminhos `ppStringArrayOut`, para CLRs carregados no processo; uma matriz de identificadores de eventos, `ppHandleArrayOut`, que pode conter um evento de inicialização de continuar para o CLR no mesmo índice; e o tamanho das matrizes, `pdwArrayLengthOut`, que especifica o número de CLRs que são carregados.</span><span class="sxs-lookup"><span data-stu-id="fe285-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="fe285-123">No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="fe285-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="fe285-124">A memória para `ppHandleArrayOut` e `ppStringArrayOut` são alocados por essa função.</span><span class="sxs-lookup"><span data-stu-id="fe285-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="fe285-125">Para liberar a memória alocada, você deve chamar [função CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="fe285-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="fe285-126">Essa função pode ser chamada com ambos os parâmetros de matriz definidos como nulo para não retornar a contagem de CLRs no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="fe285-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="fe285-127">Essa contagem, um chamador pode inferir o tamanho do buffer que será criado: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="fe285-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe285-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe285-128">Requirements</span></span>  
 <span data-ttu-id="fe285-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe285-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe285-130">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="fe285-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="fe285-131">**Biblioteca:** dbgshim</span><span class="sxs-lookup"><span data-stu-id="fe285-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="fe285-132">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="fe285-132">**.NET Framework Versions:** 3.5 SP1</span></span>
