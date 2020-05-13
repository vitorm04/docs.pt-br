---
title: 'Método ICorDebugSymbolProvider2:: GetGenericDictionaryInfo'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: a6c32b72c5924399aeb13d56ddf9242fe7990f35
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379317"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="49127-102">Método ICorDebugSymbolProvider2:: GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="49127-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="49127-103">Recupera um mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="49127-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="49127-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49127-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="49127-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49127-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="49127-106">fora Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) que contém o mapa de dicionário genérico.</span><span class="sxs-lookup"><span data-stu-id="49127-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="49127-107">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="49127-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="49127-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="49127-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="49127-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49127-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="49127-110">O mapa consiste em duas seções de nível superior:</span><span class="sxs-lookup"><span data-stu-id="49127-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="49127-111">Um [diretório](#Directory) que contém os endereços virtuais relativos (RVA) de todos os dicionários incluídos neste mapa.</span><span class="sxs-lookup"><span data-stu-id="49127-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="49127-112">Um [heap](#Heap) alinhado em byte que contém informações de instanciação de objeto.</span><span class="sxs-lookup"><span data-stu-id="49127-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="49127-113">Ele começa imediatamente após a última entrada de diretório.</span><span class="sxs-lookup"><span data-stu-id="49127-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="49127-114">O diretório</span><span class="sxs-lookup"><span data-stu-id="49127-114">The Directory</span></span>

<span data-ttu-id="49127-115">Cada entrada no diretório refere-se a um deslocamento dentro do heap; ou seja, é um deslocamento relativo ao início do heap.</span><span class="sxs-lookup"><span data-stu-id="49127-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="49127-116">O valor de entradas individuais não é necessariamente exclusivo; é possível que várias entradas de diretório apontem para o mesmo deslocamento no heap.</span><span class="sxs-lookup"><span data-stu-id="49127-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="49127-117">A parte do diretório do mapa de dicionário genérico tem a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="49127-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="49127-118">Os quatro primeiros bytes contêm o número de entradas de dicionário (ou seja, o número de endereços virtuais relativos no dicionário).</span><span class="sxs-lookup"><span data-stu-id="49127-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="49127-119">Iremos nos referir a esse valor como *N*. Se o bit alto for definido, as entradas serão classificadas por endereço virtual relativo em ordem crescente.</span><span class="sxs-lookup"><span data-stu-id="49127-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="49127-120">As entradas *N* diretório seguem.</span><span class="sxs-lookup"><span data-stu-id="49127-120">The *N* directory entries follow.</span></span> <span data-ttu-id="49127-121">Cada entrada consiste em 8 bytes, em dois segmentos de 4 bytes:</span><span class="sxs-lookup"><span data-stu-id="49127-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="49127-122">Bytes 0-3: RVA; o endereço virtual relativo do dicionário.</span><span class="sxs-lookup"><span data-stu-id="49127-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="49127-123">Bytes 4-7: offset; um deslocamento relativo ao início do heap.</span><span class="sxs-lookup"><span data-stu-id="49127-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="49127-124">O heap</span><span class="sxs-lookup"><span data-stu-id="49127-124">The Heap</span></span>

<span data-ttu-id="49127-125">O tamanho do heap pode ser calculado por um leitor de fluxo subtraindo o comprimento do fluxo do tamanho do diretório + 4.</span><span class="sxs-lookup"><span data-stu-id="49127-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="49127-126">Em outras palavras:</span><span class="sxs-lookup"><span data-stu-id="49127-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="49127-127">onde o tamanho do diretório é `N * 8` .</span><span class="sxs-lookup"><span data-stu-id="49127-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="49127-128">O formato de cada item de informações de instanciação no heap é:</span><span class="sxs-lookup"><span data-stu-id="49127-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="49127-129">O comprimento deste item de informações de instanciação em bytes no formato de metadados ECMA compactado.</span><span class="sxs-lookup"><span data-stu-id="49127-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="49127-130">O valor exclui essas informações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="49127-130">The value excludes this length information.</span></span>

- <span data-ttu-id="49127-131">O número de tipos de instanciação genérica ou *T*, em formato de metadados ECMA compactado.</span><span class="sxs-lookup"><span data-stu-id="49127-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="49127-132">Tipos *T* , cada um representado no formato de assinatura do tipo ECMA.</span><span class="sxs-lookup"><span data-stu-id="49127-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="49127-133">A inclusão do comprimento de cada elemento de heap permite a classificação simples da seção de diretório sem afetar o heap.</span><span class="sxs-lookup"><span data-stu-id="49127-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="49127-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49127-134">Requirements</span></span>

<span data-ttu-id="49127-135">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49127-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="49127-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49127-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="49127-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49127-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="49127-138">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49127-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="49127-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="49127-139">See also</span></span>

- [<span data-ttu-id="49127-140">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="49127-140">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="49127-141">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="49127-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
