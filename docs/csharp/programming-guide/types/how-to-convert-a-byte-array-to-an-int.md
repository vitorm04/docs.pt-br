---
title: Como converter uma matriz de bytes em um guia de C# programação de int
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 96507f03a3d64b96ef6059a92459bfc7fa854372
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395683"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="499dc-102">Como converter uma matriz de bytes em um int (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="499dc-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="499dc-103">Este exemplo mostra como usar a classe <xref:System.BitConverter> para converter uma matriz de bytes em um [int](../../language-reference/builtin-types/integral-numeric-types.md) e de volta em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="499dc-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="499dc-104">Talvez você precise converter bytes em um tipo de dados interno depois de ler bytes da rede, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="499dc-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="499dc-105">Além do método [ToInt32 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) no exemplo, a tabela a seguir lista os métodos na classe <xref:System.BitConverter> que convertem bytes (de uma matriz de bytes) em outros tipos internos.</span><span class="sxs-lookup"><span data-stu-id="499dc-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="499dc-106">Tipo retornado</span><span class="sxs-lookup"><span data-stu-id="499dc-106">Type returned</span></span>|<span data-ttu-id="499dc-107">Método</span><span class="sxs-lookup"><span data-stu-id="499dc-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="499dc-108">[ToBoolean (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="499dc-109">[ToChar (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="499dc-110">[ToDouble (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="499dc-111">[ToInt16 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="499dc-112">[ToInt32 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="499dc-113">[ToInt64 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="499dc-114">[ToSingle (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="499dc-115">[ToUInt16 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="499dc-116">[ToUInt32 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="499dc-117">[ToUInt64 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="499dc-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="499dc-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="499dc-118">Example</span></span>

<span data-ttu-id="499dc-119">Este exemplo Inicializa uma matriz de bytes, reverte a matriz se a arquitetura do computador for little-endian (ou seja, o byte menos significativo é armazenado primeiro) e, em seguida, chama o método [ToInt32 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) para converter quatro bytes em a matriz a um `int`.</span><span class="sxs-lookup"><span data-stu-id="499dc-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="499dc-120">O segundo argumento para [ToInt32 (byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) especifica o índice de início da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="499dc-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="499dc-121">A saída pode ser diferente dependendo do quanto a arquitetura do computador é endian.</span><span class="sxs-lookup"><span data-stu-id="499dc-121">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="499dc-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="499dc-122">Example</span></span>

<span data-ttu-id="499dc-123">Neste exemplo, o método <xref:System.BitConverter.GetBytes%28System.Int32%29> da classe <xref:System.BitConverter> é chamado para converter um `int` em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="499dc-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="499dc-124">A saída pode ser diferente dependendo do quanto a arquitetura do computador é endian.</span><span class="sxs-lookup"><span data-stu-id="499dc-124">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="499dc-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="499dc-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="499dc-126">Tipos</span><span class="sxs-lookup"><span data-stu-id="499dc-126">Types</span></span>](./index.md)
