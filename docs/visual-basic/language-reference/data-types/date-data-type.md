---
title: Tipo de dados Data (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 32bd0912b0bae3340cffed010fc67431d0efb376
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033526"
---
# <a name="date-data-type-visual-basic"></a>Tipo de dados Data (Visual Basic)
Contém os valores de (8 bytes) do IEEE de 64 bits que representam datas desde 1 de janeiro do ano de 0001 até 31 de dezembro do ano 9999 e horas de 12:00:00 AM (meia-noite) por meio de 11:59:59.9999999 PM. Cada incremento representa 100 nanossegundos de tempo decorrido desde o início de 1º de janeiro do ano 1 no calendário gregoriano. O valor máximo representará 100 nanosegundos antes do início do dia 1º de janeiro do ano 10000.  
  
## <a name="remarks"></a>Comentários  
 Use o `Date` tipo de dados para conter os valores de data, hora valores ou valores de data e hora.  
  
 O valor padrão de `Date` é 0:00:00 (meia-noite) em 1º de janeiro de 0001.  
  
 Você pode obter a data e hora atuais do <xref:Microsoft.VisualBasic.DateAndTime> classe.  
  
## <a name="format-requirements"></a>Requisitos de formato  
 Você deve incluir um `Date` literal entre sinais numéricos (`# #`). Você deve especificar o valor de data no formato dd/aaaa, por exemplo `#5/31/1993#`, ou AAAA-MM-dd, por exemplo `#1993-5-31#`. Ao especificar o ano pela primeira vez, você pode usar barras "/".  Esse requisito é independente de sua localidade e data do seu computador e configurações de formato de hora.  
  
 O motivo para essa restrição é que o significado do seu código nunca deve alterar dependendo da localidade na qual seu aplicativo está em execução. Suponha que você codifique uma `Date` literal de `#3/4/1998#` e pretender dizer 4 de março de 1998. Em uma localidade que utilize mm/dd/aaaa, 4/3/1998 compila como você deseja. Mas suponha que você implanta seu aplicativo em vários países. Em uma localidade que utilize dd/mm/aaaa, o literal embutido em código seria compiladas para 3 de abril de 1998. Em uma localidade que utilize aaaa/mm/dd, o literal seriam inválido (abril de 1998, 0003) e causa um erro do compilador.  
  
## <a name="workarounds"></a>Soluções alternativas  
 Para converter um `Date` literal para o formato de sua localidade, ou para um formato personalizado, forneça o literal para o <xref:Microsoft.VisualBasic.Strings.Format%2A> função, especificando um formato de data predefinidos ou definidos pelo usuário. O exemplo a seguir demonstra isso.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Como alternativa, você pode usar um dos construtores sobrecarregados do <xref:System.DateTime> estrutura para montar um valor de data e hora. O exemplo a seguir cria um valor para representar a 31 de maio de 1993 em 12:14, à tarde.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>Formato de hora  
 Você pode especificar o valor de hora no formato de 12 horas ou 24 horas, por exemplo `#1:15:30 PM#` ou `#13:15:30#`. No entanto, se você não especificar os minutos ou segundos, você deve especificar AM ou PM.  
  
## <a name="date-and-time-defaults"></a>Data e hora padrão  
 Se você não incluir uma data em uma literal de data/hora, o Visual Basic define a parte da data do valor de 1 de janeiro, 0001. Se você não incluir um tempo em um literal de data/hora, o Visual Basic define a parte de hora do valor para o início do dia, ou seja, meia-noite (0: 00:00).  
  
## <a name="type-conversions"></a>Conversões de tipo  
 Se você converter um `Date` de valor para o `String` tipo, Visual Basic renderiza a data de acordo com o formato de data abreviada especificado pela localidade do tempo de execução e o renderiza a hora de acordo com o formato de hora (12 horas ou 24 horas) especificada pelo localidade do tempo de execução.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que os tipos em outros ambientes de data/hora não são compatíveis com o Visual Basic `Date` tipo. Se você estiver passando um argumento de data/hora para esse componente, declare-o como `Double` em vez de `Date` em seu novo Visual Basic de código e usar os métodos de conversão <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> e <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Caracteres de tipo.** `Date` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador. No entanto, o compilador trata literais entre sinais numéricos (`# #`) como `Date`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.DateTime?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
 Uma variável ou constante do `Date` tipo de dados contém a data e a hora. O exemplo a seguir ilustra essa situação.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Cadeias de caracteres de formato de data e hora padrão](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [Cadeias de caracteres de formato de data e hora personalizado](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
