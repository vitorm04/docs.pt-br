---
title: Como converter uma matriz de bytes em um guia de C# programação int
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698749"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="99d61-102">Como converter uma matriz de bytes em um int (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="99d61-102">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="99d61-103">Este exemplo mostra como usar a classe <xref:System.BitConverter> para converter uma matriz de bytes em um [int](../../language-reference/builtin-types/integral-numeric-types.md) e de volta em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="99d61-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="99d61-104">Talvez você precise converter bytes em um tipo de dados interno depois de ler bytes da rede, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="99d61-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="99d61-105">Além do método [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) no exemplo, a tabela a seguir lista os métodos na classe <xref:System.BitConverter> que convertem bytes (de uma matriz de bytes) em outros tipos internos.</span><span class="sxs-lookup"><span data-stu-id="99d61-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="99d61-106">Tipo retornado</span><span class="sxs-lookup"><span data-stu-id="99d61-106">Type returned</span></span>|<span data-ttu-id="99d61-107">Método</span><span class="sxs-lookup"><span data-stu-id="99d61-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="99d61-108">[ToBoolean (byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="99d61-109">[ToChar (byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="99d61-110">[ToDouble (byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="99d61-111">[ToInt16 (byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="99d61-112">[ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="99d61-113">[ToInt64 (byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="99d61-114">[Tosimples (byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="99d61-115">[ToUInt16 (byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="99d61-116">[ToUInt32 (byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="99d61-117">[ToUInt64 (byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="99d61-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="99d61-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99d61-118">Example</span></span>

<span data-ttu-id="99d61-119">Este exemplo Inicializa uma matriz de bytes, reverte a matriz se a arquitetura do computador for little-endian (ou seja, o byte menos significativo é armazenado primeiro) e, em seguida, chama o método [ToInt32 (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) para converter quatro bytes na matriz em uma `int`.</span><span class="sxs-lookup"><span data-stu-id="99d61-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="99d61-120">O segundo argumento para [ToInt32 (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) especifica o índice de início da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="99d61-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="99d61-121">A saída pode diferir dependendo da ordenação da arquitetura do seu computador.</span><span class="sxs-lookup"><span data-stu-id="99d61-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="99d61-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99d61-122">Example</span></span>

<span data-ttu-id="99d61-123">Neste exemplo, o método <xref:System.BitConverter.GetBytes%28System.Int32%29> da classe <xref:System.BitConverter> é chamado para converter um `int` em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="99d61-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="99d61-124">A saída pode diferir dependendo da ordenação da arquitetura do seu computador.</span><span class="sxs-lookup"><span data-stu-id="99d61-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="99d61-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="99d61-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="99d61-126">Tipos</span><span class="sxs-lookup"><span data-stu-id="99d61-126">Types</span></span>](./index.md)
