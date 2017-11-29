---
title: "Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0c4192c94d70bd9406607d645716e4dd6f8b957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="30465-102">Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="30465-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="30465-103">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="30465-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30465-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30465-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30465-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30465-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="30465-106">[out] Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém o mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="30465-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="30465-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="30465-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30465-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="30465-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30465-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30465-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="30465-110">O mapa consiste em duas seções de nível superior:</span><span class="sxs-lookup"><span data-stu-id="30465-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="30465-111">Um [diretório](#Directory) que contém os endereços virtuais relativos (RVA) de todos os dicionários incluídos neste mapa.</span><span class="sxs-lookup"><span data-stu-id="30465-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="30465-112">Um byte alinhado [heap](#Heap) que contém informações de instanciação do objeto.</span><span class="sxs-lookup"><span data-stu-id="30465-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="30465-113">Ele inicia imediatamente após a última entrada de diretório.</span><span class="sxs-lookup"><span data-stu-id="30465-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="30465-114">O diretório</span><span class="sxs-lookup"><span data-stu-id="30465-114">The Directory</span></span>  
 <span data-ttu-id="30465-115">Cada entrada no diretório refere-se a um deslocamento dentro de heap; ou seja, é um deslocamento relativo ao início da pilha.</span><span class="sxs-lookup"><span data-stu-id="30465-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="30465-116">O valor de entradas individuais não é necessariamente exclusivo; é possível que várias entradas de diretório apontar para o mesmo deslocamento no heap.</span><span class="sxs-lookup"><span data-stu-id="30465-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="30465-117">A parte do diretório do mapa do dicionário genérico tem a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="30465-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="30465-118">Os primeiros 4 bytes contém o número de entradas de dicionário (ou seja, o número de endereços virtuais relativos no dicionário).</span><span class="sxs-lookup"><span data-stu-id="30465-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="30465-119">Chamaremos esse valor como *N*. Se o bit alto for definido, as entradas são classificadas por endereço virtual relativo em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="30465-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="30465-120">O *N* execute as entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="30465-120">The *N* directory entries follow.</span></span> <span data-ttu-id="30465-121">Cada entrada consiste em 8 bytes, de dois segmentos de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="30465-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="30465-122">Bytes de 0 a 3: RVA; endereço virtual relativo do dicionário.</span><span class="sxs-lookup"><span data-stu-id="30465-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="30465-123">Bytes de 4 a 7: deslocamento; um deslocamento em relação ao início da pilha.</span><span class="sxs-lookup"><span data-stu-id="30465-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="30465-124">O Heap</span><span class="sxs-lookup"><span data-stu-id="30465-124">The Heap</span></span>  
 <span data-ttu-id="30465-125">Tamanho do heap pode ser calculado por um leitor de fluxo subtraindo-se o comprimento do fluxo de tamanho de diretório + 4.</span><span class="sxs-lookup"><span data-stu-id="30465-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="30465-126">Em outras palavras:</span><span class="sxs-lookup"><span data-stu-id="30465-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="30465-127">onde é o tamanho da pasta `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="30465-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="30465-128">O formato para cada item de informação de instanciação no heap é:</span><span class="sxs-lookup"><span data-stu-id="30465-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="30465-129">O comprimento deste item de informações de instanciação em bytes, no formato compactado de metadados ECMA.</span><span class="sxs-lookup"><span data-stu-id="30465-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="30465-130">O valor exclui essas informações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="30465-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="30465-131">O número de tipos de instanciação genérica ou *T*, em formato compactado de metadados ECMA.</span><span class="sxs-lookup"><span data-stu-id="30465-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="30465-132">*T* tipos, cada um representado no formato de assinatura de tipo ECMA.</span><span class="sxs-lookup"><span data-stu-id="30465-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="30465-133">A inclusão do comprimento de cada elemento de heap ativa a classificação simples da seção de diretório sem afetar o heap.</span><span class="sxs-lookup"><span data-stu-id="30465-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30465-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30465-134">Requirements</span></span>  
 <span data-ttu-id="30465-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30465-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30465-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30465-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30465-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30465-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30465-138">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30465-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30465-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30465-139">See Also</span></span>  
 [<span data-ttu-id="30465-140">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="30465-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="30465-141">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="30465-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
