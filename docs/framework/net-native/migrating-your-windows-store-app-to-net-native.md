---
title: Migrando seu aplicativo da Windows Store para .NET Nativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: 29
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 55414d4479ca3cca8a7b5fbb15e4982b5dd12aad
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Migrando seu aplicativo da Windows Store para .NET Nativo
[!INCLUDE[net_native](../../../includes/net-native-md.md)] fornece compilação estática dos aplicativos na Windows Store ou no computador do desenvolvedor. Isso difere da compilação dinâmica realizada para Aplicativos da Windows Store pelo compilador JIT (just-in-time) ou o [Gerador de Imagem Nativa (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) no dispositivo. Apesar das diferenças, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] tenta manter a compatibilidade com os [.NET para aplicativos da Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). Em geral, as coisas que funcionam em aplicativos do .NET para Windows Store também funcionam com [!INCLUDE[net_native](../../../includes/net-native-md.md)].  No entanto, em alguns casos, você pode encontrar alterações de comportamento. Este documento descreve essas diferenças entre os aplicativos padrão do .NET para Windows Store e o [!INCLUDE[net_native](../../../includes/net-native-md.md)] nas seguintes áreas:  
  
-   [Diferenças de tempo de execução geral](#Runtime)  
  
-   [Diferenças de programação dinâmica](#Dynamic)  
  
-   [Outras diferenças relacionadas à reflexão](#Reflection)  
  
-   [Cenários e APIs sem suporte](#Unsupported)  
  
-   [Diferenças do Visual Studio](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Diferenças de tempo de execução geral  
  
-   Exceções, como <xref:System.TypeLoadException>, que são geradas pelo compilador JIT quando um aplicativo é executado no CLR (common language runtime), geralmente resulta em erros de tempo de compilação quando processados por [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Não chame o método <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=fullName> de um thread de interface do usuário do aplicativo. Isso pode resultar em um deadlock em [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Não conte com ordenação de invocação do construtor de classe estática. No [!INCLUDE[net_native](../../../includes/net-native-md.md)], a ordem de invocação é diferente da ordem do tempo de execução padrão. (Mesmo com o tempo de execução padrão, você não deve confiar na ordem de execução de construtores de classe estáticos.)  
  
-   Loops infinitos sem fazer uma chamada (por exemplo, `while(true);`) em qualquer thread interromper o aplicativo. Da mesma forma, esperas grandes ou infinitas podem interromper o aplicativo.  
  
-   Certos ciclos de inicialização genéricos não geram exceções em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Por exemplo, o código a seguir gera uma exceção <xref:System.TypeLoadException> no CLR padrão. No [!INCLUDE[net_native](../../../includes/net-native-md.md)], não.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   Em alguns casos, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] fornece diferentes implementações das Bibliotecas de Classe do .NET Framework. Um objeto retornado de um método sempre implementará os membros do tipo retornado. No entanto, desde que sua implementação de backup seja diferente, você não poderá convertê-lo para o mesmo conjunto de tipos como realizado em outras plataformas .NET Framework. Por exemplo, em alguns casos, você não poderá converter o objeto de interface <xref:System.Collections.Generic.IEnumerable%601> retornado por métodos como <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=fullName> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=fullName> para `T[]`.  
  
-   O cache de WinInet não é habilitado por padrão em aplicativos .NET para Windows Store, mas é habilitado no [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Isso melhora o desempenho, mas tem implicações de conjunto de trabalho. Nenhuma ação do desenvolvedor é necessária.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Diferenças de programação dinâmica  
 O [!INCLUDE[net_native](../../../includes/net-native-md.md)] vincula estaticamente no código do .NET Framework para criar o código de aplicativo local para máximo desempenho. No entanto, os tamanhos binários precisam permanecer pequenos para que todo o .NET Framework não seja trazido. O compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] resolve esta limitação usando um redutor de dependência que remove referências ao código não usado. No entanto, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] pode não manter ou gerar algumas informações de tipo e código quando elas não podem ser deduzidas estaticamente no tempo de compilação, mas em vez disso, são recuperadas dinamicamente no tempo de execução.  
  
 O [!INCLUDE[net_native](../../../includes/net-native-md.md)] habilita a reflexão e programação dinâmica. No entanto, nem todos os tipos podem ser marcados para reflexão, porque isso tornaria o tamanho do código gerado grande demais (especialmente porque há suporte para reflexão nas APIs públicas do .NET Framework). O compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] faz escolhas inteligentes sobre quais tipos devem oferecer suporte à reflexão, mantém os metadados e gera código somente para esses tipos.  
  
 Por exemplo, a associação de dados necessita de um aplicativo para conseguir mapear nomes de propriedade às funções. Nos aplicativos .NET para Windows Store, o Common Language Runtime usa reflexão automaticamente para fornecer esse recurso para tipos nativos gerenciados e disponíveis publicamente. No [!INCLUDE[net_native](../../../includes/net-native-md.md)], o compilador inclui automaticamente os metadados para tipos aos quais você associa dados.  
  
 O compilador do [!INCLUDE[net_native](../../../includes/net-native-md.md)] também pode manipular tipos genéricos comumente usados como <xref:System.Collections.Generic.List%601> e <xref:System.Collections.Generic.Dictionary%602>, que funcionam sem necessitar de quaisquer dicas ou diretivas. A palavra-chave [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) também tem suporte dentro de certos limites.  
  
> [!NOTE]
>  Você deve testar todos os caminhos de código dinâmico completamente ao realizar a portabilidade do seu aplicativo para [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 A configuração padrão do [!INCLUDE[net_native](../../../includes/net-native-md.md)] é suficiente para a maioria dos desenvolvedores, mas alguns talvez queiram ajustar suas configurações usando um arquivo de diretivas de tempo de execução (.rd.xml). Além disso, em alguns casos, o compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] não consegue determinar quais metadados devem estar disponíveis para reflexão baseia-se em dicas, particularmente nos seguintes casos:  
  
-   Algumas construções <xref:System.Type.MakeGenericType%2A?displayProperty=fullName> e <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=fullName> não podem ser determinadas estaticamente.  
  
-   Como o compilador não pode determinar as instanciações, um tipo genérico sobre o qual você deseja refletir deverá ser especificado por diretivas de tempo de execução. Isso não é apenas porque todo o código deve ser incluído, mas sim porque a reflexão em tipos genéricos pode formar um ciclo infinito (por exemplo, quando um método genérico é invocado em um tipo genérico).  
  
> [!NOTE]
>  Diretivas de tempo de execução são definidas em um arquivo de diretivas de tempo de execução (.rd.xml). Para obter mais informações sobre como usar essa arquivo, consulte [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md). Para obter informações sobre as diretivas de tempo de execução, consulte [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 O [!INCLUDE[net_native](../../../includes/net-native-md.md)] também inclui ferramentas de perfil que ajudam o desenvolvedor a determinar quais tipos de fora do conjunto padrão devem suportar a reflexão.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Outras diferenças relacionadas à reflexão  
 Há uma série de outras diferenças individuais do comportamento relacionadas à reflexão entre aplicativos .NET para Windows Store e o [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 No [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Não há suporte para reflexão privada sobre tipos e membros da biblioteca de classes do .NET Framework. No entanto, é possível refletir sobre seus próprios tipos e membros privados, bem como tipos e membros em bibliotecas de terceiros.  
  
-   A propriedade <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=fullName> retorna `false` corretamente para um objeto <xref:System.Reflection.ParameterInfo> que representa um valor de retorno. Nos aplicativos .NET para Windows Store, ele retorna `true`. A Linguagem intermediária (IL) não oferece suporte a isso diretamente e interpretações são deixada para a linguagem.  
  
-   Membros públicos nas estruturas <xref:System.RuntimeFieldHandle> e <xref:System.RuntimeMethodHandle> não são suportadas. Esses tipos são suportados apenas para LINQ, árvores de expressão e inicialização de matriz estática.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=fullName> e <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=fullName> incluem membros ocultos em classes base e, portanto, podem ser substituídos sem substituições explícitas. Isso também é verdadeiro para outros métodos [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx).  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=fullName> e <xref:System.Type.MakeByRefType%2A?displayProperty=fullName> não falham quando você tentar criar certas combinações (por exemplo, uma matriz de byrefs).  
  
-   Você não pode usar reflexão para invocar os membros que têm parâmetros de ponteiro.  
  
-   Você não pode usar reflexão para obter ou definir um campo de ponteiro.  
  
-   Quando a contagem de argumentos está incorreta e o tipo de um dos argumentos está incorreto, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] gera um <xref:System.ArgumentException> em vez de um <xref:System.Reflection.TargetParameterCountException>.  
  
-   A serialização binária de exceções geralmente não é suportada. Como resultado, objetos não serializáveis não podem ser adicionados ao dicionário <xref:System.Exception.Data%2A?displayProperty=fullName>.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Cenários e APIs sem suporte  
 As seções a seguir listam cenários não suportados e APIs de desenvolvimento geral, interoperabilidade e tecnologias como HTTPClient e Windows Communication Foundation (WCF):  
  
-   [Desenvolvimento geral](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interoperabilidade](#Interop)  
  
-   [APIs sem suporte](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Diferenças de desenvolvimento geral  
 **Tipos de valor**  
  
-   Se você substituir os métodos <xref:System.ValueType.Equals%2A?displayProperty=fullName> e <xref:System.ValueType.GetHashCode%2A?displayProperty=fullName> para um tipo de valor, não chame as implementações de classe base. Em aplicativos .NET para Windows Store, esses métodos dependem de reflexão. No tempo de compilação, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] gera uma implementação que não depende de reflexão no tempo de execução. Isso significa que se você não substituir esses dois métodos, eles funcionarão conforme o esperado, porque [!INCLUDE[net_native](../../../includes/net-native-md.md)] gera a implementação no tempo de compilação. No entanto, substituir esses métodos, mas chamar a implementação de classe base, resulta em uma exceção.  
  
-   Não há suporte para tipos de valor maior do que um megabyte.  
  
-   Tipos de valor não podem ter um construtor padrão em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. (C# e Visual Basic proíbem construtores padrão em tipos de valor. No entanto, eles podem ser criados em IL.)  
  
 **Matrizes**  
  
-   Não há suporte para matrizes com um limite inferior diferente de zero. Normalmente, esses conjuntos são criados ao chamar a sobrecarga <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=fullName>.  
  
-   A criação dinâmica de matrizes multidimensionais não tem suporte. Essas matrizes geralmente são criados chamando uma sobrecarga do método <xref:System.Array.CreateInstance%2A?displayProperty=fullName> que inclui um parâmetro `lengths` ou chamando o método <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=fullName>.  
  
-   Não há suporte para matrizes multidimensionais com quatro ou mais dimensões, ou seja, com valor da propriedade <xref:System.Array.Rank%2A?displayProperty=fullName> quatro ou superior. Use [matrizes denteadas](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (uma matriz de matrizes) em vez disso. Por exemplo, `array[x,y,z]` é inválido, mas `array[x][y][z]` não é.  
  
-   Variação de matrizes multidimensionais não é suportada e causa uma exceção <xref:System.InvalidCastException> no tempo de execução.  
  
 **Genéricos**  
  
-   A expansão do tipo genérico infinito resulta em um erro do compilador. Por exemplo, esse código falha ao compilar:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **Ponteiros**  
  
-   Não há suporte para matrizes de ponteiros.  
  
-   Você não pode usar reflexão para obter ou definir um campo de ponteiro.  
  
 **Serialização**  
  
 O atributo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> não é suportado. Use o atributo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> em vez disso.  
  
 **Recursos**  
  
 O uso de recursos localizados com a classe <xref:System.Diagnostics.Tracing.EventSource> não é suportado. A propriedade <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=fullName> não define os recursos localizados.  
  
 **Delegados**  
  
 `Delegate.BeginInvoke` e `Delegate.EndInvoke` não são suportados.  
  
 **Async**  
  
 A lógica de threading em sobrecargas da tarefa IAsync não é suportada.  
  
 **APIs diversas**  
  
-   A propriedade <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=fullName> gera uma exceção <xref:System.PlatformNotSupportedException> se um atributo <xref:System.Runtime.InteropServices.GuidAttribute> não for aplicado ao tipo. O GUID é usado principalmente para suporte a COM.  
  
-   O método <xref:System.DateTime.Parse%2A?displayProperty=fullName> analisa corretamente as cadeias de caracteres que contêm datas curtas em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Contudo, ele não mantém a compatibilidade com as alterações na análise de data e hora descritas no artigos da Base de Dados de Conhecimento Microsoft [KB2803771](http://support.microsoft.com/kb/2803771) e [KB2803755](http://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=fullName> `("E")` é arredondado corretamente em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Em algumas versões do CLR, a cadeia de caracteres de resultado é truncada em vez de arredondada.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>Diferenças do HttpClient  
 Em [!INCLUDE[net_native](../../../includes/net-native-md.md)], a classe <xref:System.Net.Http.HttpClientHandler> usa internamente WinINet (por meio da classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx)) em vez das classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> usadas no .NET padrão para Aplicativos da Windows Store.  O WinINet não oferece suporte a todas as opções de configuração que a classe <xref:System.Net.Http.HttpClientHandler> suporta.  Portanto:  
  
-   Algumas das propriedades do recurso em <xref:System.Net.Http.HttpClientHandler> retornam `false` em [!INCLUDE[net_native](../../../includes/net-native-md.md)], considerando que retornam `true` nos aplicativos padrão .NET para Windows Store.  
  
-   Algumas das propriedades de configuração dos acessadores `get` sempre retornam um valor fixo no [!INCLUDE[net_native](../../../includes/net-native-md.md)] diferente do valor configurável padrão nos aplicativos .NET da Windows Store.  
  
 Algumas diferenças comportamentais adicionais são abrangidas nas subseções a seguir.  
  
 **Proxy**  
  
 A classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) não dá suporte para configurar ou substituir o proxy por solicitação.  Isso significa que todas as solicitações no [!INCLUDE[net_native](../../../includes/net-native-md.md)] usam o servidor de proxy configurado pelo sistema ou nenhum servidor de proxy, dependendo do valor da propriedade <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=fullName>.  Em aplicativos .NET para Windows Store, o servidor proxy é definido pela propriedade <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=fullName>.  Em [!INCLUDE[net_native](../../../includes/net-native-md.md)], definir <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=fullName> para um valor diferente de `null` gera uma exceção <xref:System.PlatformNotSupportedException>.  A propriedade <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=fullName> retorna `false` em [!INCLUDE[net_native](../../../includes/net-native-md.md)], considerando que retorna `true` nos aplicativos .NET Framework para Windows Store.  
  
 **Redirecionamento automático**  
  
 A classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) não permite que o número máximo de redirecionamentos automáticos seja configurado.  O valor da propriedade <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=fullName> é 50 por padrão nos aplicativos .NET para Windows Store e pode ser modificada. Em [!INCLUDE[net_native](../../../includes/net-native-md.md)], o valor desta propriedade é 10 e tentar modificá-la gera uma exceção <xref:System.PlatformNotSupportedException>.  A propriedade <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=fullName> retorna `false` em [!INCLUDE[net_native](../../../includes/net-native-md.md)], considerando que retorna `true` em aplicativos .NET para Windows Store.  
  
 **Descompactação automática**  
  
 Aplicativos .NET para Windows Store permitem definir a propriedade <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=fullName> para <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, ambas <xref:System.Net.DecompressionMethods.Deflate> e <xref:System.Net.DecompressionMethods.GZip>, ou <xref:System.Net.DecompressionMethods.None>.  [!INCLUDE[net_native](../../../includes/net-native-md.md)] somente suporta <xref:System.Net.DecompressionMethods.Deflate> junto com <xref:System.Net.DecompressionMethods.GZip> ou <xref:System.Net.DecompressionMethods.None>.  Tentar definir a propriedade <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> para <xref:System.Net.DecompressionMethods.Deflate> ou <xref:System.Net.DecompressionMethods.GZip> sozinho silenciosamente define-a para <xref:System.Net.DecompressionMethods.Deflate> e <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Cookies**  
  
 A manipulação de cookies é executada simultaneamente por <xref:System.Net.Http.HttpClient> e WinINet.  Os cookies do <xref:System.Net.CookieContainer> são combinados com cookies no cache de cookies do WinINet.  Remover um cookie do <xref:System.Net.CookieContainer> impede que <xref:System.Net.Http.HttpClient> envie o cookie, mas se o cookie já foi visto pelo WinINet e os cookies não foram excluídos pelo usuário, o WinINet o envia.  Não é possível programar a remoção automática de um cookie do WinINet usando a API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler> ou <xref:System.Net.CookieContainer>.  Definir a propriedade <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=fullName> para `false` faz com que apenas <xref:System.Net.Http.HttpClient> pare de enviar cookies; o WinINet ainda pode incluir os cookies na solicitação.  
  
 **Credenciais**  
  
 Em aplicativos .NET para Windows Store, as propriedades <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=fullName> e <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=fullName> funcionam de forma independente.  Além disso, a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> aceita qualquer objeto que implemente a interface <xref:System.Net.ICredentials>.  No [!INCLUDE[net_native](../../../includes/net-native-md.md)], definir a propriedade <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> para `true` faz com que a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> torne-se `null`.  Além disso, a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> pode ser definida somente para `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A> ou um objeto do tipo <xref:System.Net.NetworkCredential>.  Atribuir de qualquer outro objeto <xref:System.Net.ICredentials>, sendo o mais popular o <xref:System.Net.CredentialCache>, para a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A>, gera uma <xref:System.PlatformNotSupportedException>.  
  
 **Outros recursos sem suporte ou não configuráveis**  
  
 No [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   O valor da propriedade <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=fullName> sempre é <xref:System.Net.Http.ClientCertificateOption.Automatic>.  Em aplicativos .NET para Windows Store, o padrão é <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   A propriedade <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=fullName> não é configurável.  
  
-   A propriedade <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=fullName> sempre é `true`.  Em aplicativos .NET para Windows Store, o padrão é `false`.  
  
-   O cabeçalho `SetCookie2` em respostas será ignorado como obsoleto.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Diferenças de interoperabilidade  
 **APIs preteridas**  
  
 Várias APIs pouco usadas para a interoperabilidade com código gerenciado foram preteridas. Quando usadas com [!INCLUDE[net_native](../../../includes/net-native-md.md)], essas APIs pode gerar uma exceção <xref:System.NotImplementedException> ou <xref:System.PlatformNotSupportedException>, ou resultar em um erro do compilador. Em aplicativos .NET para Windows Store, essas APIs são marcadas como obsoletas, embora chamá-las gere um aviso do compilador em vez de um erro do compilador.  
  
 APIs preteridas para marshaling de `VARIANT`:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=fullName>|  
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=fullName> tem suporte, porém gera uma exceção em alguns cenários, por exemplo, quando usado com [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) ou variantes byref.  
  
 APIs preteridas para suporte a [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx):  
  
|Tipo|Membro|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=fullName>|Atributo não é suportado|  
  
 APIs preteridas para eventos clássicos de COM:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 APIs preteridas na interface do <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName>, sem suporte no [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
|Tipo|Membro|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName>|Todos os membros.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=fullName>|Todos os membros.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=fullName>|Todos os membros.|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>|  
  
 Outros recursos de interoperabilidade sem suporte:  
  
|Tipo|Membro|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=fullName>|Todos os membros.|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=fullName>|Todos os membros.|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 APIs de marshalling raramente usadas:  
  
|Tipo|Membro|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 **Invocação de plataforma e compatibilidade de interoperabilidade COM**  
  
 A maioria dos cenários de invocação de plataforma e interoperabilidade COM ainda são suportados no [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Em especial, toda a interoperabilidade com APIs do Tempo de Execução do Windows (WinRT) APIs e todo o marshaling necessário para o Tempo de Execução do Windows são suportados. Isso inclui suporte a marshaling para:  
  
-   Matrizes (incluindo <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=fullName>)  
  
-   `BStr`  
  
-   Representantes  
  
-   Cadeias de caracteres (Unicode, Ansi e HSTRING)  
  
-   Estruturas (`byref` e `byval`)  
  
-   Uniões  
  
-   Identificadores do Win32  
  
-   Todos os constructos do WinRT  
  
-   Suporte parcial aos tipos variantes de marshaling. Há suporte para os seguintes recursos:  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 No entanto, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] não oferece suporte aos seguintes:  
  
-   Usando os eventos clássicos do COM  
  
-   Implementando a interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName> em um tipo gerenciado  
  
-   Implementando a interface [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) em um tipo gerenciado por meio do atributo <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=fullName>. No entanto, observe que você não pode chamar objetos COM por meio de `IDispatch`, e o objeto gerenciado não pode implementar `IDispatch`.  
  
 Usar reflexão para invocar um método de invocação de plataforma não é suportado. Você pode contornar essa limitação envolvendo a chamada de método em outro método e usando reflexão para chamar o wrapper em vez disso.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Outras diferenças das APIs .NET para Windows Store  
 Esta seção lista as APIs restantes que não têm suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. O maior conjunto de APIs sem suporte são APIs do Windows Communication Foundation (WCF).  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Os tipos nos namespaces <xref:System.ComponentModel.DataAnnotations> e <xref:System.ComponentModel.DataAnnotations.Schema> não têm suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Eles incluem os seguintes tipos que estão presentes nos aplicativos .NET para Windows Store para o Windows 8:  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=fullName>|  
  
 **Visual Basic**  
  
 Visual Basic não é suportada atualmente no [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Os seguintes tipos nos namespaces <xref:Microsoft.VisualBasic> e <xref:Microsoft.VisualBasic.CompilerServices> não estão disponíveis em [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=fullName>|  
  
 **Contexto de reflexão (namespace System.Reflection.Context)**  
  
 A classe <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=fullName> não tem suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **RTC (System.Net.Http.Rtc)**  
  
 A classe <xref:System.Net.Http.RtcRequestFactory?displayProperty=fullName> não tem suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Os tipos nos [namespaces System.ServiceModel.*](http://msdn.microsoft.com/library/gg145010.aspx) não têm suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Eles incluem os seguintes tipos:  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=fullName>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=fullName>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultException?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=fullName>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=fullName>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=fullName>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=fullName>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=fullName>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=fullName>|  
  
### <a name="differences-in-serializers"></a>Diferenças nos serializadores  
 As seguintes diferenças envolvem serialização e desserialização com e classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer>:  
  
-   No [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não conseguem serializar ou desserializar uma classe derivada que tem um membro da classe base cujo tipo não é um tipo de serialização de raiz. Por exemplo, no código a seguir, tentar serializar ou desserializar `Y` resulta em um erro:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     O tipo `InnerType` não é conhecido pelo serializador, pois os membros da classe base não são percorridos durante a serialização.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não conseguem serializar uma classe ou estrutura que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>. Por exemplo, os seguintes tipos falham ao serializar ou desserializar:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> falha ao serializar o valor de objeto a seguir, porque não sabe o tipo exato de objeto a ser serializado:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> falha ao serializar ou desserializar se o tipo do objeto serializado é <xref:System.Xml.XmlQualifiedName>.  
  
-   Todos os serializadores (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer>) falham ao gerar o código de serialização para tipo <xref:System.Xml.Linq.XElement?displayProperty=fullName> ou para um tipo que contém <xref:System.Xml.Linq.XElement>. Eles exibem erros de tempo de compilação em vez disso.  
  
-   Não há garantia que os seguintes construtores dos tipos de serialização funcionem conforme o esperado:  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=fullName>  
  
-   O <xref:System.Xml.Serialization.XmlSerializer> falha ao gerar o código para um tipo que tem métodos atribuídos com qualquer um dos seguintes atributos:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   O <xref:System.Xml.Serialization.XmlSerializer> não aceita a interface de serialização personalizada <xref:System.Xml.Serialization.IXmlSerializable>. Se você tiver uma classe que implementa essa interface, <xref:System.Xml.Serialization.XmlSerializer> considera o tipo como um objeto CLR (POCO) antigo simples, serializando apenas suas propriedades públicas.  
  
-   Serializar um objeto <xref:System.Exception> simples, como a seguir, não funciona bem com <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Diferenças do Visual Studio  
 **Exceções e depuração**  
  
 Quando você estiver executando aplicativos compilados usando [!INCLUDE[net_native](../../../includes/net-native-md.md)] no depurador, as exceções de primeira chance são habilitadas para os seguintes tipos de exceção:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Criando aplicativos**  
  
 Use as ferramentas de criação x86 usadas por padrão pelo Visual Studio. Não recomendamos usar as ferramentas AMD64 MSBuild, que se encontram em C:\Program Files (x86)\MSBuild\12.0\bin\amd64, pois podem criar problemas de compilação.  
  
 **Criadores de perfil**  
  
-   O criador de perfil de CPU do Visual Studio e o criador de perfil de memória XAML não exibem o Just-My-Code corretamente.  
  
-   O gerador de perfil de memória XAML não exibe corretamente os dados da pilha gerenciada.  
  
-   O gerador de perfil de CPU não identifica corretamente módulos e exibe nomes de função de prefixo.  
  
 **Projetos da biblioteca de teste de unidade**  
  
 Habilitar [!INCLUDE[net_native](../../../includes/net-native-md.md)] em uma biblioteca de teste de unidade para aplicativos da Windows Store não é suportado e causa erros de compilação no projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md)   
 [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Visão geral do .NET para aplicativos da Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)   
 [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

