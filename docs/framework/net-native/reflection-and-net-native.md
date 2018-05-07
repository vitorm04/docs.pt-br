---
title: Reflexão e .NET Nativo
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56107c5d8760f69a29d9e4ad6e1bd445d4831d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reflection-and-net-native"></a>Reflexão e .NET Nativo
No .NET Framework, o desenvolvimento gerenciado oferece suporte à metaprogramação por meio da API de reflexão. A reflexão permite inspecionar objetos em um aplicativo, chamar métodos em objetos descobertos por meio de inspeção, gerar novos tipos no tempo de execução e oferece suporte a muitos outros cenários de código dinâmico. Ele também oferece suporte à serialização e desserialização, o que permite que os valores do campo do objeto sejam mantidos e restaurados posteriormente. Todos esses cenários exigem o compilador do .NET Framework JIT (just-in-time) para gerar código nativo com base em metadados disponíveis.  
  
 O tempo de execução do [!INCLUDE[net_native](../../../includes/net-native-md.md)] não inclui um compilador JIT. Como resultado, todo o código nativo necessário deve ser gerado com antecedência. Um conjunto de heurística é usado para determinar qual código deve ser gerado, mas esses heurística não pode abranger todos os cenários de metaprogramação possíveis.  Portanto, você deve fornecer dicas para esses cenários metaprogramação usando [diretivas de tempo de execução](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Se o código de implementação ou de metadados necessário não está disponível em tempo de execução, seu aplicativo gerará uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) ou [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md). Estão disponíveis duas soluções de problemas que gerarão a entrada apropriada para seu arquivo de diretivas de tempo de execução, a qual elimina a exceção:  
  
-   A [solução de problemas MissingMetadataException](http://dotnet.github.io/native/troubleshooter/type.html) para tipos.  
  
-   A [solução de problemas MissingMetadataException](http://dotnet.github.io/native/troubleshooter/method.html) para métodos.  
  
> [!NOTE]
>  Para obter uma visão geral do processo de compilação do .NET Native que fornece informações de contexto sobre a necessidade de ter um arquivo das diretivas de tempo de execução, consulte [.NET Native e compilação](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Além disso, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] não permite refletir sobre membros particulares da biblioteca de classes do .NET Framework. Por exemplo, uma chamada para a propriedade <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> para recuperar os campos de um tipo de biblioteca de classes do .NET Framework retorna somente campos públicos ou protegidos.  
  
 Os tópicos a seguir fornecem a documentação conceitual e de referência necessária para oferecer suporte à reflexão e serialização nos seus aplicativos:  
  
-   [APIs que dependem de reflexão](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Referência da API de reflexão](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Consulte também  
 [Compilação de aplicativos com o .NET Native](../../../docs/framework/net-native/index.md)  
 [.NET Native e compilação](../../../docs/framework/net-native/net-native-and-compilation.md)
