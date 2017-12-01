---
title: "Caractere de codificação no .NET"
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
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce7c8ff2154b8503b0ef73954464f380f520c3f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="character-encoding-in-net"></a>Caractere de codificação no .NET
Os caracteres são entidades abstratas que podem ser representadas de muitas maneiras diferentes. Uma codificação de caracteres é um sistema que emparelha cada caractere em um conjunto de caracteres com suporte com algum valor que representa esse caractere. Por exemplo, o código Morse é uma codificação de caracteres que emparelha cada caractere do alfabeto romano com um padrão de pontos e traços adequados para transmissão por linhas telegráficas. Uma codificação de caracteres para computadores emparelha cada caractere em um conjunto de caracteres com suporte com um valor numérico que representa esse caractere. Uma codificação de caracteres tem dois componentes distintos:  
  
-   Um codificador, que converte uma sequência de caracteres em uma sequência de valores numéricos (bytes).  
  
-   Um decodificador, que converte uma sequência de bytes em uma sequência de caracteres.  
  
 A codificação de caracteres descreve as regras por meio das quais um codificador e um decodificador são operados. Por exemplo, a <xref:System.Text.UTF8Encoding> classe descreve as regras de codificação e decodificação de formato de transformação de 8 bits Unicode (UTF-8), que usa um a quatro bytes para representar um único caractere Unicode. Codificar e decodificar também podem incluir a validação. Por exemplo, a <xref:System.Text.UnicodeEncoding> classe verifica todos os substitutos para certificar-se de que constituem os pares substitutos válido. (Um par alternativo consiste em um caractere com um ponto de código que varia de U+D800 a U+DBFF seguido por um caractere com um ponto de código que varia de U+DC00 a U+DFFF.)  Uma estratégia de fallback determina como um codificador lida com caracteres inválidos ou como um decodificador lida com bytes inválidos.  
  
> [!WARNING]
>  Classes de codificação do .NET fornecem uma maneira de armazenar e converter dados de caractere. Elas não devem ser usadas para armazenar dados binários no formato de cadeia de caracteres. Dependendo da codificação usada, a conversão de dados binários em formato de cadeia de caracteres com classes de codificação pode introduzir um comportamento inesperado e produzir dados imprecisos ou corrompidos. Para converter dados binários em um formulário de cadeia de caracteres, use o <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> método.  
  
 .NET usa a codificação UTF-16 (representado pela <xref:System.Text.UnicodeEncoding> classe) para representar caracteres e cadeias de caracteres. Aplicativos que segmentam o Common Language Runtime e usam codificadores para mapear representações de caracteres Unicode com suporte pelo common language runtime para outros esquemas de codificação. Eles usam decodificadores para mapear caracteres de codificações não Unicode para Unicode.  
  
 Este tópico é composto pelas seguintes seções:  
  
-   [Codificações no .NET](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
-   [Selecionando uma classe de codificação](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
-   [Usando um objeto de codificação](../../../docs/standard/base-types/character-encoding.md#Using)  
  
-   [Escolhendo uma estratégia de fallback](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
-   [Implementando uma estratégia de fallback personalizada](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>Codificações no .NET  
 Todos os caracteres codificação classes no .NET herdam o <xref:System.Text.Encoding?displayProperty=nameWithType> classe, que é uma classe abstrata que define a funcionalidade comum para todas as codificações de caracteres. Para acessar os objetos de codificação individuais implementados no .NET, faça o seguinte:  
  
-   Use as propriedades estáticas do <xref:System.Text.Encoding> classe, que retornam objetos que representam as codificações de caractere padrão disponíveis no .NET (ASCII, UTF-7, UTF-8, UTF-16 e UTF-32). Por exemplo, o <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.Text.UnicodeEncoding> objeto. Cada objeto usa o fallback de substituição para lidar com cadeias de caracteres que ele não consegue codificar e bytes que ele não consegue decodificar. (Para obter mais informações, consulte a seção [Replacement Fallback (Fallback de substituição)](../../../docs/standard/base-types/character-encoding.md#Replacement).)  
  
-   Chame o construtor de classe da codificação. A instância de objetos para as codificações ASCII, UTF-7, UTF-8, UTF-16 e UTF-32 podem ser criadas dessa forma. Por padrão, cada objeto usa fallback de substituição para manipular as cadeias de caracteres que ele não consegue codificar e bytes que ele não consegue decodificar, mas, em vez disso, você pode especificar que uma exceção seja gerada. (Para obter mais informações, consulte as seções [Fallback de substituição](../../../docs/standard/base-types/character-encoding.md#Replacement) e [Fallback de exceção](../../../docs/standard/base-types/character-encoding.md#Exception).)  
  
-   Chamar o <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> construtor e passá-lo em um inteiro que representa a codificação. Os objetos de codificação padrão usam o fallback de substituição e a página de código e o DBCS (conjunto de caracteres de dois bytes) que codificam objetos usam o fallback que melhor se ajusta para manipular cadeias de caracteres que eles não conseguem codificar e bytes que eles não conseguem decodificar. (Para obter mais informações, consulte a seção [Best-Fit Fallback (Fallback de melhor ajuste)](../../../docs/standard/base-types/character-encoding.md#BestFit).)  
  
-   Chamar o <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> método, que retorna qualquer padrão, página de código ou DBCS codificação disponível no .NET. As sobrecargas permitem especificar um objeto de fallback para o codificador e o decodificador.  
  
> [!NOTE]
>  O padrão Unicode atribui um ponto de código (um número) e um nome a cada caractere em todos os scripts com suporte. Por exemplo, o caractere "A" é representado pelo ponto de código de U+0041 e o nome "LETRA MAIÚSCULA LATINA A". As codificações UTF (Unicode Transformation Format) definem maneiras de codificar esse ponto de código em uma sequência de um ou mais bytes. Um esquema de codificação Unicode simplifica o desenvolvimento de aplicativos prontos para o mundo, porque ele permite que qualquer conjunto de caracteres sejam representados em uma única codificação. Os desenvolvedores de aplicativos não precisam mais controlar o esquema de codificação usado para gerar caracteres para um idioma específico ou sistema de gravação e os dados podem ser compartilhados entre sistemas internacionalmente sem serem corrompidos.  
>   
>  O .NET dá suporte a três codificações definidas pelo padrão Unicode: UTF-8, UTF-16 e UTF-32. Para obter mais informações, consulte Padrão Unicode na [página inicial do Unicode](http://go.microsoft.com/fwlink/?LinkId=37123).  
  
 Você pode recuperar informações sobre todas as codificações disponíveis no .NET chamando o <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> método. O .NET dá suporte aos sistemas de codificação de caracteres listados na tabela a seguir.  
  
|Codificando|Classe|Descrição|Vantagens/desvantagens|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|Codifica um intervalo limitado de caracteres usando os menores sete bits de um byte.|Como essa codificação só dá suporte a valores de caracteres de U+0000 a U+007F, na maioria dos casos, ela é inadequada para aplicativos internacionalizados.|  
|UTF-7|<xref:System.Text.UTF7Encoding>|Representa caracteres como sequências de caracteres ASCII de 7 bits. Caracteres Unicode não ASCII são representados por uma sequência de escape de caracteres ASCII.|O UTF-7 dá suporte a protocolos como email e protocolos de grupos de notícias. No entanto, o UTF-7 não é particularmente seguro ou robusto. Em alguns casos, alterar um bit pode alterar radicalmente a interpretação de toda uma cadeia de caracteres UTF-7. Em outros casos, diferentes cadeias de caracteres UTF-7 podem codificar o mesmo texto. Para as sequências que incluem caracteres não ASCII, o UTF-7 requer mais espaço do que o UTF-8 e a codificação/decodificação é mais lenta. Consequentemente, você deve usar o UTF-8 em vez do UTF-7, se possível.|  
|UTF-8|<xref:System.Text.UTF8Encoding>|Representa cada ponto de código Unicode como uma sequência de um a quatro bytes.|O UTF-8 dá suporte a tamanhos de dados de 8 bits e funciona bem com muitos sistemas operacionais existentes. Para o intervalo de caracteres ASCII, o UTF-8 é idêntico à codificação ASCII e permite um conjunto mais amplo de caracteres. No entanto, para scripts CJK (chinês-japonês-coreano), o UTF-8 pode exigir três bytes para cada caractere e pode eventualmente gerar tamanhos de dados maiores do que o UTF-16. Observe que, às vezes, a quantidade de dados ASCII, como tags HTML, justifica o tamanho maior do intervalo CJK.|  
|UTF-16|<xref:System.Text.UnicodeEncoding>|Representa cada ponto de código Unicode como uma sequência de um a dois inteiros de 16 bits. Os caracteres Unicode mais comuns exigem apenas um ponto de código UTF-16, embora os caracteres suplementares Unicode (U+10000 e maiores) exigem dois pontos de código UTF-16 alternativos. Há suporte para as ordens de byte little endian e big endian.|Codificação UTF-16 é usada pelo common language runtime para representar <xref:System.Char> e <xref:System.String> valores e ele é usado pelo sistema operacional Windows para representar `WCHAR` valores.|  
|UTF-32|<xref:System.Text.UTF32Encoding>|Representa cada ponto de código Unicode como um inteiro de 32 bits. Há suporte para as ordens de byte little endian e big endian.|A codificação UTF-32 é usada quando aplicativos desejam evitar o comportamento do ponto de código alternativo de codificação UTF-16 em sistemas operacionais para os quais o espaço codificado é muito importante. Glifos únicos renderizados em uma tela ainda podem ser codificados com mais de um caractere UTF-32.|  
|Codificações ANSI/ISO||Fornece suporte a uma variedade de páginas de código. Em sistemas operacionais Windows, páginas de código são usadas para oferecer suporte a um idioma específico ou a um grupo de idiomas. Para uma tabela que lista as páginas de código com suporte pelo .NET, consulte o <xref:System.Text.Encoding> classe. Você pode recuperar um objeto de codificação para uma página de código específico ao chamar o <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> método.|Uma página de código contém 256 pontos de código e é baseada em zero. Na maioria das páginas de código, os pontos de código de 0 a 127 representam o conjunto de caracteres ASCII e pontos de código de 128 a 255 diferem significativamente entre páginas de código. Por exemplo, a página de código 1252 fornece os caracteres para sistemas com alfabeto latino, incluindo inglês, alemão e francês. Os últimos 128 pontos de código na página de código 1252 contêm os caracteres de acentuação. A página de código 1253 fornece códigos de caracteres que são necessários no sistema alfabético grego. Os últimos 128 pontos de código na página de código 1253 contêm os caracteres gregos. Como resultado, um aplicativo que se baseia em páginas de código ANSI não pode armazenar grego e alemão no mesmo fluxo de texto, a menos que inclua um identificador que indique a página de código referenciada.|  
|Codificações de conjunto de caracteres de byte duplo (DBCS)||Oferece suporte a idiomas, como chinês, japonês e coreano, que contêm mais de 256 caracteres. Um DBCS, um par de pontos de código (de byte duplo) representa cada caractere. O <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> propriedade retorna `false` para codificações DBCS. Você pode recuperar um objeto de codificação para um determinado DBCS chamando o <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> método.|Um DBCS, um par de pontos de código (de byte duplo) representa cada caractere. Quando um aplicativo manipula dados DBCS, o primeiro byte de um caractere DBCS (o byte inicial) é processado em combinação com o byte final que vem imediatamente a seguir. Como um único par de pontos de código de byte duplo pode representar caracteres diferentes dependendo da página de código, esse esquema ainda não permite a combinação dos dois idiomas, como japonês e chinês no mesmo fluxo de dados.|  
  
 Essas codificações permitem que você trabalhe com caracteres Unicode, bem como com codificações mais comumente usadas em aplicativos herdados. Além disso, você pode criar uma codificação personalizada definindo uma classe que deriva de <xref:System.Text.Encoding> e substituindo a seus membros.  
  
### <a name="platform-notes-includenetcoreincludesnet-core-mdmd"></a>Notas de plataforma: [!INCLUDE[net_core](../../../includes/net-core-md.md)]  
 Por padrão, o [!INCLUDE[net_core](../../../includes/net-core-md.md)] não disponibiliza nenhuma codificação de página de código diferente da página de código 28591 e das codificações Unicode, como UTF-8 e UTF-16. No entanto, você pode adicionar as codificações de página de código encontradas em aplicativos do Windows padrão que visam .NET ao seu aplicativo. Para obter mais informações, consulte o <xref:System.Text.CodePagesEncodingProvider> tópico.  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>Selecionando uma classe de codificação  
 Se você tem a oportunidade de escolher a codificação a ser usada pelo seu aplicativo, você deve usar um Unicode codificação, preferencialmente o <xref:System.Text.UTF8Encoding> ou <xref:System.Text.UnicodeEncoding>. (.NET também oferece suporte a uma terceira codificação Unicode, <xref:System.Text.UTF32Encoding>.)  
  
 Se você estiver planejando usar uma codificação ASCII (<xref:System.Text.ASCIIEncoding>), escolha <xref:System.Text.UTF8Encoding> em vez disso. As duas codificações são idênticas para o conjunto de caracteres ASCII, mas <xref:System.Text.UTF8Encoding> tem as seguintes vantagens:  
  
-   Ele pode representar cada caractere Unicode, enquanto <xref:System.Text.ASCIIEncoding> dá suporte apenas a valores de caractere Unicode entre U + 0000 e U + 007F.  
  
-   Ele fornece detecção de erros e melhor segurança.  
  
-   Ele foi ajustado para ser o mais rápido possível e deve ser mais rápido do que qualquer outra codificação. Mesmo para conteúdo que é totalmente ASCII, operações realizadas com <xref:System.Text.UTF8Encoding> são mais rápidos que as operações realizadas com <xref:System.Text.ASCIIEncoding>.  
  
 Você deve considerar o uso <xref:System.Text.ASCIIEncoding> apenas para aplicativos herdados. No entanto, até mesmo para aplicativos herdados, <xref:System.Text.UTF8Encoding> pode ser uma escolha melhor pelos seguintes motivos (supondo que as configurações padrão):  
  
-   Se seu aplicativo tem conteúdo que não é estritamente ASCII e codifica com <xref:System.Text.ASCIIEncoding>, todos os caracteres não ASCII codifica como um ponto de interrogação (?). Se o aplicativo decodificar esses dados, as informações serão perdidas.  
  
-   Se seu aplicativo tem conteúdo que não é estritamente ASCII e codifica com <xref:System.Text.UTF8Encoding>, o resultado parece ininteligível se interpretado como ASCII. No entanto, se o aplicativo usar um decodificador de UTF-8 para decodificar esses dados, os dados executarão uma viagem de ida e volta com êxito.  
  
 Em um aplicativo Web, os caracteres enviados ao cliente em resposta a uma solicitação da Web devem refletir a codificação usada no cliente. Na maioria dos casos, você deve definir o <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> o valor retornado pela propriedade de <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> propriedade para exibir o texto na codificação que espera que o usuário.  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>Usando um objeto de codificação  
 Um codificador converte uma cadeia de caracteres (mais comumente, caracteres Unicode) em seu equivalente numérico (byte). Por exemplo, você pode usar um codificador ASCII para converter caracteres Unicode em ASCII para que eles possam ser exibidos no console. Para executar a conversão, você deve chamar o <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> método. Se você quiser determinar o número de bytes necessários para armazenar os caracteres codificados antes de executar a codificação, você pode chamar o <xref:System.Text.Encoding.GetByteCount%2A> método.  
  
 O exemplo a seguir usa uma matriz de byte único para codificar cadeias de caracteres em duas operações separadas. Ela mantém um índice que indica a posição inicial na matriz de bytes para o próximo conjunto de bytes codificados em ASCII. Ele chama o <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> método para garantir que a matriz de bytes é grande o suficiente para acomodar a cadeia de caracteres codificada. Depois, ele chama o <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> método para codificar os caracteres na cadeia de caracteres.  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 Um decodificador converte uma matriz de bytes que reflete uma codificação de caracteres específica em um conjunto de caracteres, seja em uma matriz de caracteres ou em uma cadeia de caracteres. Para decodificar uma matriz de bytes em uma matriz de caracteres, você deve chamar o <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> método. Para decodificar uma matriz de bytes em uma cadeia de caracteres, você deve chamar o <xref:System.Text.Encoding.GetString%2A> método. Se você quiser determinar o número de caracteres é necessários para armazenar os bytes decodificados antes de executar a decodificação, você pode chamar o <xref:System.Text.Encoding.GetCharCount%2A> método.  
  
 O exemplo a seguir codifica três cadeias de caracteres e, em seguida, as decodifica em uma única matriz de caracteres. Ela mantém um índice que indica a posição inicial na matriz de bytes para o próximo conjunto de caracteres codificados. Ele chama o <xref:System.Text.ASCIIEncoding.GetCharCount%2A> método para garantir que a matriz de caracteres é grande o suficiente para acomodar todos os caracteres decodificados. Depois, ele chama o <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> método decodificar a matriz de bytes.  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 A codificação e decodificação de métodos de uma classe derivam de <xref:System.Text.Encoding> são projetados para trabalhar em um conjunto completo de dados; ou seja, todos os dados a ser codificada ou decodificada é fornecido em uma única chamada de método. No entanto, em alguns casos, os dados estão disponíveis em um fluxo e os dados a serem codificados ou decodificados podem estar disponíveis somente em operações de leitura separadas. Isso requer a operação de codificação ou decodificação para lembrar qualquer estado salvo em sua invocação anterior. Métodos de classes derivam de <xref:System.Text.Encoder> e <xref:System.Text.Decoder> são capazes de lidar com a codificação e decodificação de operações que abrangem várias chamadas de método.  
  
 Um <xref:System.Text.Encoder> do objeto para uma codificação específica está disponível de codificação <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> propriedade. Um <xref:System.Text.Decoder> do objeto para uma codificação específica está disponível de codificação <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> propriedade. Para operações de decodificação, observe que as classes derivadas de <xref:System.Text.Decoder> incluem um <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> método, mas eles não têm um método que corresponde à <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType>.  
  
 O exemplo a seguir ilustra a diferença entre usar o <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> e <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> métodos para decodificação de uma matriz de byte Unicode. O exemplo codifica uma cadeia de caracteres que contém alguns caracteres Unicode em um arquivo e, em seguida, usa os dois métodos de decodificação para decodificá-los dez bytes por vez. Como um par alternativo ocorre nos bytes décimo e décimo primeiro, ele é decodificado em chamadas de método separadas. Como mostra a saída, o <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> método não é capaz de decodificar corretamente os bytes e em vez disso, substituí-los por U + FFFD (CARACTERE de substituição). Por outro lado, o <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> método é capaz de decodificar com êxito a matriz de bytes para obter a cadeia de caracteres original.  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>Escolhendo uma estratégia de fallback  
 Quando um método tenta codificar ou decodificar um caractere, mas não existe nenhum mapeamento, ele deve implementar uma estratégia de fallback que determine como o mapeamento com falha deva ser tratado. Há três tipos de estratégias de fallback:  
  
-   Fallback de melhor ajuste  
  
-   Fallback de substituição  
  
-   Fallback de exceção  
  
> [!IMPORTANT]
>  Os problemas mais comuns em operações de codificação ocorrem quando um caractere Unicode não pode ser mapeado para uma determinada codificação de página de código. Os problemas mais comuns em operações de decodificação ocorrem quando sequências de bytes inválidas não podem ser convertidas em caracteres Unicode válidos. Por esses motivos, você deve saber qual estratégia de fallback um objeto de codificação específico usa. Sempre que possível, você deve especificar a estratégia de fallback usada por um objeto de codificação quando você criar uma instância do objeto.  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>Fallback de melhor ajuste  
 Quando um caractere não tiver uma correspondência exata na codificação de destino, o codificador pode tentar mapeá-lo para um caractere semelhante. (O fallback de melhor ajuste é sobretudo uma codificação em vez de um problema de decodificação. Há poucas páginas de código que contêm caracteres que não podem ser mapeados com êxito para Unicode.) Melhor ajuste de fallback é o padrão para a página de código e conjunto de caracteres de byte duplo codificações que são recuperadas pelo <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> e <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> sobrecargas.  
  
> [!NOTE]
>  Em teoria, a codificação Unicode classes fornecidas no .NET (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>, e <xref:System.Text.UTF32Encoding>) dão suporte a cada caractere em cada conjunto de caracteres, para que possam ser usados para eliminar problemas de fallbacks de melhor ajuste.  
  
 As estratégias de melhor ajuste variam de acordo com as diferentes páginas de código e não são documentadas detalhadamente. Por exemplo, para algumas páginas de código, caracteres latinos de largura inteira mapeiam para os caracteres latinos de meia largura mais comuns. Para outras páginas de código, esse mapeamento não é feito. Mesmo em uma estratégia de melhor ajuste agressiva, não há nenhum ajuste imaginável para alguns caracteres em algumas codificações. Por exemplo, um ideograma chinês tem nenhum mapeamento razoável para a página de código 1252. Nesse caso, é usada uma cadeia de caracteres de substituição. Por padrão, essa cadeia de caracteres é apenas um PONTO DE INTERROGAÇÃO (U+003F).  
  
 O exemplo a seguir usa a página de código 1252 (a página de código do Windows para idiomas da Europa Ocidental) para ilustrar o mapeamento de melhor ajuste e suas desvantagens. O <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> método é usado para recuperar um objeto de codificação de página de código 1252. Por padrão, ele usa um mapeamento de melhor ajuste para caracteres Unicode aos quais ele não dá suporte. O exemplo cria uma instância de uma cadeia de caracteres que contém três caracteres não ASCII – LETRA MAIÚSCULA LATINA S CIRCULADA (U+24C8), CINCO SOBRESCRITO (U+2075) e INFINITO (U+221E) – separados por espaços. Como mostra a saída de exemplo, quando a cadeia de caracteres é codificada, os três caracteres originais sem espaço são substituídos pelo PONTO DE INTERROGAÇÃO (U+003F), DÍGITO CINCO (U+0035) e DÍGITO OITO (U+0038). DÍGITO OITO é um substituto especialmente ruim para o caractere INFINITO sem suporte e o PONTO DE INTERROGAÇÃO indica que nenhum mapeamento estava disponível para o caractere original.  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 Mapeamento de melhor ajuste é o comportamento padrão para um <xref:System.Text.Encoding> objeto que codifica dados Unicode em dados de página de código e aplicativos herdados que contam com esse comportamento. No entanto, a maioria dos novos aplicativos devem evitar o comportamento de melhor ajuste por motivos de segurança. Por exemplo, os aplicativos não devem colocar um nome de domínio por meio de uma codificação de melhor ajuste.  
  
> [!NOTE]
>  Você também pode implementar um mapeamento de fallback de melhor ajuste personalizado para uma codificação. Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](../../../docs/standard/base-types/character-encoding.md#Custom).  
  
 Se mais adequada de fallback é o padrão para um objeto de codificação, você pode escolher outra estratégia de fallback quando você recupera um <xref:System.Text.Encoding> objeto chamando o <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> ou <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> de sobrecarga. A seção a seguir inclui um exemplo que substitui cada caractere que não pode ser mapeado para a página de código 1252 com um asterisco (*).  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Fallback de substituição  
 Quando um caractere não tem uma correspondência exata do esquema de destino, mas não há nenhum caractere apropriado para o qual ele pode ser mapeado, o aplicativo pode especificar um caractere ou uma cadeia de caracteres de substituição. Esse é o comportamento padrão para o decodificador de Unicode, que substitui qualquer sequência de dois bytes que ele não pode decodificar por REPLACEMENT_CHARACTER (U+FFFD). Também é o comportamento padrão da <xref:System.Text.ASCIIEncoding> classe que substitui cada caractere que não pode codificar ou decodificar com um ponto de interrogação. O exemplo a seguir ilustra a substituição de caracteres para a cadeia de caracteres Unicode do exemplo anterior. Como mostra a saída, cada caractere que não puder ser decodificado em um valor de bytes ASCII é substituído por 0x3F, que é o código ASCII para um ponto de interrogação.  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 .NET inclui o <xref:System.Text.EncoderReplacementFallback> e <xref:System.Text.DecoderReplacementFallback> classes, que substituir uma cadeia de caracteres de substituição, se um caractere não mapear exatamente na codificação ou decodificação de operação. Por padrão, essa cadeia de caracteres de substituição é um ponto de interrogação, mas você pode chamar uma sobrecarga do construtor de classes para escolher uma cadeia de caracteres diferente. Normalmente, a cadeia de caracteres de substituição é um único caractere, embora isso não seja um requisito. O exemplo a seguir altera o comportamento do codificador de 1252 de página de código instanciando um <xref:System.Text.EncoderReplacementFallback> objeto que usa um asterisco (*) como uma cadeia de caracteres de substituição.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  Você também pode implementar uma classe de substituição para uma codificação. Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](../../../docs/standard/base-types/character-encoding.md#Custom).  
  
 Além de PONTO DE INTERROGAÇÃO (U+003F), o CARACTERE DE SUBSTITUIÇÃO Unicode (U+FFFD) normalmente é usado como uma cadeia de caracteres de substituição, especialmente ao decodificar sequências de bytes que não podem ser convertidas com êxito em caracteres Unicode. No entanto, você está livre para escolher qualquer cadeia de caracteres de substituição e ela pode conter vários caracteres.  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Fallback de exceção  
 Em vez de fornecer um melhor ajuste fallback ou uma cadeia de caracteres de substituição, um codificador pode gerar um <xref:System.Text.EncoderFallbackException> se não é possível codificar um conjunto de caracteres e um decodificador pode lançar um <xref:System.Text.DecoderFallbackException> se não for possível decodificar uma matriz de bytes. Para gerar uma exceção em codificação e decodificação de operações, você deve fornecer um <xref:System.Text.EncoderExceptionFallback> objeto e um <xref:System.Text.DecoderExceptionFallback> objeto, respectivamente, para o <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> método. O exemplo a seguir ilustra a exceção fallback com o <xref:System.Text.ASCIIEncoding> classe.  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  Você também pode implementar um manipulador de exceção personalizado para uma operação de codificação. Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](../../../docs/standard/base-types/character-encoding.md#Custom).  
  
 O <xref:System.Text.EncoderFallbackException> e <xref:System.Text.DecoderFallbackException> objetos fornecem as seguintes informações sobre a condição que causou a exceção:  
  
-   O <xref:System.Text.EncoderFallbackException> objeto inclui um <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A> método, que indica se um ou mais caracteres que não podem ser codificados representam um par substituto desconhecido (nesse caso, o método retorna `true`) ou um único caractere desconhecido (em Nesse caso, o método retorna `false`). Os caracteres do par substituto estão disponíveis no <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> e <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> propriedades. O único caractere desconhecido é proveniente do <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> propriedade. O <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> propriedade indica a posição na cadeia de caracteres em que o primeiro caractere que não pode ser codificado foi encontrado.  
  
-   O <xref:System.Text.DecoderFallbackException> objeto inclui um <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> propriedade que retorna uma matriz de bytes que não pode ser decodificada. O <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> propriedade indica a posição inicial dos bytes desconhecidos.  
  
 Embora o <xref:System.Text.EncoderFallbackException> e <xref:System.Text.DecoderFallbackException> objetos fornecem informações de diagnósticas adequadas sobre a exceção, não fornecem acesso a codificação ou decodificação de buffer. Portanto, eles não permitem que dados inválidos sejam substituídos ou corrigidos dentro do método de codificação ou de decodificação.  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementando uma estratégia de fallback personalizada  
 Além do mapeamento de melhor ajuste implementado internamente por páginas de código, o .NET inclui as seguintes classes para implementar uma estratégia de fallback:  
  
-   Use <xref:System.Text.EncoderReplacementFallback> e <xref:System.Text.EncoderReplacementFallbackBuffer> para substituir caracteres em codificação de operações.  
  
-   Use <xref:System.Text.DecoderReplacementFallback> e <xref:System.Text.DecoderReplacementFallbackBuffer> para substituir caracteres em operações de decodificação.  
  
-   Use <xref:System.Text.EncoderExceptionFallback> e <xref:System.Text.EncoderExceptionFallbackBuffer> para lançar uma <xref:System.Text.EncoderFallbackException> quando um caractere não pode ser codificado.  
  
-   Use <xref:System.Text.DecoderExceptionFallback> e <xref:System.Text.DecoderExceptionFallbackBuffer> para lançar uma <xref:System.Text.DecoderFallbackException> quando um caractere não pode ser decodificado.  
  
 Além disso, você pode implementar uma solução personalizada que usa o fallback de melhor ajuste, fallback de substituição ou fallback de exceção seguindo estas etapas:  
  
1.  Derive uma classe de <xref:System.Text.EncoderFallback> para operações de codificação e de <xref:System.Text.DecoderFallback> para operações de decodificação.  
  
2.  Derive uma classe de <xref:System.Text.EncoderFallbackBuffer> para operações de codificação e de <xref:System.Text.DecoderFallbackBuffer> para operações de decodificação.  
  
3.  Se fallback, exceção predefinida <xref:System.Text.EncoderFallbackException> e <xref:System.Text.DecoderFallbackException> classes não atenderem às suas necessidades, derive uma classe de um objeto de exceção como <xref:System.Exception> ou <xref:System.ArgumentException>.  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Derivando de EncoderFallback ou DecoderFallback  
 Para implementar uma solução personalizada de fallback, você deve criar uma classe que herda de <xref:System.Text.EncoderFallback> para operações de codificação e de <xref:System.Text.DecoderFallback> para operações de decodificação. Instâncias dessas classes são passadas para o <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> método e serve como um intermediário entre a classe de codificação e a implementação de fallback.  
  
 Quando você cria uma solução de fallback personalizada para um codificador ou um decodificador, você deve implementar os seguintes membros:  
  
-   O <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> propriedade, que retorna o número máximo possível de caracteres que o pode fallback melhor ajuste, substituição ou exceção de retorno para substituir um único caractere. Para um fallback de exceção personalizado, seu valor é zero.  
  
-   O <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> método, que retorna personalizados <xref:System.Text.EncoderFallbackBuffer> ou <xref:System.Text.DecoderFallbackBuffer> implementação. O método é chamado pelo codificador quando ele encontra o primeiro caractere que ele não consegue codificar com êxito ou pelo decodificador quando ele encontra o primeiro byte que ele não consegue decodificar com êxito.  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Derivando de EncoderFallbackBuffer ou DecoderFallbackBuffer  
 Para implementar uma solução personalizada de fallback, você também deve criar uma classe que herda de <xref:System.Text.EncoderFallbackBuffer> para operações de codificação e de <xref:System.Text.DecoderFallbackBuffer> para operações de decodificação. Instâncias dessas classes são retornadas pelo <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> método o <xref:System.Text.EncoderFallback> e <xref:System.Text.DecoderFallback> classes. O <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> método é chamado pelo codificador quando ele encontra o primeiro caractere que não é capaz de codificar, e o <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> método é chamado pelo decodificador quando ele encontra um ou mais bytes que não é capaz de decodificar. O <xref:System.Text.EncoderFallbackBuffer> e <xref:System.Text.DecoderFallbackBuffer> classes fornecem a implementação de fallback. Cada instância representa um buffer que contém os caracteres de fallback que substituirão o caractere que não pode ser codificado ou a sequência de bytes que não pode ser decodificada.  
  
 Quando você cria uma solução de fallback personalizada para um codificador ou um decodificador, você deve implementar os seguintes membros:  
  
-   O <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> método. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>é chamado pelo codificador para fornecer informações sobre o caractere que não é possível codificar o buffer de fallback. Como o caractere a ser codificado pode ser um par alternativo, esse método está sobrecarregado. Uma sobrecarga é passada para o caractere a ser codificado e para o seu índice na cadeia de caracteres. A segunda sobrecarga é passada para os substitutos altos e baixos juntamente com seu índice na cadeia de caracteres. O <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> método é chamado pelo decodificador para fornecer informações sobre os bytes que não é possível decodificar o buffer de fallback. Esse método recebe uma matriz de bytes que ele não consegue decodificar, juntamente com o índice do primeiro byte. O método de fallback deverá retornar `true` se o buffer de fallback conseguir fornecer caracteres de melhor ajuste ou de substituição; caso contrário, ele deverá retornar `false`. Para um fallback de exceção, o método de fallback deve lançar uma exceção.  
  
-   O <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> método, que é chamado repetidamente pelo codificador ou decodificador para obter o próximo caractere do buffer de fallback. Quando todos os caracteres de fallback tiverem sido retornados, o método deverá retornar U+0000.  
  
-   O <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> propriedade, que retorna o número de caracteres restantes no buffer de fallback.  
  
-   O <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> método, que move a posição atual no buffer de fallback para o caractere anterior.  
  
-   O <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> ou <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> método, que reinicializa o buffer de fallback.  
  
 Se a implementação de fallback é uma alternativa melhor ajuste ou fallback substituição, as classes derivadas de <xref:System.Text.EncoderFallbackBuffer> e <xref:System.Text.DecoderFallbackBuffer> também manter dois campos de instância privada: o número exato de caracteres no buffer; e o índice do próximo caractere no buffer para retornar.  
  
### <a name="an-encoderfallback-example"></a>Um exemplo de EncoderFallback  
 Um exemplo anterior usava o fallback de substituição para substituir caracteres Unicode que não correspondiam aos caracteres ASCII por um asterisco (*). O exemplo a seguir usa uma implementação de fallback de melhor ajuste personalizada em vez de fornecer um melhor mapeamento de caracteres não ASCII.  
  
 O código a seguir define uma classe denominada `CustomMapper` que é derivado de <xref:System.Text.EncoderFallback> para lidar com o mapeamento de melhor ajuste de caracteres não-ASCII. Seu `CreateFallbackBuffer` método retorna um `CustomMapperFallbackBuffer` object, que fornece o <xref:System.Text.EncoderFallbackBuffer> implementação. O `CustomMapper` classe usa um <xref:System.Collections.Generic.Dictionary%602> objeto para armazenar os mapeamentos de caracteres de Unicode sem suporte (o valor da chave) e seus caracteres de 8 bits correspondentes (que são armazenados em dois bytes consecutivas em um inteiro de 64 bits). Para disponibilizar esse mapeamento ao buffer de fallback, a instância `CustomMapper` é passada como um parâmetro para o construtor de classe `CustomMapperFallbackBuffer`. Como o mapeamento mais longo é a cadeia de caracteres "INF" para o caractere Unicode U+221E, a propriedade `MaxCharCount` retorna 3.  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 O código a seguir define o `CustomMapperFallbackBuffer` classe, que é derivado de <xref:System.Text.EncoderFallbackBuffer>. O dicionário que contém mapeamentos de melhor ajuste e definido na instância `CustomMapper` está disponível no seu construtor de classe. Seu método `Fallback` retornará `true` se qualquer um dos caracteres Unicode que o codificador ASCII não conseguir codificar forem definidos no dicionário de mapeamento; caso contrário, retornará `false`. Para cada fallback, a variável `count` privada indica o número de caracteres que continuam sendo retornados e a variável `index` privada indica a posição no buffer de cadeia de caracteres, `charsToReturn`, do próximo caractere a ser retornado.  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 O código a seguir instancia o `CustomMapper` do objeto e passa uma instância dele para o <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> método. A saída indica que a implementação de fallback de melhor ajuste lida com êxito com os três caracteres não ASCII na cadeia de caracteres original.  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.Encoder>  
 <xref:System.Text.Decoder>  
 <xref:System.Text.DecoderFallback>  
 <xref:System.Text.Encoding>  
 <xref:System.Text.EncoderFallback>  
 [Globalização e localização](../../../docs/standard/globalization-localization/index.md)
