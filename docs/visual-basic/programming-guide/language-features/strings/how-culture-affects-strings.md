---
title: Como a cultura afeta cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 2520a7684b8710abd949543e3f17f77d3c631d22
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352472"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Como a cultura afeta cadeias de caracteres no Visual Basic
Esta página de ajuda discute como Visual Basic usa informações de cultura para executar conversões e comparações de cadeia de caracteres.  
  
## <a name="when-to-use-culture-specific-strings"></a>Quando usar cadeias de caracteres específicas de cultura  
 Normalmente, você deve usar cadeias de caracteres específicas de cultura para todos os dados apresentados e lidos de usuários e usar cadeias de caracteres invariáveis de cultura para os dados internos do seu aplicativo.  
  
 Por exemplo, se seu aplicativo solicitar que os usuários insiram uma data como uma cadeia de caracteres, ele deverá esperar que os usuários formatem as cadeias de acordo com sua cultura, e o aplicativo deverá converter a cadeia de caracteres adequadamente. Se seu aplicativo apresentar essa data em sua interface do usuário, ele deverá apresentá-la na cultura do usuário.  
  
 No entanto, se o aplicativo carregar a data em um servidor central, ele deverá Formatar a cadeia de caracteres de acordo com uma cultura específica, para evitar confusão entre formatos de data potencialmente diferentes.  
  
## <a name="culture-sensitive-functions"></a>Funções sensíveis à cultura  
 Todas as funções de conversão de cadeia de caracteres Visual Basic (exceto para as funções `Str` e `Val`) usam as informações de cultura do aplicativo para garantir que as conversões e comparações sejam apropriadas para a cultura do usuário do aplicativo.  
  
 A chave para usar com êxito funções de conversão de cadeia de caracteres em aplicativos executados em computadores com diferentes configurações de cultura é entender quais funções usam uma configuração de cultura específica e que usam a configuração de cultura atual. Observe que as configurações de cultura do aplicativo são, por padrão, herdadas das configurações de cultura do sistema operacional. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 O `Str` (converte números em cadeias de caracteres) e `Val` (converte cadeias de caracteres em números) as funções não usam as informações de cultura do aplicativo ao converter entre cadeias de caracteres e números. Em vez disso, eles reconhecem apenas o ponto final (.) como um separador decimal válido. Os análogos com reconhecimento cultural dessas funções são:  
  
- **Conversões que usam a cultura atual.** As funções `CStr` e `Format` convertem um número em uma cadeia de caracteres e as funções `CDbl` e `CInt` convertem uma cadeia de caracteres em um número.  
  
- **Conversões que usam uma cultura específica.** Cada objeto de número tem um método `ToString(IFormatProvider)` que converte um número em uma cadeia de caracteres e um método `Parse(String, IFormatProvider)` que converte uma cadeia de caracteres em um número. Por exemplo, o tipo de `Double` fornece os métodos <xref:System.Double.ToString%28System.IFormatProvider%29> e <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>.  
  
 Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Conversion.Str%2A> e <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Usando uma cultura específica  
 Imagine que você está desenvolvendo um aplicativo que envia uma data (formatada como uma cadeia de caracteres) para um serviço Web. Nesse caso, seu aplicativo deve usar uma cultura específica para a conversão de cadeia de caracteres. Para ilustrar o porquê, considere o resultado do uso do método de <xref:System.DateTime.ToString> da data: se seu aplicativo usar esse método para formatar a data 4 de julho de 2005, ele retornará "7/4/2005 12:00:00 AM" quando executado com a cultura de Estados Unidos Inglês (en-US), mas retornará "04.07.2005 00:00:00" quando for executado com a cultura alemão (de-DE).  
  
 Quando você precisar executar uma conversão de cadeia de caracteres em um formato de cultura específico, deverá usar a classe `CultureInfo` que é criada no .NET Framework. Você pode criar um novo objeto `CultureInfo` para uma cultura específica passando o nome da cultura para o Construtor <xref:System.Globalization.CultureInfo.%23ctor%2A>. Os nomes de cultura com suporte são listados na página de ajuda da classe <xref:System.Globalization.CultureInfo>.  
  
 Como alternativa, você pode obter uma instância da *cultura invariável* da propriedade <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. A cultura invariável é baseada na cultura em inglês, mas há algumas diferenças. Por exemplo, a cultura invariável especifica um relógio de 24 horas, em vez de um relógio de 12 horas.  
  
 Para converter uma data na cadeia de caracteres da cultura, passe o objeto <xref:System.Globalization.CultureInfo> para o método <xref:System.DateTime.ToString%28System.IFormatProvider%29> do objeto Date. Por exemplo, o código a seguir exibe "07/04/2005 00:00:00", independentemente das configurações de cultura do aplicativo.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Os literais de data são sempre interpretados de acordo com a cultura em inglês.  
  
## <a name="comparing-strings"></a>Comparando cadeias de caracteres  
 Há duas situações importantes em que são necessárias comparações de cadeia de caracteres:  
  
- **Classificando dados para exibição para o usuário.** Use operações com base na cultura atual para que as cadeias de caracteres sejam classificadas adequadamente.  
  
- **Determinando se duas cadeias de caracteres internas de aplicativo correspondem exatamente (normalmente para fins de segurança).** Use operações que Desconsiderem a cultura atual.  
  
 Você pode executar os dois tipos de comparações com a função Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A>. Especifique o argumento de `Compare` opcional para controlar o tipo de comparação: `Text` para a maioria dos `Binary` de entrada e saída para determinar correspondências exatas.  
  
 A função `StrComp` retorna um inteiro que indica a relação entre as duas cadeias de caracteres comparadas com base na ordem de classificação. Um valor positivo para o resultado indica que a primeira cadeia de caracteres é maior que a segunda. Um resultado negativo indica que a primeira cadeia de caracteres é menor e zero indica igualdade entre as cadeias de caracteres.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Você também pode usar o parceiro .NET Framework da função `StrComp`, o método <xref:System.String.Compare%2A?displayProperty=nameWithType>. Esse é um método estático e sobrecarregado da classe de cadeia de caracteres base. O exemplo a seguir ilustra como esse método é usado:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Para obter um controle mais preciso sobre como as comparações são executadas, você pode usar sobrecargas adicionais do método <xref:System.String.Compare%2A>. Com o método <xref:System.String.Compare%2A?displayProperty=nameWithType>, você pode usar o argumento `comparisonType` para especificar o tipo de comparação a ser usado.  
  
|Valor para `comparisonType` argumento|Tipo de comparação|Quando usar|  
|---|---|---|  
|`Ordinal`|Comparação baseada em bytes de componente de cadeias de caracteres.|Use esse valor ao comparar: identificadores que diferenciam maiúsculas de minúsculas, configurações relacionadas à segurança ou outros identificadores não lingüísticos em que os bytes devem corresponder exatamente.|  
|`OrdinalIgnoreCase`|Comparação baseada em bytes de componente de cadeias de caracteres.<br /><br /> `OrdinalIgnoreCase` usa as informações de cultura invariável para determinar quando dois caracteres diferem apenas em maiúsculas.|Use esse valor ao comparar: identificadores que não diferenciam maiúsculas de minúsculas, configurações relacionadas à segurança e dados armazenados no Windows.|  
|`CurrentCulture` ou `CurrentCultureIgnoreCase`|Comparação baseada na interpretação de cadeias de caracteres na cultura atual.|Use estes valores ao comparar: dados que são exibidos para o usuário, a maioria das entradas de usuário e outros dados que exigem interpretação linguística.|  
|`InvariantCulture` ou `InvariantCultureIgnoreCase`|Comparação baseada na interpretação de cadeias de caracteres na cultura invariável.<br /><br /> Isso é diferente do `Ordinal` e `OrdinalIgnoreCase`, porque a cultura invariável trata os caracteres fora do intervalo aceito como caracteres invariáveis equivalentes.|Use esses valores somente ao comparar dados persistentes ou exibir dados relevantes linguísticas que exijam uma ordem de classificação fixa.|  
  
### <a name="security-considerations"></a>considerações sobre segurança  
 Se seu aplicativo toma decisões de segurança com base no resultado de uma operação de comparação ou de alteração de maiúsculas e minúsculas, a operação deve usar o método <xref:System.String.Compare%2A?displayProperty=nameWithType> e passar `Ordinal` ou `OrdinalIgnoreCase` para o argumento `comparisonType`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Globalization.CultureInfo>
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
