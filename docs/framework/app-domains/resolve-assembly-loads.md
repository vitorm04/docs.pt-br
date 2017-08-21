---
title: Resolvendo carregamentos de assembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0fe3347c640b7e99487d630cbfac97e774bda7bb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="resolving-assembly-loads"></a>Resolvendo carregamentos de assembly
O .NET Framework fornece o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> para aplicativos que exigem maior controle sobre o carregamento do assembly. Ao tratar esse evento, seu aplicativo pode carregar um assembly no contexto de carga de fora dos caminhos normais de investigação, selecionar qual das várias versões de assembly carregar, emitir um assembly dinâmico e retorná-lo, etc. Este tópico fornece orientação para a manipulação do evento <xref:System.AppDomain.AssemblyResolve>.  
  
> [!NOTE]
>  Para resolver carregamentos de assembly no contexto de somente reflexão, use o evento <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=fullName> em vez disso.  
  
## <a name="how-the-assemblyresolve-event-works"></a>Como o evento AssemblyResolve funciona  
 Quando você registra um manipulador para o evento <xref:System.AppDomain.AssemblyResolve>, o manipulador é invocado sempre que o tempo de execução falha ao se associar a um assembly por nome. Por exemplo, chamar os seguintes métodos usando o código do usuário pode fazer com que o evento <xref:System.AppDomain.AssemblyResolve> seja gerado:  
  
-   Uma sobrecarga de método <xref:System.AppDomain.Load%2A?displayProperty=fullName> ou uma sobrecarga de método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> cujo primeiro argumento é uma cadeia de caracteres que representa o nome de exibição do assembly a ser carregado (ou seja, a cadeia de caracteres retornada pela propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName>).  
  
-   Uma sobrecarga de método <xref:System.AppDomain.Load%2A?displayProperty=fullName> ou uma sobrecarga de método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> cujo primeiro argumento é um objeto <xref:System.Reflection.AssemblyName> que identifica o assembly a ser carregado.  
  
-   Uma sobrecarga de método <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>.  
  
-   Uma sobrecarga de método <xref:System.AppDomain.CreateInstance%2A?displayProperty=fullName> ou <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName> que cria uma instância de um objeto em outro domínio de aplicativo.  
  
### <a name="what-the-event-handler-does"></a>O que o manipulador de eventos faz  
 O manipulador do evento <xref:System.AppDomain.AssemblyResolve> recebe o nome de exibição do assembly a ser carregado na propriedade <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName>. Se o manipulador não reconhecer o nome do assembly, ele retornará nulo (`Nothing` no Visual Basic, `nullptr` no Visual C++).  
  
 Se o manipulador reconhecer o nome do assembly, ele poderá carregar e retornar um assembly que atende à solicitação. A lista a seguir descreve alguns cenários de exemplo.  
  
-   Se o manipulador conhecer o local de uma versão do assembly, ele poderá carregar o assembly usando o método <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName> e poderá retornar o assembly carregado se tiver êxito.  
  
-   Se o manipulador tiver acesso a um banco de dados de assemblies armazenados como matrizes de bytes, ele poderá carregar uma matriz de bytes usando uma das sobrecargas do método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> que usa uma matriz de bytes.  
  
-   O manipulador pode gerar um assembly dinâmico e retorná-lo.  
  
> [!NOTE]
>  O manipulador deve carregar o assembly no contexto de origem de carga, no contexto de carregamento ou sem contexto. Se o manipulador carregar o assembly no contexto de somente reflexão usando o método <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=fullName> ou o <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=fullName>, a tentativa de carregamento que gerou o evento <xref:System.AppDomain.AssemblyResolve> falhará.  
  
 É responsabilidade do manipulador de eventos retornar um assembly adequado. O manipulador pode analisar o nome de exibição do assembly solicitado passando o valor da propriedade <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName> para o construtor <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>. A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o manipulador pode usar a propriedade <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> para determinar se a solicitação atual é uma dependência de outro assembly. Essas informações podem ajudar a identificar um assembly que atenderá à dependência.  
  
 O manipulador de eventos pode retornar uma versão diferente do assembly do que a versão que foi solicitada.  
  
 Na maioria dos casos, o assembly que é retornado pelo manipulador aparece no contexto de carga, independentemente do contexto em que o manipulador o carrega. Por exemplo, se o manipulador usar o método <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> para carregar um assembly no contexto de origem de carga, o assembly aparecerá no contexto de carga quando o manipulador o retornar. No entanto, no seguinte caso, o assembly aparece sem contexto quando o manipulador o retorna:  
  
-   O manipulador carrega um assembly sem contexto.  
  
-   A propriedade <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> não é nula.  
  
-   O assembly solicitante (ou seja, o assembly que é retornado pela propriedade <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName>) foi carregado sem contexto.  
  
 Para obter informações sobre os contextos, consulte a sobrecarga de método <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=fullName>.  
  
 Várias versões do mesmo assembly podem ser carregadas no mesmo domínio do aplicativo. Essa prática não é recomendada, pois ela pode levar a problemas de atribuição de tipo. Confira [Práticas recomendadas para carregamento de assemblies](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>O que o manipulador de eventos não deve fazer  
 A regra principal para tratamento do evento <xref:System.AppDomain.AssemblyResolve> é que você não deve tentar retornar um assembly que não reconhece. Ao escrever o manipulador, você deve saber quais assemblies podem fazer com que o evento seja acionado. O manipulador deve retornar nulo para outros assemblies.  
  
> [!IMPORTANT]
>  Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], o evento <xref:System.AppDomain.AssemblyResolve> é gerado para assemblies satélite. Essa alteração afeta um manipulador de eventos que foi escrito para uma versão anterior do .NET Framework, se o manipulador tenta resolver todas as solicitações de carga do assembly. Os manipuladores de eventos que ignoram assemblies que eles não reconhecem não são afetados por essa alteração: eles retornam nulo, e os mecanismos normais de fallback são seguidos.  
  
 Ao carregar um assembly, o manipulador de eventos não deve usar nenhuma das sobrecargas de método <xref:System.AppDomain.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> que possam fazer com que o evento <xref:System.AppDomain.AssemblyResolve> seja gerado recursivamente, pois isso poderia levar a um excedente de pilha. (Confira a lista fornecida anteriormente neste tópico.) Isso acontece mesmo se você fornecer tratamento de exceções para a solicitação de carga, pois nenhuma exceção será gerada até que todos os manipuladores de eventos tenham retornado. Desse modo, o seguinte código resultará em um excedente de pilha se `MyAssembly` não for encontrado:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)] [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)] [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Práticas recomendadas para carregamento de assemblies](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)   
 [Uso de domínios do aplicativo](../../../docs/framework/app-domains/use.md)

