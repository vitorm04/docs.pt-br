---
title: Compilando aplicativos com o .NET Nativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 76645ae43ce6754ffdf505729ec1198785a71561
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="compiling-apps-with-net-native"></a>Compilando aplicativos com o .NET Nativo
[!INCLUDE[net_native](../../../includes/net-native-md.md)] é uma tecnologia de pré-compilação para compilação e implantação de aplicativos do Windows que está incluída com [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]. Ele compila automaticamente a versão de lançamento de aplicativos escritos em código gerenciado (C# ou Visual Basic) e que são destinados ao .NET Framework e ao Windows 10 para código nativo.  
  
 Normalmente, os aplicativos com destino para o .NET Framework são compilados para IL (linguagem intermediária). No tempo de execução, uma compilação JIT (just-in-time) converte o IL em código nativo. Em contraste, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] compila aplicativos do Windows diretamente em código nativo. Para desenvolvedores, isso significa que:  
  
-   Seus aplicativos fornecerão o melhor desempenho do código nativo.  
  
-   Você pode continuar a programar em C# ou em Visual Basic.  
  
-   Você pode continuar a aproveitar os recursos fornecidos pelo .NET Framework, incluindo sua biblioteca de classes, coleta de lixo, gerenciamento automático de memória e manipulação de exceção.  
  
 Para os usuários dos seus aplicativos, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] oferece estas vantagens:  
  
-   Tempos de execução rápidos  
  
-   Tempos de inicialização rápida consistentemente  
  
-   Custos baixos de implantação e atualização  
  
-   Uso da memória otimizada do aplicativo  
  
 Porém, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] representa mais do que uma compilação para código nativo. Ele transforma a maneira que os aplicativos .NET Framework são criados e executados. Em particular:  
  
-   Durante a pré-compilação, partes necessárias do .NET Framework são vinculadas estaticamente ao seu aplicativo. Isso permite que o aplicativo seja executado com as bibliotecas de aplicativo local do .NET Framework e o compilador realize análises globais para proporcionar vantagens de desempenho. Como resultado, os aplicativos são inicializados consistentemente mais rápido mesmo depois de atualizações do .NET Framework.  
  
-   O tempo de execução do [!INCLUDE[net_native](../../../includes/net-native-md.md)] é otimizado para pré-compilação estática, podendo oferecer melhor desempenho. Ao mesmo tempo, ele mantém os recursos de reflexão principais que os desenvolvedores acham tão produtivos.  
  
-   O [!INCLUDE[net_native](../../../includes/net-native-md.md)] usa o mesmo back-end que o compilador do C++, que é otimizado para cenários de pré-compilação estáticos.  
  
 O [!INCLUDE[net_native](../../../includes/net-native-md.md)] também oferece benefícios de desempenho do C++ para desenvolvedores de código gerenciado porque ele usa as ferramentas iguais ou semelhantes às do C++ nos bastidores, conforme mostrado nesta tabela.  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|Libraries|O .NET Framework + Tempo de Execução do Windows|Win32 + Tempo de Execução do Windows|  
|Compilador|Compilador de otimização de UTC|Compilador de otimização de UTC|  
|Implantado|Binários prontos para execução|Binários prontos para execução (ASM)|  
|Tempo de execução|MRT.dll (tempo de execução de CLR mínimo)|CRT.dll (tempo de execução C)|  
  
 Para aplicativos do Windows para Windows 10, carregue os binários de compilação de código do .NET Native nos pacotes do aplicativo (arquivos .appx) para a Windows Store.  
  
## <a name="in-this-section"></a>Nesta seção  
 Para obter mais informações sobre o desenvolvimento de aplicativos com compilação de código do .NET Nativo, consulte estes tópicos:  
  
-   [Guia de Introdução à compilação de código do .NET Native: passo a passo da experiência de desenvolvedor](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [Compilação e .NET Native:](../../../docs/framework/net-native/net-native-and-compilation.md) como o .NET Native compila seu projeto para código nativo.  
  
-   [Reflexão e .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [APIs que dependem de reflexão](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [Referência da API de reflexão](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [Serialização e metadados](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Migrando seu aplicativo da Windows Store para .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [Solução de problemas gerais do .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes do .NET Native](http://msdn.microsoft.com/vstudio/dn642499.aspx)

