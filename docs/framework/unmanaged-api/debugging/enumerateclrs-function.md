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
ms.openlocfilehash: 1f33fb98712939d1e687798547b784819f164d63
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860730"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="c3c50-102">Função EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="c3c50-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="c3c50-103">Fornece um mecanismo para enumerar o CLRs em um processo.</span><span class="sxs-lookup"><span data-stu-id="c3c50-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3c50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3c50-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3c50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3c50-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="c3c50-106">no Identificador do processo do qual o CLRs carregado será enumerado.</span><span class="sxs-lookup"><span data-stu-id="c3c50-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="c3c50-107">fora Ponteiro para uma matriz que contém identificadores de eventos que são usados para continuar uma inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="c3c50-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="c3c50-108">Não há garantia de que cada identificador na matriz seja válido.</span><span class="sxs-lookup"><span data-stu-id="c3c50-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="c3c50-109">Se for válido, o identificador será usado como o evento continue-Startup para o tempo de execução correspondente localizado no mesmo índice de `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="c3c50-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="c3c50-110">fora Ponteiro para uma matriz de cadeias de caracteres que especificam caminhos completos para CLRs carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="c3c50-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="c3c50-111">fora Ponteiro para um DWORD que contém o comprimento do tamanho igualmente `ppHandleArrayOut` e. `pdwArrayLengthOut`</span><span class="sxs-lookup"><span data-stu-id="c3c50-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3c50-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c3c50-112">Return Value</span></span>  
 <span data-ttu-id="c3c50-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3c50-113">S_OK</span></span>  
 <span data-ttu-id="c3c50-114">O número de CLRs no processo foi determinado com êxito e as matrizes de identificador e caminho correspondentes foram preenchidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="c3c50-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="c3c50-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c3c50-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="c3c50-116">`ppHandleArrayOut` Or `ppStringArrayOut` é nulo ou `pdwArrayLengthOut` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c3c50-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="c3c50-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c3c50-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="c3c50-118">A função não pode alocar memória suficiente para as matrizes de identificador e caminho.</span><span class="sxs-lookup"><span data-stu-id="c3c50-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="c3c50-119">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="c3c50-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c3c50-120">Não é possível enumerar o CLRs carregado.</span><span class="sxs-lookup"><span data-stu-id="c3c50-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3c50-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3c50-121">Remarks</span></span>  
 <span data-ttu-id="c3c50-122">Para um processo de destino identificado pelo `debuggeePID`, a função retorna uma matriz de caminhos, `ppStringArrayOut`, para CLRs carregada no processo; uma matriz de identificadores de `ppHandleArrayOut`eventos,, que pode conter um evento continue-Startup para o CLR no mesmo índice; e o tamanho das matrizes, `pdwArrayLengthOut`, que especifica o número de CLRs que são carregadas.</span><span class="sxs-lookup"><span data-stu-id="c3c50-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="c3c50-123">No sistema operacional Windows, `debuggeePID` o mapeia para um identificador de processo do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c3c50-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="c3c50-124">A memória para `ppHandleArrayOut` e `ppStringArrayOut` são alocadas por essa função.</span><span class="sxs-lookup"><span data-stu-id="c3c50-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="c3c50-125">Para liberar a memória alocada, você deve chamar a [função CloseCLREnumeration](closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="c3c50-125">To free the memory allocated, you must call [CloseCLREnumeration Function](closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="c3c50-126">Essa função pode ser chamada com ambos os parâmetros de matriz definidos como NULL para retornar a contagem de CLRs no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="c3c50-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="c3c50-127">A partir dessa contagem, um chamador pode inferir o tamanho do buffer que será criado: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="c3c50-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3c50-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3c50-128">Requirements</span></span>  
 <span data-ttu-id="c3c50-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3c50-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3c50-130">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="c3c50-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c3c50-131">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="c3c50-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c3c50-132">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c3c50-132">**.NET Framework Versions:** 3.5 SP1</span></span>
