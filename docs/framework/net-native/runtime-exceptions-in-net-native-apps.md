---
title: Exceções em tempo de execução em aplicativos do .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da30ae3f32ebbfabbdf35dd939c27b8d88e7e755
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696861"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Exceções em tempo de execução em aplicativos do .NET Native
É importante testar os builds de versão do seu aplicativo da Plataforma Universal do Windows nas respectivas plataformas de destino, porque as configurações de depuração e de lançamento são completamente diferentes. Por padrão, a configuração de depuração usa o tempo de execução do .Net Core para compilar seu aplicativo, mas a configuração de lançamento usa .NET Native para compilar seu aplicativo em código nativo.  
  
> [!IMPORTANT]
>  Para obter informações sobre como lidar com o [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), e [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceções que você pode encontrar ao testar as versões de lançamento do seu aplicativo, consulte "etapa 4: Resolver manualmente metadados ausentes: na [guia de Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md) tópico, bem como [reflexão e .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) e [diretivas de tempo de execução (RD. xml) a referência de arquivo de configuração](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Builds de depuração e de versão  
 Quando o build de depuração é executado no tempo de execução do .Net Core, ele não foi compilado para código nativo. Isso torna todos os serviços normalmente fornecidos pelo tempo de execução disponíveis para seu aplicativo.  
  
 Por outro lado, o build de versão é compilado em código nativo para suas plataformas de destino, remove a maioria das dependências de bibliotecas e tempos de execução externos e otimiza muito o código para obter o máximo de desempenho.  
  
 Quando você depura builds de versão que são compilados usando o .NET Native:  
  
-   Você usa o mecanismo de depuração do .NET Native, que é diferente das ferramentas de depuração normais do .NET.  
  
-   O tamanho de seu executável é reduzido tanto quanto possível. Uma das maneiras pelas quais o .NET Native reduz o tamanho de um executável é cortando significativamente as mensagens de exceção de tempo de execução, um tópico discutido em maiores detalhes na seção [Mensagens de exceção de tempo de execução](#Messages).  
  
-   Seu código é altamente otimizado. Isso significa que inlining é usado sempre que possível. (O inlining move código de rotinas externas para a rotina chamadora.)   O fato de que o .NET Native fornece um tempo de execução especializado e implementa inlining agressivo afeta a pilha de chamadas que é exibida durante a depuração.  Para obter mais informações, consulte a seção [Pilha de chamadas de tempo de execução](#CallStack).  
  
> [!NOTE]
>  Você pode controlar se os builds de depuração e de versão são compilados com a cadeia de ferramentas do .NET Native, marcando ou desmarcando a caixa **Compilar com cadeia de ferramentas do .NET Native**.   No entanto, observe que a Windows Store sempre compilará a versão de produção do seu aplicativo com a cadeia de ferramentas do .NET Native.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Mensagens de exceção de tempo de execução  
 Para minimizar o tamanho do executável do aplicativo, o .NET Native não inclui o texto completo das mensagens de exceção. Como resultado, exceções de tempo de execução geradas em builds de versão podem não exibir o texto completo das mensagens de exceção. Em vez disso, o texto pode conter uma subcadeia de caracteres junto com um link para mais informações. Por exemplo, as informações de exceção podem aparecer como:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Se você precisar que a mensagem de exceção completa, execute o build de depuração em vez disso. Por exemplo, as informações de exceção anteriores do build de versão podem aparecer da seguinte maneira no build de depuração:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Pilha de chamadas de tempo de execução  
 Devido ao inlining e outras otimizações, a pilha de chamadas exibida por um aplicativo compilado pela cadeia de ferramentas do .NET Native pode não lhe ajudar a identificar claramente o caminho para uma exceção de tempo de execução.  
  
 Para obter a pilha completa, execute o build de depuração em vez disso.  
  
## <a name="see-also"></a>Consulte também
- [Depurando aplicativos universais do Windows nativo .NET](https://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)
- [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md)
