---
title: Compilando aplicativos com o .NET Nativo
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660899"
---
# <a name="compiling-apps-with-net-native"></a>Compilando aplicativos com o .NET Nativo

.NET native é uma tecnologia de pré-compilação para compilar e implantar aplicativos do Windows que está incluída no Visual Studio 2015 e versões posteriores. Ele compila automaticamente a versão de lançamento de aplicativos escritos em código gerenciado (C# ou Visual Basic) e que são destinados ao .NET Framework e ao Windows 10 para código nativo.

Normalmente, os aplicativos com destino para o .NET Framework são compilados para IL (linguagem intermediária). No tempo de execução, uma compilação JIT (just-in-time) converte o IL em código nativo. Em contraste, o .NET Native compila aplicativos do Windows diretamente em código nativo. Para desenvolvedores, isso significa que:

- O desempenho do código nativo de recurso de seus aplicativos. Normalmente, o desempenho será superior ao código que é compilado pela primeira vez para IL e, em seguida, é compilado para código nativo pelo compilador JIT.

- Você pode continuar a programar em C# ou em Visual Basic.

- Você pode continuar a aproveitar os recursos fornecidos pelo .NET Framework, incluindo sua biblioteca de classes, coleta de lixo, gerenciamento automático de memória e manipulação de exceção.

Para usuários de seus aplicativos, o .NET Native oferece estas vantagens:

- Tempos de execução mais rápidos para a maioria dos aplicativos e cenários.

- Tempos de inicialização mais rápidos para a maioria dos aplicativos e cenários.

- Custos baixos de implantação e atualização.

- Uso de memória do aplicativo otimizado.

> [!IMPORTANT]
> Para a maioria dos aplicativos e cenários, o .NET Native oferece tempos de inicialização significativamente mais rápidos e melhor desempenho quando comparado a um aplicativo compilado para IL ou para uma imagem NGEN. No entanto, os resultados podem variar. Para garantir que seu aplicativo se beneficiou dos aprimoramentos de desempenho do .NET nativo, você deve comparar seu desempenho com o da versão do seu aplicativo não - .NET Native. Para obter mais informações, consulte [visão geral da sessão de desempenho](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Mas o .NET Native envolve mais do que uma compilação para código nativo. Ele transforma a maneira que os aplicativos .NET Framework são criados e executados. Em particular:

- Durante a pré-compilação, partes necessárias do .NET Framework são vinculadas estaticamente ao seu aplicativo. Isso permite que o aplicativo seja executado com as bibliotecas de aplicativo local do .NET Framework e o compilador realize análises globais para proporcionar vantagens de desempenho. Como resultado, os aplicativos são inicializados consistentemente mais rápido mesmo depois de atualizações do .NET Framework.

- O tempo de execução .NET Native é otimizado para pré-compilação estática e na grande maioria dos casos, oferece um desempenho superior. Ao mesmo tempo, ele mantém os recursos de reflexão principais que os desenvolvedores acham tão produtivos.

- O .NET native usa o mesmo back-end como o C++ compilador, que é otimizado para cenários de pré-compilação estáticos.

.NET native é capaz de trazer os benefícios de desempenho do C++ gerenciado para desenvolvedores de código porque ele usa as ferramentas iguais ou semelhantes, como C++ nos bastidores, conforme mostrado nesta tabela.

||.NET Nativo|C++|
|-|----------------------------------------------------------------|-----------|
|Libraries|O .NET Framework + Tempo de Execução do Windows|Win32 + Tempo de Execução do Windows|
|Compilador|Compilador de otimização de UTC|Compilador de otimização de UTC|
|Implantado|Binários prontos para execução|Binários prontos para execução (ASM)|
|Tempo de execução|MRT.dll (tempo de execução de CLR mínimo)|CRT.dll (tempo de execução C)|

Para aplicativos do Windows para Windows 10, carregue os binários de compilação de código do .NET Native nos pacotes do aplicativo (arquivos .appx) para a Windows Store.

## <a name="in-this-section"></a>Nesta seção

Para obter mais informações sobre o desenvolvimento de aplicativos com compilação de código do .NET Nativo, consulte estes tópicos:

- [Introdução à compilação de código nativo do .NET: Passo a passo de experiência de desenvolvedor](../../../docs/framework/net-native/getting-started-with-net-native.md)

- [.NET native e compilação:](../../../docs/framework/net-native/net-native-and-compilation.md) Como o .NET Native compila seu projeto para código nativo.

- [Reflexão e .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [APIs que dependem de reflexão](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [Referência da API de reflexão](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [Serialização e metadados](../../../docs/framework/net-native/serialization-and-metadata.md)

- [Migrando seu aplicativo da Windows Store para .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

- [Solução de problemas gerais do .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
