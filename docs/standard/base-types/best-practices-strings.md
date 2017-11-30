---
title: "Práticas recomendadas para usar cadeias de caracteres no .NET"
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
- strings [.NET Framework],searching
- best practices,string comparison and sorting
- strings [.NET Framework],best practices
- strings [.NET Framework],basic string operations
- sorting strings
- strings [.NET Framework],sorting
- string comparison [.NET Framework],best practices
- string sorting
- comparing strings
- strings [.NET Framework],comparing
ms.assetid: b9f0bf53-e2de-4116-8ce9-d4f91a1df4f7
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d187096fee5119a22d886029cd63173e4ca1c8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="best-practices-for-using-strings-in-net"></a>Práticas recomendadas para usar cadeias de caracteres no .NET
<a name="top"></a>.NET fornece amplo suporte para desenvolvimento de aplicativos globalizados e localizados e torna mais fácil aplicar as convenções de cultura atual ou de uma cultura específica ao executar operações comuns, como classificação e exibir cadeias de caracteres. Mas a classificação ou a comparação de cadeias de caracteres nem sempre é uma operação que leva em conta a cultura. Por exemplo, cadeias de caracteres que são usadas internamente por um aplicativo normalmente devem ser manipuladas de maneira idêntica em todas as culturas. Quando os dados de cadeias de caracteres culturalmente independentes, como marcações XML, marcações HTML, nomes de usuário, caminhos de arquivo e nomes de objetos do sistema, são interpretados como se levassem em conta a cultura, o código do aplicativo pode estar sujeito a bugs sutis, desempenho ruim e, em alguns casos, problemas de segurança.  
  
 Este tópico examina a cadeia de caracteres de classificação, de comparação e métodos de maiusculas e minúsculas no .NET, apresenta recomendações para selecionar um método de manipulação de cadeia de caracteres apropriado e fornece informações adicionais sobre métodos de manipulação de cadeia de caracteres. Ela também examina como os dados formatados, como dados numéricos e dados de data e hora, são manipulados para exibição e armazenamento.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Recomendações para uso de cadeia de caracteres](#recommendations_for_string_usage)  
  
-   [Especifica comparações de cadeia de caracteres explicitamente](#specifying_string_comparisons_explicitly)  
  
-   [Os detalhes de comparação de cadeia de caracteres](#the_details_of_string_comparison)  
  
-   [Escolhendo um membro StringComparison para a chamada de método](#choosing_a_stringcomparison_member_for_your_method_call)  
  
-   [Métodos comuns de comparação de cadeia de caracteres no .NET](#common_string_comparison_methods_in_the_net_framework)  
  
-   [Métodos que executam a comparação de cadeia de caracteres indiretamente](#methods_that_perform_string_comparison_indirectly)  
  
-   [Exibindo e persistir dados formatados](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>Recomendações para Uso da Cadeia de Caracteres  
 Ao desenvolver com o .NET, siga estas recomendações simples quando usar cadeias de caracteres:  
  
-   Use sobrecargas que especificam explicitamente as regras de comparação de cadeias de caracteres para operações de cadeia de caracteres. Normalmente, isso envolve uma sobrecarga de método que tem um parâmetro de tipo de chamada <xref:System.StringComparison>.  
  
-   Use <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> para comparações como segurança padrão para correspondência de cadeia de caracteres de cultura independente.  
  
-   Use as comparações com <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> para melhorar o desempenho.  
  
-   Usar operações de cadeia de caracteres com base em <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> quando você exibir a saída para o usuário.  
  
-   Use o não linguística <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> valores em vez de operações de cadeia de caracteres com base em <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> quando a comparação é irrelevante linguisticamente (simbólico, por exemplo).  
  
-   Use o <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> método em vez do <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> método quando normalizar cadeias de caracteres para comparação.  
  
-   Use uma sobrecarga de <xref:System.String.Equals%2A?displayProperty=nameWithType> método para testar se duas cadeias de caracteres são iguais.  
  
-   Use o <xref:System.String.Compare%2A?displayProperty=nameWithType> e <xref:System.String.CompareTo%2A?displayProperty=nameWithType> métodos para classificar cadeias de caracteres, para não verificar igualdade.  
  
-   Use a formatação que leva em conta a cultura para exibir dados que não são de cadeias de caracteres, como números e datas, em uma interface do usuário. Use a formatação com a cultura invariável para persistir os dados que não são de cadeias de caracteres no formato de cadeia de caracteres.  
  
 Evite as práticas a seguir ao usar cadeias de caracteres:  
  
-   Não use sobrecargas que não especificam explicita ou implicitamente as regras de comparação de cadeias de caracteres para operações de cadeia de caracteres.  
  
-   Não use operações de cadeia de caracteres com base em <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> na maioria dos casos. Uma das poucas exceções é quando a persistência de dados de forma linguisticamente significativos mas culturalmente desconhecidos.  
  
-   Não use uma sobrecarga de <xref:System.String.Compare%2A?displayProperty=nameWithType> ou <xref:System.String.CompareTo%2A> método e teste para um valor de retorno de zero para determinar se duas cadeias de caracteres são iguais.  
  
-   Não use a formatação que leva em conta a cultura para persistir dados numéricos ou dados de data e hora no formato de cadeia de caracteres.  
  
 [Voltar ao início](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>Especificando Comparações da Cadeia de Caracteres Explicitamente  
 A maioria dos métodos de manipulação de cadeia de caracteres no .NET é sobrecarregada. Normalmente, uma ou mais sobrecargas aceitam as configurações padrão, enquanto outras não aceitam nenhum padrão e definem a maneira exata em que as cadeias de caracteres devem ser comparadas ou manipuladas. A maioria dos métodos que não depende de padrões inclui um parâmetro de tipo <xref:System.StringComparison>, que é uma enumeração que especifica explicitamente as regras de comparação de cadeia de caracteres, cultura e caso. A tabela a seguir descreve o <xref:System.StringComparison> membros de enumeração.  
  
|Membro de StringComparison|Descrição|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|Executa uma comparação que diferencia maiúsculas de minúsculas usando a cultura atual.|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Executa uma comparação que não diferencia maiúsculas de minúsculas usando a cultura atual.|  
|<xref:System.StringComparison.InvariantCulture>|Executa uma comparação diferencia maiusculas de minúsculas, usando a cultura invariável.|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Executa uma comparação de maiusculas e minúsculas usando a cultura invariável.|  
|<xref:System.StringComparison.Ordinal>|Executa uma comparação ordinal.|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|Executa uma comparação ordinal que não diferencia maiúsculas de minúsculas.|  
  
 Por exemplo, o <xref:System.String.IndexOf%2A> método, que retorna o índice de uma subcadeia de caracteres em um <xref:System.String> objeto que corresponde a um caractere ou uma cadeia de caracteres tem nove sobrecargas:  
  
-   <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>, e <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, que por padrão realizar uma pesquisa de (diferencia maiusculas de minúsculas e não levam em conta a cultura) ordinal para um caractere na cadeia de caracteres.  
  
-   <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, e <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, que por padrão realizar uma pesquisa diferencia maiusculas de minúsculas e sensíveis à cultura de uma subcadeia de caracteres na cadeia de caracteres.  
  
-   <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, e <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, que incluem um parâmetro de tipo <xref:System.StringComparison> que permite que o formulário da comparação seja especificado.  
  
 É recomendável que você selecione uma sobrecarga que não usa valores padrão, pelos seguintes motivos:  
  
-   Algumas sobrecargas com parâmetros padrão (aquelas que pesquise um <xref:System.Char> na instância de cadeia de caracteres) realizar uma comparação ordinal, ao passo que outras pessoas (aquelas que pesquisar uma cadeia de caracteres na instância de cadeia de caracteres) são sensíveis à cultura. É difícil lembrar qual método usa o valor padrão e é fácil confundir as sobrecargas.  
  
-   A intenção do código que depende de valores padrão para chamadas de método não é clara. No exemplo a seguir, que se baseia em padrões, é difícil saber se o desenvolvedor realmente planejava uma comparação ordinal ou linguística de duas cadeias de caracteres ou se uma diferença entre maiúsculas e minúsculas entre `protocol` e “http” pode fazer com que o teste de igualdade retorne `false`.  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 Em geral, é recomendável que você chame um método que não se baseie em padrões, pois ele torna a intenção do código clara. Isso, por sua vez, torna o código mais legível e fácil de depurar e manter. O exemplo a seguir aborda as questões levantadas sobre o exemplo anterior. Ele deixa claro que a comparação ordinal é usada e que as diferenças de maiúsculas e minúsculas são ignoradas.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [Voltar ao início](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>Os Detalhes de Comparação da Cadeia de Caracteres  
 A comparação de cadeia de caracteres é o centro de muitas operações relacionadas à cadeia de caracteres, especialmente a classificação e teste de igualdade. As cadeias de caracteres são classificadas em uma determinada ordem: se “my” aparece antes de “string” em uma lista classificada de cadeias de caracteres, “my” deve comparar menos que ou igual a “string”. Além disso, a comparação define implicitamente a igualdade. A operação de comparação retorna zero para cadeias de caracteres que considerar iguais. Uma boa interpretação é que nenhuma cadeia de caracteres é menor que a outra. Operações mais significativas envolvendo cadeias de caracteres incluem um ou ambos destes procedimentos: comparação com outra cadeia de caracteres e execução de uma operação de classificação bem definida.  
  
 No entanto, avaliar duas cadeias de caracteres quanto à igualdade ou ordem de classificação não gera um único resultado correto, o resultado depende dos critérios usados para comparar as cadeias de caracteres. Em particular, as comparações de cadeia de caracteres ordinais ou baseadas no uso de maiúsculas e minúsculas e convenções classificação da cultura atual ou da cultura invariável (uma cultura independente de localidade com base no idioma inglês) podem gerar resultados diferentes.  
  
<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>Comparações da Cadeia de Caracteres que Usam a Cultura Atual  
 Um critério envolve o uso das convenções da cultura atual ao comparar cadeias de caracteres. As comparações que se baseiam na cultura atual usam a localidade ou a cultura atual do thread. Se a cultura não é definida pelo usuário, o padrão é a configuração no **opções regionais** janela no painel de controle. Você deve sempre usar comparações que se baseiam na cultura atual quando os dados forem linguisticamente relevantes e quando eles refletirem a interação do usuário que leva em conta a cultura.  
  
 No entanto, o comportamento da comparação e do uso de maiúsculas e minúsculas no .NET muda quando a cultura muda. Isso acontece quando um aplicativo é executado em um computador que tem uma cultura diferente do computador em que o aplicativo foi desenvolvido ou quando o thread em execução muda sua cultura. Esse comportamento é intencional, mas permanece não óbvio para muitos desenvolvedores. O exemplo a seguir ilustra as diferenças na ordem de classificação entre as culturas de inglês dos EUA ("en-US") e sueco ("sv-SE"). Observe que as palavras "ångström", "Windows" e "Visual Studio" aparecem em posições diferentes nas matrizes de cadeias de caracteres classificadas.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 As comparações que não diferenciam maiúsculas de minúsculas que usam a cultura atual são iguais às comparações que levam em conta a cultura, exceto que elas ignoram as maiúsculas e minúsculas conforme determinado pela cultura atual do thread. Esse comportamento pode se manifestar em ordens de classificação também.  
  
 As comparações que usam a semântica de cultura atual são o padrão para os seguintes métodos:  
  
-   <xref:System.String.Compare%2A?displayProperty=nameWithType>sobrecargas que não incluam um <xref:System.StringComparison> parâmetro.  
  
-   <xref:System.String.CompareTo%2A?displayProperty=nameWithType>sobrecargas.  
  
-   O padrão <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> método e o <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> método com um `null` <xref:System.Globalization.CultureInfo> parâmetro.  
  
-   O padrão <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> método e o <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> método com um `null` <xref:System.Globalization.CultureInfo> parâmetro.  
  
-   <xref:System.String.IndexOf%2A?displayProperty=nameWithType>sobrecargas que aceitam um <xref:System.String> como uma pesquisa de parâmetro e que não têm um <xref:System.StringComparison> parâmetro.  
  
-   <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>sobrecargas que aceitam um <xref:System.String> como uma pesquisa de parâmetro e que não têm um <xref:System.StringComparison> parâmetro.  
  
 Em qualquer caso, é recomendável que você chame uma sobrecarga que tem um <xref:System.StringComparison> parâmetro para fazer com que a intenção do método de chamada clara.  
  
 Bugs sutis e não tão sutis podem surgir quando dados de cadeias de caracteres não linguísticas são interpretados linguisticamente ou quando os dados da cadeia de caracteres de uma cultura específica são interpretados usando as convenções de outra cultura. O exemplo canônico é o problema do I turco.  
  
 Para quase todos os alfabetos latinos, incluindo o do inglês dos EUA, o caractere "i" (\u0069) é a versão em letra minúscula do caractere "I" (\u0049). Essa regra de maiúsculas e minúsculas rapidamente se torna o padrão para alguém programando em tal cultura. No entanto, o alfabeto turco ("tr-TR") inclui um caractere "I com um ponto", "İ" (\u0130), que é a versão maiúscula de "i". O turco também inclui um caractere minúsculo "i sem um ponto", "ı" (\u0131), que em maiúscula é “I”. Esse comportamento também ocorre na cultura azerbaidjana ("az").  
  
 Portanto, as suposições feitas sobre a colocação do "i" em maiúscula ou do "I" em minúscula não são válidas entre todas as culturas. Se você usar as sobrecargas padrão para rotinas de comparação de cadeias de caracteres, elas estarão sujeitas à variação entre culturas. Se os dados a serem comparados são forem linguísticos, o uso das sobrecargas padrão pode gerar resultados indesejáveis, como a tentativa a seguir de realizar uma comparação que não diferencia maiúsculas de minúsculas das cadeias de caracteres “file” e “FILE” ilustra.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 Essa comparação pode causar problemas significativos se a cultura for usada inadvertidamente nas configurações sensíveis à segurança, como no exemplo a seguir. Uma chamada de método, como `IsFileURI("file:")` retorna `true` se a cultura atual for inglês dos EUA, mas `false` se a cultura atual for turco. Assim, em sistemas turcos, alguém poderia driblar as medidas de segurança que bloqueiam o acesso a URIs que não diferenciam maiúsculas de minúsculas que começam com “FILE:”.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 Nesse caso, como "file:" deve ser interpretado como um identificador não linguístico que não leva em conta a cultura, o código deveria ser escrito como mostrado no exemplo a seguir.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>Operações Ordinais da Cadeia de Caracteres  
 Especificando o <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> valor em uma chamada de método significa uma comparação não linguística em que os recursos de idiomas naturais são ignorados. Métodos que são invocados com estas <xref:System.StringComparison> valores embasar decisões de operação de cadeia de caracteres em comparações de byte simples em vez de maiusculas e minúsculas ou equivalência de tabelas que são parametrizadas pela cultura. Na maioria dos casos, essa abordagem se adapta melhor à interpretação pretendida de cadeias de caracteres, enquanto torna o código mais rápido e confiável.  
  
 Comparações ordinais são comparações de cadeia de caracteres nas quais cada byte de cada cadeia de caracteres é comparado sem a interpretação linguística, por exemplo, “windows” não corresponde a “Windows”. Isso é basicamente uma chamada para o tempo de execução do C `strcmp` função. Use essa comparação quando o contexto determinar que as cadeias de caracteres devem corresponder exatamente ou exigir uma política de correspondência conservadora. Além disso, a comparação ordinal é a operação de comparação mais rápida porque ela não aplica nenhuma regra linguística ao determinar um resultado.  
  
 As cadeias de caracteres no .NET podem conter caracteres nulos inseridos. Uma das diferenças mais clara entre a comparação ordinal e a que leva em conta a cultura (incluindo comparações que usam a cultura invariável) diz respeito à manipulação de caracteres nulos inseridos em uma cadeia de caracteres. Esses caracteres são ignorados quando você usa o <xref:System.String.Compare%2A?displayProperty=nameWithType> e <xref:System.String.Equals%2A?displayProperty=nameWithType> métodos para executar comparações de cultura (incluindo comparações que usam a cultura invariável). Como resultado, em comparações que levam em conta a cultura, cadeias de caracteres que contêm caracteres nulos inseridos podem ser consideradas iguais a cadeias de caracteres que não contêm.  
  
> [!IMPORTANT]
>  Embora os métodos de comparação de cadeia de caracteres ignorar caracteres nulos inseridos, os métodos de pesquisa, como de cadeia de caracteres <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, e <xref:System.String.StartsWith%2A?displayProperty=nameWithType> não.  
  
 O exemplo a seguir executa uma comparação que leva em conta a cultura da cadeia de caracteres "Aa" com uma cadeia de caracteres semelhante que contém vários caracteres nulos inseridos entre "A" e "a" e mostra como as duas cadeias de caracteres são consideradas iguais.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 No entanto, as cadeias de caracteres não são consideradas iguais ao usar a comparação ordinal, como mostra o exemplo a seguir.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 As comparações ordinais que não diferenciam maiúsculas de minúsculas são a próxima abordagem conservadora. Essas comparações ignoram a maioria das maiúsculas e minúsculas, por exemplo, "windows" corresponde a "Windows". Ao lidar com caracteres ASCII, essa política é equivalente a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, exceto que ele ignora maiusculas e minúsculas de usual ASCII. Portanto, qualquer caractere em [A, Z] (\u0041-\u005A) corresponde ao caractere correspondente em [a,z] (\u0061-\007A). As maiúsculas e minúsculas fora do intervalo de ASCII usam as tabelas de cultura invariável. Portanto, a comparação a seguir:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 é equivalente a (mas mais rápida do que) esta comparação:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 Essas comparações ainda são muito rápidas.  
  
> [!NOTE]
>  O comportamento de cadeia de caracteres do sistema de arquivos, chaves do registro e valores e as variáveis de ambiente é melhor representado por <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.  
  
 Ambos <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> e <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> usam os valores binários diretamente e são mais adequados para correspondência. Quando você não tiver certeza sobre as configurações de comparação, use um destes dois valores. No entanto, como elas executam uma comparação byte por byte, elas não classificam por uma ordem de classificação linguística (como um dicionário de inglês), mas por ordem de classificação binária. Os resultados podem parecer estranhos na maioria dos contextos se exibido aos usuários.  
  
 Ordinal semântica é o padrão para <xref:System.String.Equals%2A?displayProperty=nameWithType> sobrecargas que não incluam um <xref:System.StringComparison> argumento (incluindo o operador de igualdade). Em qualquer caso, é recomendável que você chame uma sobrecarga que tem um <xref:System.StringComparison> parâmetro.  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>Operações da Cadeia de Caracteres que Usam a Cultura Invariável  
 As comparações com o uso de cultura invariável de <xref:System.Globalization.CultureInfo.CompareInfo%2A> propriedade retornada pelo estático <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade. Esse comportamento é o mesmo em todos os sistemas, ele converte qualquer caractere fora de seu intervalo no que ele acredita que sejam caracteres invariáveis equivalentes. Essa política pode ser útil para manter um conjunto de comportamentos de cadeia de caracteres entre culturas, mas geralmente fornece resultados inesperados.  
  
 Comparações de maiusculas e minúsculas com a cultura invariável usam estático <xref:System.Globalization.CultureInfo.CompareInfo%2A> propriedade retornada pelo estático <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade para obter informações de comparação também. As diferenças de maiúsculas e minúsculas entre esses caracteres convertidos são ignoradas.  
  
 Comparações que usam <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> e <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> funcionam de forma idêntica em cadeias de caracteres ASCII. No entanto, <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> toma decisões linguísticas que podem não ser apropriadas para cadeias de caracteres que deve ser interpretado como um conjunto de bytes. O `CultureInfo.InvariantCulture.CompareInfo` objeto torna o <xref:System.String.Compare%2A> método interpretar determinados conjuntos de caracteres como equivalentes. Por exemplo, a equivalência a seguir é válida na cultura invariável:  
  
 InvariantCulture: a + ̊ = å  
  
 A LETRA minúscula latina caracteres "a" (\u0061), quando ele está ao lado de caracteres COMBINANDO ANEL acima "+"̊"(\u030a) é interpretado como o LATINO pequena LETRA A com ANEL acima de caracteres"å"(\u00e5). Como mostra o exemplo a seguir, esse comportamento é diferente da comparação ordinal.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 Ao interpretar nomes de arquivo, cookies ou qualquer outro elemento em que uma combinação como "å" pode aparecer, as comparações ordinais ainda oferecem o comportamento mais transparente e adequado.  
  
 De forma geral, a cultura invariável tem muito poucas propriedades que a tornam útil para comparação. Ela faz a comparação de maneira linguisticamente relevante, o que impede que ela garanta a equivalência simbólica total, mas não é a opção de exibição em nenhuma cultura. Um dos motivos para usar alguns <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> de comparação é manter dados ordenados, para uma exibição cross-culturally idêntico. Por exemplo, se um arquivo de dados grande que contém uma lista de identificadores classificados para exibição acompanha um aplicativo, a adição a essa lista exige uma inserção com a inserção de estilo invariável.  
  
 [Voltar ao início](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Escolhendo um Membro StringComparison para a Chamada de Método  
 A tabela a seguir descreve o mapeamento do contexto de semântica de cadeia de caracteres para um <xref:System.StringComparison> membro de enumeração.  
  
|Dados|Comportamento|System.StringComparison correspondente<br /><br /> Valor |  
|----------|--------------|-----------------------------------------------------|  
|Identificadores internos diferencia maiusculas de minúsculas.<br /><br /> Identificadores de maiusculas e minúsculas nos padrões como XML e HTTP.<br /><br /> Configurações relacionadas à segurança diferencia maiusculas de minúsculas.|Um identificador não linguístico, em que bytes correspondem exatamente.|<xref:System.StringComparison.Ordinal>|  
|Identificadores internos maiusculas de minúsculas.<br /><br /> Identificadores de maiusculas e minúsculas em padrões como XML e HTTP.<br /><br /> Caminhos de arquivo.<br /><br /> Chaves do registro e valores.<br /><br /> Variáveis de ambiente.<br /><br /> Identificadores de recurso (por exemplo, nomes de identificador).<br /><br /> Configurações relacionadas à segurança maiusculas de minúsculas.|Um identificador não linguística, em que o caso é irrelevante; especialmente dados armazenados na maioria dos serviços de sistema do Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|Alguns dados persistentes, linguisticamente relevantes.<br /><br /> Exibição de dados linguísticas que requer uma ordem de classificação fixa.|Dados culturalmente desconhecidos que ainda são linguisticamente relevantes.|<xref:System.StringComparison.InvariantCulture><br /><br /> -ou-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|Dados exibidos para o usuário.<br /><br /> A maioria das entradas do usuário.|Dados que exigem os costumes linguísticos locais.|<xref:System.StringComparison.CurrentCulture><br /><br /> -ou-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [Voltar ao início](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>Métodos comuns de comparação de cadeia de caracteres no .NET  
 As seções a seguir descrevem os métodos que são mais comumente usados para a comparação de cadeias de caracteres.  
  
### <a name="stringcompare"></a>String.Compare  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Como a operação mais central da interpretação de cadeia de caracteres, todas as instâncias de chamadas desse método devem ser examinadas para determinar se as cadeias de caracteres devem ser interpretadas de acordo com a cultura atual ou dissociadas da cultura (simbolicamente). Normalmente, é o último e um <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> comparação deve ser usada em vez disso.  
  
 O <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> classe, que é retornado pelo <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> também inclui uma propriedade, um <xref:System.Globalization.CompareInfo.Compare%2A> método que fornece um grande número de correspondência de opções (ordinal, ignorando espaço em branco, tipo kana ignorando e assim por diante) por meio do <xref:System.Globalization.CompareOptions> sinalizador enumeração.  
  
### <a name="stringcompareto"></a>String.CompareTo  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Este método não oferece atualmente uma sobrecarga que especifica um <xref:System.StringComparison> tipo. É possível converter esse método para recomendada <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formulário.  
  
 Tipos que implementam o <xref:System.IComparable> e <xref:System.IComparable%601> interfaces implementam este método. Porque ele não oferece a opção de um <xref:System.StringComparison> parâmetro, implementar tipos geralmente permitem que o usuário especifique um <xref:System.StringComparer> no seu construtor. O exemplo a seguir define uma `FileName` classe cujo construtor de classe inclui um <xref:System.StringComparer> parâmetro. Isso <xref:System.StringComparer> objeto é usado no `FileName.CompareTo` método.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>String.Equals  
 Padrão de interpretação: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 O <xref:System.String> classe permite que você teste de igualdade chamando a estáticas ou instância <xref:System.String.Equals%2A> sobrecargas do método, ou usando o operador de igualdade estático. O operador e as sobrecargas utilizam a comparação ordinal por padrão. No entanto, ainda é recomendável que você chame uma sobrecarga que especifica explicitamente o <xref:System.StringComparison> tipo mesmo se você deseja executar uma comparação ordinal; isso facilita o código para um determinado interpretação de cadeia de caracteres de pesquisa.  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper e String.ToLower  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Você deve ter cuidado ao usar esses métodos, pois forçar uma cadeia de caracteres para maiúsculas ou minúsculas normalmente é usado como uma normalização pequena para comparar cadeias de caracteres independentemente de maiúsculas e minúsculas. Nesse caso, considere o uso de uma comparação que não diferencie maiúsculas de minúsculas.  
  
 O <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> e <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> métodos também estão disponíveis. <xref:System.String.ToUpperInvariant%2A>é o modo padrão para normalizar o caso. As comparações feitas usando <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> são a composição de duas chamadas de maneira comportamental: chamar <xref:System.String.ToUpperInvariant%2A> em ambos os argumentos de cadeia de caracteres e fazer uma comparação usando <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 Sobrecargas também estão disponíveis para converter para letras maiusculas e minúsculas em uma cultura específica, passando um <xref:System.Globalization.CultureInfo> objeto que representa essa cultura para o método.  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper e Char.ToLower  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Esses métodos funcionam da mesma forma que o <xref:System.String.ToUpper%2A?displayProperty=nameWithType> e <xref:System.String.ToLower%2A?displayProperty=nameWithType> métodos descritos na seção anterior.  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith e String.EndsWith  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Por padrão, esses dois métodos executam uma comparação que leva em conta a cultura.  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf e String.LastIndexOf  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Há uma falta de consistência em como as sobrecargas padrão desses métodos realizam comparações. Todos os <xref:System.String.IndexOf%2A?displayProperty=nameWithType> e <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> métodos que incluem um <xref:System.Char> parâmetro realizar uma comparação ordinal, mas o padrão <xref:System.String.IndexOf%2A?displayProperty=nameWithType> e <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> métodos que incluem um <xref:System.String> parâmetro executar um sensíveis à cultura comparação.  
  
 Se você chamar o <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> ou <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> método e passá-lo em uma cadeia de caracteres a ser localizado na instância atual, recomendamos que você chame uma sobrecarga que especifica explicitamente o <xref:System.StringComparison> tipo. As sobrecargas que incluem um <xref:System.Char> argumento não permitem que você especifique um <xref:System.StringComparison> tipo.  
  
 [Voltar ao início](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>Métodos que Realizam Comparação da Cadeia de Caracteres Indiretamente  
 Alguns métodos de não-cadeia de caracteres que têm a comparação de cadeia de caracteres como uma operação central, use o <xref:System.StringComparer> tipo. O <xref:System.StringComparer> classe inclui seis propriedades estáticas que retornam <xref:System.StringComparer> instâncias cuja <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> métodos executam os seguintes tipos de comparações de cadeia de caracteres:  
  
-   Comparações de cadeias de caracteres que levam em conta a cultura usando a cultura atual. Isso <xref:System.StringComparer> retornado pelo objeto de <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> propriedade.  
  
-   Comparações que não diferenciam maiúsculas de minúsculas usando a cultura atual. Isso <xref:System.StringComparer> retornado pelo objeto de <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> propriedade.  
  
-   Comparações sem diferenciação de cultura usando as regras de comparação de palavras da cultura invariável. Isso <xref:System.StringComparer> retornado pelo objeto de <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> propriedade.  
  
-   Comparações de maiusculas e minúsculas e não levam em conta a cultura usando as regras de comparação de palavras da cultura invariável. Isso <xref:System.StringComparer> retornado pelo objeto de <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> propriedade.  
  
-   Comparação ordinal. Isso <xref:System.StringComparer> retornado pelo objeto de <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> propriedade.  
  
-   Comparação ordinal que não diferencia maiúsculas de minúsculas. Isso <xref:System.StringComparer> retornado pelo objeto de <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> propriedade.  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort e Array.BinarySearch  
 Padrão de interpretação: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Ao armazenar quaisquer dados em uma coleção ou ler dados persistentes de um arquivo ou banco de dados em uma coleção, alternar a cultura atual pode invalidar as invariáveis na coleção. O <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> método pressupõe que os elementos da matriz devem ser pesquisadas já estão classificados. Para classificar qualquer elemento de cadeia de caracteres na matriz, o <xref:System.Array.Sort%2A?displayProperty=nameWithType> chamadas de método de <xref:System.String.Compare%2A?displayProperty=nameWithType> método ordenar elementos individuais. Usar um comparador que leva em conta a cultura pode ser perigoso se a cultura mudar entre o momento em que a matriz é ordenada e que seu conteúdo é pesquisado. Por exemplo, no código a seguir, o armazenamento e a recuperação operam no comparador que é fornecido implicitamente pela propriedade `Thread.CurrentThread.CurrentCulture`. Se a cultura puder mudar entre as chamadas para `StoreNames` e `DoesNameExist`, e especialmente se os conteúdos da matriz forem mantidos em algum lugar entre as duas chamadas de método, a pesquisa binária poderá falhar.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 Uma variação recomendada é exibida no exemplo a seguir, que usa o mesmo método de comparação (que não leva em conta a cultura) ordinal para classificar e pesquisar a matriz. O código de alteração é refletido nas linhas rotuladas como `Line A` e `Line B` nos dois exemplos.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 Se esses dados forem mantidos e movidos entre as culturas e a classificação for usada para apresentar esses dados para o usuário, você pode considerar usar <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, que opera linguisticamente para a melhor saída do usuário, mas não é afetado pelas alterações na cultura. O exemplo a seguir modifica os dois exemplos anteriores para usar a cultura invariável para classificar e pesquisar a matriz.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>Exemplo de Coleções: Construtor da Tabela de Hash  
 As cadeias de caracteres de hash fornecem um segundo exemplo de uma operação que é afetada pela maneira como as cadeias de caracteres são comparadas.  
  
 O exemplo a seguir cria um <xref:System.Collections.Hashtable> objeto passando-o <xref:System.StringComparer> objeto que é retornado pelo <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> propriedade. Porque uma classe <xref:System.StringComparer> que é derivado de <xref:System.StringComparer> implementa o <xref:System.Collections.IEqualityComparer> interface, seu <xref:System.Collections.IEqualityComparer.GetHashCode%2A> método é usado para calcular o código hash de cadeias de caracteres na tabela de hash.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [Voltar ao início](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>Exibindo e Mantendo Dados Formatados  
 Quando você exibir dados que não são de cadeias de caracteres como números e datas e horas para os usuários, formate-os usando as configurações culturais do usuário. Por padrão, o <xref:System.String.Format%2A?displayProperty=nameWithType> método e o `ToString` métodos dos tipos numéricos e os tipos de data e hora usam a cultura do thread atual para operações de formatação. Para especificar explicitamente que o método de formatação deve usar a cultura atual, você pode chamar uma sobrecarga de um método de formatação que tem um `provider` parâmetro, como <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ou <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>e passá-lo a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> propriedade.  
  
 Você pode manter os dados que não são de cadeias de caracteres como dados binários ou como dados formatados. Se você optar por salvá-lo dados formatados como, você deve chamar uma sobrecarga de método de formatação que inclui um `provider` parâmetro e passá-lo a <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade. A cultura invariável fornece um formato consistente para os dados formatados que é independente da cultura e do computador. Em contraste, dados persistentes que são formatados usando culturas diferentes da cultura invariável têm várias limitações:  
  
-   É provável que os dados não sejam utilizáveis se forem recuperados em um sistema que tem uma cultura diferente ou se o usuário do sistema atual alterar a cultura atual e tentar recuperar os dados.  
  
-   As propriedades de uma cultura em um computador específico podem ser diferentes dos valores padrão. A qualquer momento, um usuário pode personalizar as configurações de exibição que levam em conta a cultura. Devido a isso, os dados formatados que são salvos em um sistema podem não ser legíveis após o usuário personalizar as configurações culturais. É provável que a portabilidade dos dados formatados entre computadores seja ainda mais limitada.  
  
-   Padrões internacionais, regionais ou nacionais que controlam a formatação de números ou datas e horas alterar ao longo do tempo, e essas alterações são incorporadas atualizações do sistema operacional Windows. Quando as convenções de formatação mudam, os dados que foram formatados usando as convenções anteriores podem se tornar ilegíveis.  
  
 O exemplo a seguir ilustra a portabilidade limitada resultante do uso da formatação que leva em conta a cultura para manter os dados. O exemplo salva uma matriz de valores de data e hora em um arquivo. Eles são formatados usando as convenções da cultura do inglês (Estados Unidos). Depois que o aplicativo altera a cultura do thread atual para francês (Suíça), ele tenta ler os valores salvos usando as convenções de formatação da cultura atual. Tentativa de leitura de dois dos dados itens lança um <xref:System.FormatException> exceção e a matriz de datas agora contém dois elementos incorretos iguais ao <xref:System.DateTime.MinValue>.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 No entanto, se você substituir o <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> propriedade com <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> em chamadas para <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> e <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, persistente de data e hora dados são restaurados com êxito, como mostra a saída a seguir.  
  
```  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manipulando cadeias de caracteres](../../../docs/standard/base-types/manipulating-strings.md)
