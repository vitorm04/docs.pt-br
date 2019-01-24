---
title: Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5ed689ad7c456121f7687e7df09eca6c7ea617d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502553"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="8ca6c-102">Método ICorDebugSymbolProvider2::GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="8ca6c-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="8ca6c-103">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca6c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ca6c-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ca6c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ca6c-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="8ca6c-106">[out] Um ponteiro para o endereço de um [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objeto que contém o mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="8ca6c-107">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca6c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ca6c-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ca6c-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="8ca6c-110">O mapa consiste em duas seções de nível superior:</span><span class="sxs-lookup"><span data-stu-id="8ca6c-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="8ca6c-111">Um [directory](#Directory) que contém os endereços de virtuais relativos (RVA) de todos os dicionários incluídos neste mapa.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="8ca6c-112">Um byte alinhado [heap](#Heap) que contém informações de instanciação do objeto.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="8ca6c-113">Ele começa imediatamente após a última entrada de diretório.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="8ca6c-114">O diretório</span><span class="sxs-lookup"><span data-stu-id="8ca6c-114">The Directory</span></span>  
 <span data-ttu-id="8ca6c-115">Cada entrada no diretório refere-se a um deslocamento dentro de heap; ou seja, é um deslocamento relativo ao início do heap.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="8ca6c-116">O valor de entradas individuais não é necessariamente exclusivo; é possível que várias entradas de diretório apontar para o mesmo deslocamento no heap.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="8ca6c-117">A parte do diretório do mapa do dicionário genérico tem a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="8ca6c-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="8ca6c-118">Os primeiros 4 bytes contém o número de entradas de dicionário (ou seja, o número de endereços virtuais no dicionário).</span><span class="sxs-lookup"><span data-stu-id="8ca6c-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="8ca6c-119">Vamos nos referir a esse valor como *N*. Se o bit alto for definido, as entradas são classificadas pelo endereço virtual relativo em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="8ca6c-120">O *N* execute as entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-120">The *N* directory entries follow.</span></span> <span data-ttu-id="8ca6c-121">Cada entrada consiste em 8 bytes, de dois segmentos de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="8ca6c-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="8ca6c-122">Bytes de 0 a 3: RVA; endereço virtual relativo do dicionário.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="8ca6c-123">Bytes de 4 a 7: Deslocamento; um deslocamento relativo para o início do heap.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="8ca6c-124">O Heap</span><span class="sxs-lookup"><span data-stu-id="8ca6c-124">The Heap</span></span>  
 <span data-ttu-id="8ca6c-125">Tamanho do heap pode ser calculado por um leitor de fluxo, subtraindo o tamanho do fluxo de tamanho de diretório + 4.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="8ca6c-126">Em outras palavras:</span><span class="sxs-lookup"><span data-stu-id="8ca6c-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="8ca6c-127">onde o tamanho do diretório é `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="8ca6c-128">O formato para cada item de informações de instanciação no heap é:</span><span class="sxs-lookup"><span data-stu-id="8ca6c-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="8ca6c-129">O comprimento deste item de informações de instanciação em bytes, no formato compactado de metadados ECMA.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="8ca6c-130">O valor exclui essas informações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="8ca6c-131">O número de tipos de instanciação genérica, ou *T*, em formato compactado de metadados ECMA.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="8ca6c-132">*T* tipos, cada uma representada em formato de assinatura de tipo ECMA.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="8ca6c-133">A inclusão do comprimento de cada elemento de heap ativa a classificação simples da seção de diretório sem afetar o heap.</span><span class="sxs-lookup"><span data-stu-id="8ca6c-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca6c-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ca6c-134">Requirements</span></span>  
 <span data-ttu-id="8ca6c-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca6c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca6c-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ca6c-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ca6c-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ca6c-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ca6c-138">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca6c-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca6c-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ca6c-139">See also</span></span>
- [<span data-ttu-id="8ca6c-140">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="8ca6c-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="8ca6c-141">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8ca6c-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
