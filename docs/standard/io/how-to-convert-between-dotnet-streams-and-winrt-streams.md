---
title: 'Como converter entre fluxos do .NET Framework e do Windows Runtime '
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96067ab6c8e13417158e4ebf7fae0e08cb9fbea4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087473"
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Como converter entre fluxos do .NET Framework e do Windows Runtime 

O .NET Framework para aplicativos da Windows Store é um subconjunto do .NET Framework completo. Devido a requisitos de segurança e outros requisitos dos aplicativos da Windows Store, você não pode usar o conjunto completo de APIs do .NET Framework para abrir e ler arquivos. Para saber mais, confira [Visão geral do .NET para aplicativos da Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). No entanto, talvez você queira usar APIs do .NET Framework para outras operações de manipulação de fluxos. Para manipular esses fluxos, talvez você ache necessário converter entre um tipo de fluxo do .NET Framework, como <xref:System.IO.MemoryStream> ou <xref:System.IO.FileStream>, e um fluxo do Windows Runtime, como <xref:Windows.Storage.Streams.IInputStream>, <xref:Windows.Storage.Streams.IOutputStream> ou <xref:Windows.Storage.Streams.IRandomAccessStream>.

A classe [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx) contém métodos que tornam essas conversões fáceis. No entanto, há diferenças subjacentes entre os fluxos no .NET Framework e no Tempo de Execução do Windows que afetam os resultados do uso desses métodos. Os detalhes são descritos nas seções a seguir.

## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Convertendo de um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework

Você pode converter de um fluxo do Windows Runtime para um fluxo do .NET Framework usando um dos seguintes métodos [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx):

[System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx)  
Converte um fluxo de acesso aleatório no Tempo de Execução do Windows para um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforwrite.aspx)  
Converte um fluxo de saída no Tempo de Execução do Windows para um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store.

[System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx)  
Converte um fluxo de entrada no Tempo de Execução do Windows para um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store.

O Tempo de Execução do Windows possui tipos de fluxos somente leitura, somente gravação ou leitura e gravação, e esses recursos são mantidos quando você converte um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework. Além disso, se você converter um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework e convertê-lo de volta, você obterá instância original do Tempo de Execução do Windows outra vez. É prática recomendada usar o método de conversão correspondente aos recursos do fluxo do Tempo de Execução do Windows que você gostaria de converter. No entanto, como <xref:Windows.Storage.Streams.IRandomAccessStream> é legível e gravável (implementa <xref:Windows.Storage.Streams.IOutputStream> e <xref:Windows.Storage.Streams.IInputStream>), você pode usar qualquer um dos métodos de conversão, e as funcionalidades do fluxo original são mantidas. Por exemplo, usar [System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstreamforread.aspx) para converter um <xref:Windows.Storage.Streams.IRandomAccessStream> não limitará o fluxo convertido do .NET Framework a ser somente leitura; ele também será gravável.

### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Para converter de um fluxo de acesso aleatório do Tempo de Execução do Windows para um fluxo do .NET Framework

- Use o método [System.IO.WindowsRuntimeStreamExtensions.AsStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asstream.aspx).

  O exemplo de código a seguir mostra como solicitar que o usuário selecione um arquivo, abra-o com APIs do Tempo de Execução do Windows e converta-o em um fluxo do .NET Framework, o qual é lido e gera um bloco de texto como saída. Nesse cenário, você normalmente manipularia o fluxo com APIs do .NET Framework antes de produzir os resultados.

  Para executar esse exemplo, você deverá criar um aplicativo XAML da Windows Store que contenha um bloco de texto chamado `TextBlock1` e um botão chamado `Button1`. O evento de clique no botão deve estar associado ao método `button1_Click` mostrado no exemplo.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]

## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Convertendo de um fluxo do .NET Framework para um fluxo do Tempo de Execução do Windows

Você pode converter de um fluxo do .NET Framework para um fluxo do Windows Runtime usando um dos seguintes métodos [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx):

[System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) Converte um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store para um fluxo de entrada no Windows Runtime.

[System.IO.WindowsRuntimeStreamExtensions.AsOutputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asoutputstream.aspx) Converte um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store para um fluxo de saída no Windows Runtime.

[AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md) Converte um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store para um fluxo de acesso aleatório que pode ser usado para leitura ou gravação no Windows Runtime.

Quando você converte um fluxo do .NET Framework para um fluxo do Tempo de Execução do Windows, os recursos do fluxo convertido dependem do fluxo original. Por exemplo, se o fluxo original dá suporte à leitura e à gravação e você chama [System.IO.WindowsRuntimeStreamExtensions.AsInputStream](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.asinputstream.aspx) para converter o fluxo, o tipo retornado é um `IRandomAccessStream`, que implementa `IInputStream` e `IOutputStream`, e dá suporte à leitura e à gravação.

Os fluxos do .NET Framework não oferecem suporte a clonagem, mesmo após a conversão. Isso significa que, se você converter um fluxo do .NET Framework em um fluxo do Windows Runtime e chamar <xref:Windows.Storage.Streams.InMemoryRandomAccessStream.GetInputStreamAt%2A> ou <xref:Windows.Storage.Streams.IRandomAccessStream.GetOutputStreamAt%2A>, que chamam <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> ou <xref:Windows.Storage.Streams.RandomAccessStreamOverStream.CloneStream%2A> diretamente, uma exceção ocorrerá.

### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Para converter de um fluxo do .NET Framework para um fluxo de acesso aleatório do Tempo de Execução do Windows

- Use o método [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md), conforme mostrado no exemplo a seguir:

  > [!IMPORTANT]
  > Certifique-se de que o fluxo do .NET Framework você está usando ofereça suporte a busca ou copie-o para um fluxo que o faça. Você pode usar a propriedade <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> para determinar isso.

  Para executar esse exemplo, você deve criar um aplicativo XAML da Windows Store voltado para o .NET Framework 4.5.1 e que contenha um bloco de texto chamado `TextBlock2` e um botão chamado `Button2`. O evento de clique no botão deve estar associado ao método `button2_Click` mostrado neste exemplo.

  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]
  [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
  [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]

## <a name="see-also"></a>Consulte também

- [Guia de Início Rápido: Lendo e gravando arquivos (Windows)](https://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
- [Visão geral dos aplicativos .NET para Windows Store](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
- [.NET para aplicativos da Windows Store – APIs com suporte](https://msdn.microsoft.com/library/windows/apps/br230232.aspx)  