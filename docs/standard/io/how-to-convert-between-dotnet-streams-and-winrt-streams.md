---
title: 'Como converter entre fluxos do .NET Framework e do Windows Runtime '
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 23a763ea-8348-4244-9f8c-a4280b870b47
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9e4c1c0b432ff44af0410b1efdc3940cd0ff19c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-convert-between-net-framework-streams-and-windows-runtime-streams"></a>Como converter entre fluxos do .NET Framework e do Windows Runtime 
O .NET Framework para aplicativos da Windows Store é um subconjunto do .NET Framework completo. Devido a requisitos de segurança e outros requisitos dos aplicativos da Windows Store, você não pode usar o conjunto completo de APIs do .NET Framework para abrir e ler arquivos. Para saber mais, confira [Visão geral do .NET para aplicativos da Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). No entanto, talvez você queira usar APIs do .NET Framework para outras operações de manipulação de fluxos. Para manipular esses fluxos, talvez você ache necessário converter entre um tipo de fluxo do .NET Framework, como <xref:System.IO.MemoryStream> ou <xref:System.IO.FileStream> e um fluxo do Tempo de Execução do Windows, como [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx), [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) ou [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx).  
  
 A classe <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions` contém métodos que tornam fáceis essas conversões. No entanto, há diferenças subjacentes entre os fluxos no .NET Framework e no Tempo de Execução do Windows que afetam os resultados do uso desses métodos. Os detalhes são descritos nas seções a seguir.  
  
<a name="BKMK_ConvertingfromaWindowsRuntimestreamtoaNETFrameworkstream"></a>   
## <a name="converting-from-a-windows-runtime-stream-to-a-net-framework-stream"></a>Convertendo de um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework  
 Você pode converter de um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework usando um dos seguintes métodos <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`  
 Converte um fluxo de acesso aleatório no Tempo de Execução do Windows para um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForWrite`
 Converte um fluxo de saída no Tempo de Execução do Windows para um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store.  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead`  
 Converte um fluxo de entrada no Tempo de Execução do Windows para um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store.  
  
 O Tempo de Execução do Windows possui tipos de fluxos somente leitura, somente gravação ou leitura e gravação, e esses recursos são mantidos quando você converte um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework. Além disso, se você converter um fluxo do Tempo de Execução do Windows para um fluxo do .NET Framework e convertê-lo de volta, você obterá instância original do Tempo de Execução do Windows outra vez. É prática recomendada usar o método de conversão correspondente aos recursos do fluxo do Tempo de Execução do Windows que você gostaria de converter. No entanto, como [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) é legível e gravável (implementa [IOutputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ioutputstream.aspx) e [IInputStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.iinputstream.aspx)), você pode usar qualquer um dos métodos de conversão, e os recursos do fluxo original são mantidos. Por exemplo, usar <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStreamForRead` para converter um [IRandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx) não limitará o fluxo convertido do .NET Framework a ser somente leitura; ele também será gravável.  
  
#### <a name="to-convert-from-a-windows-runtime-random-access-stream-to-a-net-framework-stream"></a>Para converter de um fluxo de acesso aleatório do Tempo de Execução do Windows para um fluxo do .NET Framework  
  
-   Use o método <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsStream`.  
  
     O exemplo de código a seguir mostra como solicitar que o usuário selecione um arquivo, abra-o com APIs do Tempo de Execução do Windows e converta-o em um fluxo do .NET Framework, o qual é lido e gera um bloco de texto como saída. Nesse cenário, você normalmente manipularia o fluxo com APIs do .NET Framework antes de produzir os resultados.  
  
     Para executar esse exemplo, você deverá criar um aplicativo XAML da Windows Store que contenha um bloco de texto chamado `TextBlock1` e um botão chamado `Button1`. O evento de clique no botão deve estar associado ao método `button1_Click` mostrado no exemplo.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#1)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#1)]  
  
<a name="BKMK_ConvertingfromaNETFrameworkstreamtoaWindowsRuntimestream"></a>   
## <a name="converting-from-a-net-framework-stream-to-a-windows-runtime-stream"></a>Convertendo de um fluxo do .NET Framework para um fluxo do Tempo de Execução do Windows  
 Você pode converter de um fluxo do .NET Framework em um fluxo do Tempo de Execução do Windows usando um dos seguintes métodos <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`:  
  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream`  
 Converte um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store para um fluxo de entrada no Tempo de Execução do Windows.  
  
<!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsOutputStream%2A>  --> `System.IO.WindowsRuntimeStreamExtensions.AsOutputStream`
 Converte um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store para fluxo de entrada no Tempo de Execução do Windows.  
  
 [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md)  
 Converte um fluxo gerenciado no subconjunto do .NET para aplicativos da Windows Store para um fluxo de acesso aleatório no Tempo de Execução do Windows.  
  
 Quando você converte um fluxo do .NET Framework para um fluxo do Tempo de Execução do Windows, os recursos do fluxo convertido dependem do fluxo original. Por exemplo, se o fluxo original oferece suporte a leitura e a gravação e você chama <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions.AsInputStream%2A> --> `System.IO.WindowsRuntimeStreamExtensions.AsInputStream` para converter o fluxo, o tipo retornado será um `IRandomAccessStream`, que implementa `IInputStream` e `IOutputStream`, e oferece suporte à leitura e à gravação de  
  
 Os fluxos do .NET Framework não oferecem suporte a clonagem, mesmo após a conversão. Isso significa que, se você converter um fluxo do .NET Framework em um fluxo do Tempo de Execução do Windows e chamar [GetInputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.inmemoryrandomaccessstream.getinputstreamat.aspx) ou [GetOutputStreamAt](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.irandomaccessstream.getoutputstreamat.aspx), que chamam [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) ou [CloneStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstreamoverstream.clonestream.aspx) diretamente, uma exceção ocorrerá.  
  
#### <a name="to-convert-from-a-net-framework-stream-to-a-windows-runtime-random-access-stream"></a>Para converter de um fluxo do .NET Framework para um fluxo de acesso aleatório do Tempo de Execução do Windows  
  
-   Use o método [AsRandomAccessStream](../../../docs/standard/cross-platform/windowsruntimestreamextensions-asrandomaccessstream-method.md), conforme mostrado no exemplo a seguir.  
  
    > [!IMPORTANT]
    >  Certifique-se de que o fluxo do .NET Framework você está usando ofereça suporte a busca ou copie-o para um fluxo que o faça. Você pode usar a propriedade <xref:System.IO.Stream.CanSeek%2A?displayProperty=nameWithType> para determinar isso.  
  
     Para executar esse exemplo, você deve criar um aplicativo XAML da Windows Store voltado para o .NET Framework 4.5.1 e que contenha um bloco de texto chamado `TextBlock2` e um botão chamado `Button2`. O evento de clique no botão deve estar associado ao método `button2_Click` mostrado neste exemplo.  
  
     [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#imports)]
     [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#Imports](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#imports)]  
    [!code-csharp[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/cs/mainpage.xaml.cs#2)]
    [!code-vb[System.IO.WindowsRuntimeStreamExtensionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestreamextensionsex/vb/mainpage.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Início Rápido: Lendo e gravando arquivos (Windows)](http://msdn.microsoft.com/library/windows/apps/hh464978.aspx)  
 [Visão geral dos aplicativos .NET para Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [.NET para aplicativos da Windows Store – APIs com suporte](http://msdn.microsoft.com/library/windows/apps/br230232.aspx)
