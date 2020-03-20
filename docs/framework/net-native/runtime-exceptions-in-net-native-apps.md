---
title: Exceções em runtime em aplicativos do .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180946"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Exceções em runtime em aplicativos do .NET Native
É importante testar os builds de versão do seu aplicativo da Plataforma Universal do Windows nas respectivas plataformas de destino, porque as configurações de depuração e de lançamento são completamente diferentes. Por padrão, a configuração de depuração usa o runtime do .Net Core para compilar seu aplicativo, mas a configuração de lançamento usa .NET Native para compilar seu aplicativo em código nativo.  
  
> [!IMPORTANT]
> Para obter informações sobre como lidar com as exceções [MissingMetadataException,](missingmetadataexception-class-net-native.md) [MissingInteropDataException](missinginteropdataexception-class-net-native.md)e [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceções que você pode encontrar ao testar as versões de versão do seu aplicativo, consulte "Passo 4: resolver manualmente metadados ausentes: no tópico [Como Começar,](getting-started-with-net-native.md) bem como [Diretivas de Reflexão e .NET Nativa](reflection-and-net-native.md) e [Runtime (rd.xml) Referência de arquivo de configuração](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Builds de depuração e de versão  
 Quando o build de depuração é executado no runtime do .Net Core, ele não foi compilado para código nativo. Isso torna todos os serviços normalmente fornecidos pelo runtime disponíveis para seu aplicativo.  
  
 Por outro lado, o build de versão é compilado em código nativo para suas plataformas de destino, remove a maioria das dependências de bibliotecas e runtimes externos e otimiza muito o código para obter o máximo de desempenho.  
  
 Quando você depura builds de versão que são compilados usando o .NET Native:  
  
- Você usa o mecanismo de depuração do .NET Native, que é diferente das ferramentas de depuração normais do .NET.  
  
- O tamanho de seu executável é reduzido tanto quanto possível. Uma das maneiras pelas quais o .NET Native reduz o tamanho de um executável é cortando significativamente as mensagens de exceção de runtime, um tópico discutido em maiores detalhes na seção [Mensagens de exceção de runtime](#Messages).  
  
- Seu código é altamente otimizado. Isso significa que inlining é usado sempre que possível. (O inlineamento move o código de rotinas externas para a rotina de chamadas.)   O fato de o .NET Native fornecer um tempo de execução especializado e implementar a inlineação agressiva afeta a pilha de chamadas exibida ao depurar.  Para obter mais informações, consulte a seção [Pilha de chamadas de runtime](#CallStack).  
  
> [!NOTE]
> Você pode controlar se os builds de depuração e de versão são compilados com a cadeia de ferramentas do .NET Native, marcando ou desmarcando a caixa **Compilar com cadeia de ferramentas do .NET Native**.   No entanto, observe que a Windows Store sempre compilará a versão de produção do seu aplicativo com a cadeia de ferramentas do .NET Native.  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a>Mensagens de exceção de runtime  
 Para minimizar o tamanho do executável do aplicativo, o .NET Native não inclui o texto completo das mensagens de exceção. Como resultado, exceções de runtime geradas em builds de versão podem não exibir o texto completo das mensagens de exceção. Em vez disso, o texto pode conter uma subcadeia de caracteres junto com um link para mais informações. Por exemplo, as informações de exceção podem aparecer como:  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Se você precisar que a mensagem de exceção completa, execute o build de depuração em vez disso. Por exemplo, as informações de exceção anteriores do build de versão podem aparecer da seguinte maneira no build de depuração:  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a>Pilha de chamadas de runtime  
 Devido ao inlining e outras otimizações, a pilha de chamadas exibida por um aplicativo compilado pela cadeia de ferramentas do .NET Native pode não lhe ajudar a identificar claramente o caminho para uma exceção de runtime.  
  
 Para obter a pilha completa, execute o build de depuração em vez disso.  
  
## <a name="see-also"></a>Confira também

- [Depurando aplicativos universais do Windows do .NET Native](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Introdução](getting-started-with-net-native.md)
