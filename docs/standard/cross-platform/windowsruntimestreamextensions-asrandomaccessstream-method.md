---
title: Método WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8935a8c282bbe812ad76ac6d4228c38ab12626a4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193582"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="cf705-102">Método WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream)</span><span class="sxs-lookup"><span data-stu-id="cf705-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="cf705-103">[Suporte somente no .NET Framework 4.5.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="cf705-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="cf705-104">Converte o fluxo especificado em um fluxo de acesso aleatório.</span><span class="sxs-lookup"><span data-stu-id="cf705-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="cf705-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **Assembly:** windowsruntime (em windowsruntime)</span><span class="sxs-lookup"><span data-stu-id="cf705-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf705-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf705-106">Syntax</span></span>

```csharp
[CLSCompliantAttribute(false)]
public static IRandomAccessStream AsRandomAccessStream(Stream stream)
```

```vb
'Declaration
<ExtensionAttribute> _
<CLSCompliantAttribute(False)> _
Public Shared Function AsRandomAccessStream ( _
        stream As Stream) As IRandomAccessStream
```

## <a name="parameters"></a><span data-ttu-id="cf705-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf705-107">Parameters</span></span>

`stream`

<span data-ttu-id="cf705-108">Tipo: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cf705-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="cf705-109">O fluxo a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="cf705-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf705-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cf705-110">Return Value</span></span>

<span data-ttu-id="cf705-111">Tipo: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="cf705-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="cf705-112">Um [!INCLUDE[wrt](../../../includes/wrt-md.md)] fluxo de acesso aleatório, que representa o fluxo convertido.</span><span class="sxs-lookup"><span data-stu-id="cf705-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="cf705-113">Exceções</span><span class="sxs-lookup"><span data-stu-id="cf705-113">Exceptions</span></span>

|<span data-ttu-id="cf705-114">Exceção</span><span class="sxs-lookup"><span data-stu-id="cf705-114">Exception</span></span>|<span data-ttu-id="cf705-115">Condição</span><span class="sxs-lookup"><span data-stu-id="cf705-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="cf705-116">O fluxo a ser convertido não oferece suporte a busca.</span><span class="sxs-lookup"><span data-stu-id="cf705-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cf705-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf705-117">Remarks</span></span>

<span data-ttu-id="cf705-118">Este método de extensão está disponível somente quando você desenvolve aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cf705-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="cf705-119">Esse método fornece um modo conveniente de trabalhar com fluxos em aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cf705-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="cf705-120">O fluxo .NET Framework que você deseja converter deve oferecer suporte a busca.</span><span class="sxs-lookup"><span data-stu-id="cf705-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="cf705-121">Para obter mais informações, consulte o método <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cf705-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf705-122">Essa API tem suporte no .NET Framework 4.5.1 e versões posteriores, mas não na versão 4.5.</span><span class="sxs-lookup"><span data-stu-id="cf705-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="cf705-123">Informações de versão</span><span class="sxs-lookup"><span data-stu-id="cf705-123">Version Information</span></span>

<span data-ttu-id="cf705-124">**.NET para aplicativos da Windows Store**</span><span class="sxs-lookup"><span data-stu-id="cf705-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="cf705-125">Suporte no: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cf705-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="cf705-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf705-126">See also</span></span>

<span data-ttu-id="cf705-127">-[Windowsruntimestreamextensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[como: converter entre fluxos do .NET Framework e do Windows Runtime](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)</span><span class="sxs-lookup"><span data-stu-id="cf705-127">-[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)</span></span>
