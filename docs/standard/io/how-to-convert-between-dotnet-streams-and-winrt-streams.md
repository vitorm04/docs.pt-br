---
title: 'Como: Fazer a conversão entre fluxos do .NET Framework e fluxos do Windows Runtime (somente Windows)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc38e69a79af7c7220b8e3b55d4cb1f4ca3695f6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255192"
---
# <a name="how-to-convert-between-net-framework-and-windows-runtime-streams-windows-only"></a>Como: Fazer a conversão entre fluxos do .NET Framework e fluxos do Windows Runtime (somente Windows)

O .NET Framework para aplicativos UWP é um subconjunto do .NET Framework completo. Devido a requisitos de segurança e outros requisitos dos aplicativos UWP, não é possível usar o conjunto completo de APIs do .NET Framework para abrir e ler arquivos. Para obter mais informações, confira [Visão geral do .NET para aplicativos UWP](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). No entanto, talvez você queira usar APIs do .NET Framework para outras operações de manipulação de fluxos. Para manipular esses fluxos, faça a conversão entre um tipo de fluxo do .NET Framework, como <xref:System.IO.MemoryStream> ou <xref:System.IO.FileStream>, e um fluxo do Windows Runtime, como <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream> ou <xref:Windows.Storage.Streams.IRandomAccessStream>.

A classe [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) contém métodos que tornam essas conversões fáceis. No entanto, as diferenças subjacentes entre os fluxos do .NET Framework e os fluxos do Windows Runtime afetam os resultados do uso desses métodos, conforme descrito nas seguintes seções:

## <a name="convert-from-a-windows-runtime-to-a-net-framework-stream"></a>Converter um fluxo do Windows Runtime em um fluxo do .NET Framework
Para converter um fluxo do Windows Runtime em um fluxo do .NET Framework, use um dos seguintes métodos [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx):

- [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx) converte um fluxo de acesso aleatório no Windows Runtime em um fluxo gerenciado no .NET para aplicativos UWP.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx) converte um fluxo de saída no Windows Runtime em um fluxo gerenciado no .NET para aplicativos UWP.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) converte um fluxo de entrada no Windows Runtime em um fluxo gerenciado no .NET para aplicativos UWP.

O Windows Runtime oferece tipos de fluxo que dão suporte ao acesso somente leitura, somente gravação ou de leitura e gravação. Essas funcionalidades são mantidas quando você converte um fluxo do Windows Runtime em um fluxo do .NET Framework. Além disso, se você converter um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework e convertê-lo de volta, você obterá instância original do Tempo de Execução do Windows outra vez. 

É uma melhor prática usar o método de conversão correspondente às funcionalidades do fluxo do Windows Runtime que você deseja converter. No entanto, como <xref:Windows.Storage.Streams.IRandomAccessStream> é legível e gravável (implementa <xref:Windows.Storage.Streams.IOutputStream> e <xref:Windows.Storage.Streams.IInputStream>), os métodos de conversão mantêm as funcionalidades do fluxo original. Por exemplo, o uso de [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) para converter um <xref:Windows.Storage.Streams.IRandomAccessStream> não limita o fluxo convertido do .NET Framework a ser legível. Ele também é gravável.

## <a name="example-convert-windows-runtime-random-access-to-net-framework-stream"></a>Exemplo: Converter um fluxo de acesso aleatório do Windows Runtime em um fluxo do .NET Framework
Para converter um fluxo de acesso aleatório do Windows Runtime em um fluxo do .NET Framework, use o método [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx).

O exemplo de código a seguir solicita que você selecione um arquivo, abre-o com as APIs do Windows Runtime e, em seguida, converte-o em um fluxo do .NET Framework. Ele lê o fluxo e os coloca em um bloco de texto. Você normalmente manipulará o fluxo com as APIs do .NET Framework antes de produzir os resultados.

Para executar esse exemplo, crie um aplicativo UWP XAML que contém um bloco de texto chamado `TextBlock1` e um botão chamado `Button1`. Associe o evento de clique no botão ao método `button1_Click` mostrado no exemplo.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage1.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage1.xaml.vb)]

## <a name="convert-from-a-net-framework-to-a-windows-runtime-stream"></a>Converter um fluxo do .NET Framework em um fluxo do Windows Runtime
Para converter um fluxo do .NET Framework em um fluxo do Windows Runtime, use um dos seguintes métodos [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx):

- [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) converte um fluxo gerenciado no .NET para aplicativos UWP em um fluxo de entrada no Windows Runtime.
  
- [System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) converte um fluxo gerenciado no .NET para aplicativos UWP em um fluxo de saída no Windows Runtime.
  
- [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) converte um fluxo gerenciado no .NET para aplicativos UWP em um fluxo de acesso aleatório que pode ser usado pelo Windows Runtime para leitura ou gravação.

Quando você converte um fluxo do .NET Framework em um fluxo do Windows Runtime, as funcionalidades do fluxo convertido dependem do fluxo original. Por exemplo, se o fluxo original dá suporte à leitura e à gravação e você chama [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) para converter o fluxo, o tipo retornado é um `IRandomAccessStream`. `IRandomAccessStream` implementa `IInputStream` e `IOutputStream` e dá suporte à leitura e à gravação.

Os fluxos do .NET Framework não dão suporte à clonagem, mesmo após a conversão. Se você converte um fluxo do .NET Framework em um fluxo do Windows Runtime e chama <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> ou <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, que chama <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A>, ou se você chama <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> diretamente, ocorre uma exceção.

## <a name="example-convert-net-framework-to-windows-runtime-random-access-stream"></a>Exemplo: Converter um fluxo do .NET Framework em um fluxo de acesso aleatório do Windows Runtime

Para converter um fluxo do .NET Framework em um fluxo de acesso aleatório do Windows Runtime, use o método [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md), conforme mostrado no seguinte exemplo:

> [!IMPORTANT]
> Verifique se o fluxo do .NET Framework que você está usando dá suporte à busca ou copie-o para um fluxo que dê esse suporte. Você pode usar a propriedade <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> para determinar isso.

Para executar esse exemplo, crie um aplicativo UWP XAML direcionado ao .NET Framework 4.5.1 e que contém um bloco de texto chamado `TextBlock2` e um botão chamado `Button2`. Associe o evento de clique no botão ao método `button2_Click` mostrado no exemplo.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage2.xaml.cs)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage2.xaml.vb)]

## <a name="see-also"></a>Consulte também

- [Início Rápido: Ler e gravar um arquivo (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
- [Visão geral dos aplicativos .NET para Windows Store](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
- [.NET para Aplicativos da Windows Store: APIs compatíveis](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)  
