---
title: Como a cultura afeta cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d3c7ae9da9c18e53da393928e34dcfbf04fc891c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834615"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Como a cultura afeta cadeias de caracteres no Visual Basic
Esta página de Ajuda discute como o Visual Basic usa informações de cultura para executar comparações e conversões de cadeia de caracteres.  
  
## <a name="when-to-use-culture-specific-strings"></a>Quando usar cadeias de caracteres específicas da cultura  
 Normalmente, você deve usar cadeias de caracteres específicas da cultura para todos os dados apresentados ao ler de usuários e usar cadeias de caracteres de cultura invariável para os dados do aplicativo interno.  
  
 Por exemplo, se seu aplicativo solicitar que os usuários insiram uma data como uma cadeia de caracteres, ele deve esperar que os usuários para formatar as cadeias de caracteres de acordo com sua cultura e o aplicativo deve converter a cadeia de caracteres corretamente. Se seu aplicativo, em seguida, apresenta essa data na interface do usuário, ele deve apresentá-lo na cultura do usuário.  
  
 No entanto, se o aplicativo carrega a data para um servidor central, ele deve formatar a cadeia de caracteres de acordo com uma cultura específica, para evitar confusão entre formatos de data potencialmente diferentes.  
  
## <a name="culture-sensitive-functions"></a>Funções de diferenciação de cultura  
 Todas as funções de conversão de cadeia de caracteres do Visual Basic (exceto para o `Str` e `Val` funções) usar informações de cultura do aplicativo para certificar-se de que as conversões e comparações são apropriadas para a cultura da caixa de diálogo usuário.  
  
 A chave para utilizar com êxito as funções de conversão de cadeia de caracteres em aplicativos que são executados em computadores com configurações de cultura diferente é entender quais funções usam uma configuração de cultura específica e que usam a configuração de cultura atual. Observe que as configurações de cultura do aplicativo são, por padrão, herdadas das configurações de cultura do sistema operacional. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, e [funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 O `Str` (converte números em cadeias de caracteres) e `Val` funções (converte cadeias de caracteres em números) não usa informações de cultura do aplicativo ao converter entre cadeias de caracteres e números. Em vez disso, eles reconhecem somente o ponto (.) como separador decimal válido. As semelhanças culturalmente ciente dessas funções são:  
  
-   **Conversões que usam a cultura atual.** O `CStr` e `Format` funções de convertem um número em uma cadeia de caracteres e o `CDbl` e `CInt` funções convertem uma cadeia de caracteres em um número.  
  
-   **Conversões que usam uma cultura específica.** Cada objeto number tem um `ToString(IFormatProvider)` método que converte um número em uma cadeia de caracteres, e um `Parse(String, IFormatProvider)` método que converte uma cadeia de caracteres em um número. Por exemplo, o `Double` tipo fornece a <xref:System.Double.ToString%28System.IFormatProvider%29> e <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> métodos.  
  
 Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Conversion.Str%2A> e <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Usando uma cultura específica  
 Imagine que você está desenvolvendo um aplicativo que envia uma data (formatada como uma cadeia de caracteres) a um serviço Web. Nesse caso, seu aplicativo deve usar uma cultura específica para a conversão de cadeia de caracteres. Para ilustrar o porquê, considere o resultado do uso da data <xref:System.DateTime.ToString> método: Se seu aplicativo usa esse método para formatar a data 4 de julho de 2005, ele retorna "4/7/2005 12:00:00 AM" quando executado com a cultura do inglês dos Estados Unidos (en-US), mas ele retorna "04.07.2005 00:00:00" quando executado com a cultura de alemão (de-DE).  
  
 Quando você precisar executar uma conversão de cadeia de caracteres em um formato de cultura específica, você deve usar o `CultureInfo` classe está incorporada a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Você pode criar um novo `CultureInfo` objeto para uma cultura específica, passando o nome da cultura para o <xref:System.Globalization.CultureInfo.%23ctor%2A> construtor. Os nomes de cultura com suporte são listados no <xref:System.Globalization.CultureInfo> página de Ajuda da classe.  
  
 Como alternativa, você pode obter uma instância de *cultura invariável* do <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriedade. A cultura invariável é com base na cultura em inglês, mas há algumas diferenças. Por exemplo, a cultura invariável Especifica um relógio de 24 horas, em vez de um relógio de 12 horas.  
  
 Para converter uma data em cadeia de caracteres da cultura, passe o <xref:System.Globalization.CultureInfo> objeto para o objeto de data <xref:System.DateTime.ToString%28System.IFormatProvider%29> método. Por exemplo, o código a seguir exibe "04/07/2005 00:00:00", independentemente das configurações de cultura do aplicativo.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Literais de data sempre são interpretados de acordo com a cultura em inglês.  
  
## <a name="comparing-strings"></a>Comparando cadeias de caracteres  
 Há duas situações importantes em que as comparações de cadeia de caracteres são necessários:  
  
-   **Classificação de dados para exibição ao usuário.** Use as operações com base na cultura atual para que as cadeias de caracteres adequadamente classificado.  
  
-   **Determinar se duas cadeias de caracteres de aplicativo interno corresponderem exatamente (normalmente para fins de segurança).** Use as operações que desconsiderar a cultura atual.  
  
 Você pode executar os dois tipos de comparações com o Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A> função. Especifique o valor opcional `Compare` argumento para controlar o tipo de comparação: `Text` para a maioria das entrada e saída `Binary` para determinar correspondências exatas.  
  
 O `StrComp` função retorna um inteiro que indica a relação entre as duas cadeias de caracteres comparadas com base na ordem de classificação. Um valor positivo para o resultado indica que a primeira cadeia de caracteres é maior que a segunda cadeia de caracteres. Um resultado negativo indica a primeira cadeia de caracteres é menor, e zero indica a igualdade entre as cadeias de caracteres.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Você também pode usar o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] parceiros do `StrComp` função, o <xref:System.String.Compare%2A?displayProperty=nameWithType> método. Esse é um método estático, sobrecarregado da classe base da cadeia de caracteres. O exemplo a seguir ilustra como esse método é usado:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Para ter maior controle sobre como as comparações são executadas, você pode usar sobrecargas adicionais do <xref:System.String.Compare%2A> método. Com o <xref:System.String.Compare%2A?displayProperty=nameWithType> método, você pode usar o `comparisonType` argumento para especificar o tipo de comparação a ser usado.  
  
|O valor para `comparisonType` argumento|Tipo de comparação|Quando usar|  
|---|---|---|  
|`Ordinal`|Comparação com base nos bytes de componente das cadeias de caracteres.|Use esse valor ao comparar: identificadores diferencia maiusculas de minúsculas, as configurações de segurança ou outros identificadores não linguística em que os bytes devem corresponder exatamente.|  
|`OrdinalIgnoreCase`|Comparação com base nos bytes de componente das cadeias de caracteres.<br /><br /> `OrdinalIgnoreCase` usa as informações de cultura invariável para determinar quando dois caracteres diferem apenas em maiusculas e minúsculas.|Use esse valor ao comparar: identificadores diferencia maiusculas de minúsculas, as configurações de segurança e dados armazenados no Windows.|  
|`CurrentCulture` ou `CurrentCultureIgnoreCase`|Comparação com base na interpretação de cadeias de caracteres na cultura atual.|Use esses valores durante a comparação: dados que são exibidos para o usuário, a maioria das entradas do usuário e outros dados que requer a interpretação linguística.|  
|`InvariantCulture` ou `InvariantCultureIgnoreCase`|Comparação com base na interpretação de cadeias de caracteres da cultura invariável.<br /><br /> Isso é diferente de `Ordinal` e `OrdinalIgnoreCase`, pois a cultura invariável trata caracteres fora do intervalo aceito como caracteres invariáveis equivalentes.|Use esses valores somente ao comparar dados persistentes ou exibem dados linguisticamente relevantes que requer uma ordem de classificação fixa.|  
  
### <a name="security-considerations"></a>Considerações sobre segurança  
 Se seu aplicativo toma decisões de segurança com base no resultado de uma comparação ou operação de alteração de caso e, em seguida, a operação deve usar o <xref:System.String.Compare%2A?displayProperty=nameWithType> método e passar `Ordinal` ou `OrdinalIgnoreCase` para o `comparisonType` argumento.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Globalization.CultureInfo>
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
