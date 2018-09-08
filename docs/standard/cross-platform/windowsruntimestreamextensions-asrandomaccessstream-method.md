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
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>Método WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream)

[Suporte somente no .NET Framework 4.5.1 e versões posteriores]

Converte o fluxo especificado em um fluxo de acesso aleatório.

**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **Assembly:** windowsruntime (em windowsruntime)

## <a name="syntax"></a>Sintaxe

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

## <a name="parameters"></a>Parâmetros

`stream`

Tipo: <xref:System.IO.Stream?displayProperty=nameWithType>  
O fluxo a ser convertido.

## <a name="return-value"></a>Valor de retorno

Tipo: <xref:Windows.Storage.Streams.RandomAccessStream>  
Um [!INCLUDE[wrt](../../../includes/wrt-md.md)] fluxo de acesso aleatório, que representa o fluxo convertido.

## <a name="exceptions"></a>Exceções

|Exceção|Condição|
|---------------|---------------|
|<xref:System.NotSupportedException>|O fluxo a ser convertido não oferece suporte a busca.|

## <a name="remarks"></a>Comentários

Este método de extensão está disponível somente quando você desenvolve aplicativos da Windows Store. Esse método fornece um modo conveniente de trabalhar com fluxos em aplicativos da Windows Store. O fluxo .NET Framework que você deseja converter deve oferecer suporte a busca. Para obter mais informações, consulte o método <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType>.

> [!IMPORTANT]
> Essa API tem suporte no .NET Framework 4.5.1 e versões posteriores, mas não na versão 4.5.

## <a name="version-information"></a>Informações de versão

**.NET para aplicativos da Windows Store**

Suporte no: Windows 8.1

## <a name="see-also"></a>Consulte também

-[Windowsruntimestreamextensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[como: converter entre fluxos do .NET Framework e do Windows Runtime](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
