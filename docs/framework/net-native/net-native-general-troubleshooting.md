---
title: Solução de problemas gerais do .NET Nativo
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5f61b0e250c4f51a966bc60959f7559d8e2fe2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049395"
---
# <a name="net-native-general-troubleshooting"></a>Solução de problemas gerais do .NET Nativo

Este tópico descreve como solucionar problemas potenciais que você pode encontrar ao desenvolver aplicativos com o .NET Native.

- **Lo** Sua janela de saída de compilação não foi atualizada corretamente.

  **Resolução** A janela de saída da compilação não é atualizada até que a compilação seja concluída. Os tempos de compilação podem levar vários minutos, por isso pode ocorrer um atraso para exibir as atualizações.

- **Lo** O tempo de compilação de varejo do aplicativo para o ARM aumentou.

  **Resolução** Quando você implanta um aplicativo em seu dispositivo ARM, a infraestrutura de .NET Native é invocada. Essa compilação executa um grande número de otimizações, garantindo que semânticas não estáticas como reflexão continuem a funcionar. Além disso, a parte do .NET Framework que o aplicativo usa está vinculada estaticamente para otimizar o desempenho e também precisa ser compilada em código nativo. É por isso que a compilação leva mais tempo.

  No entanto, o tempo de compilação ainda está dentro de um minuto da compilação padrão para a maioria dos aplicativos em uma máquina de desenvolvimento padrão.  Normalmente, apenas gerar imagens nativas para o .NET Framework em uma máquina de desenvolvimento padrão leva vários minutos.  Mesmo com todas as otimizações para melhorar o código gerado e incluindo o .NET Framework, os tempos de compilação do aplicativo são normalmente de um ou dois minutos.

  Continuamos a trabalhar para aprimorar o desempenho da compilação investigando a multi-threaded compilação e outras otimizações.

- **Lo** Você não sabe se seu aplicativo foi compilado usando .NET Native.

  **Resolução** Se o compilador de .NET Native for invocado, você perceberá tempos de compilação mais longos e o Gerenciador de tarefas mostrará vários processos de componentes de .NET Native, como ILC. exe e nutc_driver. exe.

  Depois de criar com êxito seu projeto com .net Native, você encontrará a saída em obj\\*config*\ *Arch*\\*ProjectName*. ilc\out.  O conteúdo do pacote nativo final pode ser encontrado em bin\\*arch*\\*config*\AppX. O conteúdo do pacote nativo final estará em \bin\\*arch*\\*config*\AppX se você tiver implantado o aplicativo.

- **Lo** Seu aplicativo compilado .NET Native está lançando exceções de tempo de execução (geralmente exceções [MissingMetadataException](missingmetadataexception-class-net-native.md) ou [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) ) que não foi gerada quando compiladas sem .net Native.

  **Resolução** As exceções são geradas porque .NET Native não forneceu os metadados ou o código de implementação que, de outra forma, está disponível por meio de reflexão. (Para obter mais informações, consulte [.NET Native e Compilação](net-native-and-compilation.md).) Para eliminar a exceção, você precisa adicionar uma entrada ao seu [arquivo (rd.xml) de diretivas de tempo de execução](runtime-directives-rd-xml-configuration-file-reference.md) para que a cadeia de ferramentas do .NET Native possa tornar o código de implementação ou os metadados disponíveis em tempo de execução. Há duas soluções de problemas disponíveis que criarão a entrada necessária para adicionar ao seu arquivo de diretivas de tempo de execução:

  - A [solução de problemas MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) para tipos.

  - A [solução de problemas MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) para métodos.

  Para obter mais informações, consulte [Reflexão e .NET Native](reflection-and-net-native.md).

## <a name="see-also"></a>Consulte também

- [Migrando seu aplicativo da Windows Store para .NET Native](migrating-your-windows-store-app-to-net-native.md)
