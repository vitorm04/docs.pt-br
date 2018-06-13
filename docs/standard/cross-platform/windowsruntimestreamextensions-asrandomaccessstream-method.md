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
ms.openlocfilehash: 16f878abc11589fe62f78d941b367d82d7b49e1c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768509"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="bf9e7-102">Método WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream)</span><span class="sxs-lookup"><span data-stu-id="bf9e7-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="bf9e7-103">[Suporte somente no .NET Framework 4.5.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="bf9e7-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="bf9e7-104">Converte o fluxo especificado em um fluxo de acesso aleatório.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="bf9e7-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bf9e7-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="bf9e7-106">**Assembly:** System.Runtime.WindowsRuntime (em System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="bf9e7-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9e7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf9e7-107">Syntax</span></span>  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf9e7-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf9e7-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="bf9e7-109">Tipo: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bf9e7-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="bf9e7-110">O fluxo a ser convertido.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf9e7-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bf9e7-111">Return Value</span></span>  
 <span data-ttu-id="bf9e7-112">Tipo: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf9e7-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="bf9e7-113">Um [!INCLUDE[wrt](../../../includes/wrt-md.md)] fluxo de acesso aleatório, que representa o fluxo convertido.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="bf9e7-114">Exceções</span><span class="sxs-lookup"><span data-stu-id="bf9e7-114">Exceptions</span></span>  
  
|<span data-ttu-id="bf9e7-115">Exceção</span><span class="sxs-lookup"><span data-stu-id="bf9e7-115">Exception</span></span>|<span data-ttu-id="bf9e7-116">Condição</span><span class="sxs-lookup"><span data-stu-id="bf9e7-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="bf9e7-117">O fluxo a ser convertido não oferece suporte a busca.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf9e7-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf9e7-118">Remarks</span></span>  
 <span data-ttu-id="bf9e7-119">Este método de extensão está disponível somente quando você desenvolve aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="bf9e7-120">Esse método fornece um modo conveniente de trabalhar com fluxos em aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="bf9e7-121">O fluxo .NET Framework que você deseja converter deve oferecer suporte a busca.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="bf9e7-122">Para obter mais informações, consulte o método <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf9e7-123">Essa API tem suporte no .NET Framework 4.5.1 e versões posteriores, mas não na versão 4.5.</span><span class="sxs-lookup"><span data-stu-id="bf9e7-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="bf9e7-124">Informações de versão</span><span class="sxs-lookup"><span data-stu-id="bf9e7-124">Version Information</span></span>  
 <span data-ttu-id="bf9e7-125">**.NET para aplicativos da Windows Store**</span><span class="sxs-lookup"><span data-stu-id="bf9e7-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="bf9e7-126">Suporte no: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="bf9e7-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9e7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf9e7-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="bf9e7-128">Como converter entre fluxos do .NET Framework e do Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="bf9e7-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
