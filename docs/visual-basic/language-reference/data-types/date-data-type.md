---
title: Data do tipo de dados (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Date
dev_langs:
- VB
helpviewer_keywords:
- Date data type
- dates, Visual Basic data types
- times, Date data type
- Date literals
- data values
- times, Visual Basic data types
- dates, Date data type
- data types [Visual Basic], assigning
- literals, Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: feaec17d899cdce2d51f4b98daa49a4b4e7e65a2
ms.lasthandoff: 03/13/2017

---
# <a name="date-data-type-visual-basic"></a>Tipo de dados Data (Visual Basic)
Contém valores de (8 bytes) IEEE de 64 bits que representam datas desde 1 de janeiro do ano de 0001 até 31 de dezembro de 9999 ano e horas de 12:00:00 AM (meia-noite) por meio de 11:59:59.9999999 PM. Cada incremento representa 100 nanossegundos de tempo decorrido desde o início de 1º de janeiro do ano 1 no calendário gregoriano. O valor máximo representa 100 nanossegundos antes do início de 1º de janeiro do ano 10000.  
  
## <a name="remarks"></a>Comentários  
 Use o `Date` tipo de dados para conter valores de data, hora valores ou valores de data e hora.  
  
 O valor padrão de `Date` é 0:00:00 (meia-noite) em 1º de janeiro de 0001.  
  
 Você pode obter a data atual e a hora da <xref:Microsoft.VisualBasic.DateAndTime>classe.</xref:Microsoft.VisualBasic.DateAndTime>  
  
## <a name="format-requirements"></a>Requisitos de formato  
 Você deve colocar um `Date` literal entre sinais numéricos (`# #`). Você deve especificar o valor de data no formato dd/aaaa, por exemplo `#5/31/1993#`, ou AAAA-MM-dd, por exemplo `#1993-5-31#`. Você pode usar barras ao especificar o ano pela primeira vez.  Esse requisito é independente da sua localidade e data do seu computador e as configurações de formato de hora.  
  
 A razão para essa restrição é que o significado de seu código nunca deve ser alterado dependendo da localidade na qual o aplicativo é executado. Suponha que você codifique uma `Date` literal de `#3/4/1998#` e pretende dizer 4 de março de 1998. Em uma localidade que utilize mm/dd/aaaa, 4/3/1998 compila como você deseja. Mas suponha que você implantar seu aplicativo em muitos países. Uma localidade que utilize dd/mm/aaaa, o literal embutida seria compilar para 3 de abril de 1998. Em uma localidade que utilize aaaa/mm/dd, literal seria inválido (abril de 1998, 0003) e causa um erro do compilador.  
  
## <a name="workarounds"></a>Soluções alternativas  
 Para converter um `Date` literal no formato de sua localidade, ou em um formato personalizado, forneça o literal para o <xref:Microsoft.VisualBasic.Strings.Format%2A>função, especificando um formato de data predefinidos ou definidos pelo usuário.</xref:Microsoft.VisualBasic.Strings.Format%2A> O exemplo a seguir demonstra isso.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Como alternativa, você pode usar um dos construtores sobrecarregados do <xref:System.DateTime>estrutura para montar um valor de data e hora.</xref:System.DateTime> O exemplo a seguir cria um valor para representar a 31 de maio de 1993 em 12:14 à tarde.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>Formato de hora  
 Você pode especificar o valor de hora no formato de 12 horas ou 24 horas, por exemplo `#1:15:30 PM#` ou `#13:15:30#`. No entanto, se você não especificar os minutos ou segundos, você deve especificar AM ou PM.  
  
## <a name="date-and-time-defaults"></a>Data e hora padrão  
 Se você não incluir uma data em uma literal de data/hora, o Visual Basic define a parte de data do valor 1 de janeiro, 0001. Se você não incluir uma vez em um literal de data/hora, o Visual Basic define a parte de hora do valor para o início do dia, ou seja, meia-noite (0:&00;:00).  
  
## <a name="type-conversions"></a>Conversões de tipo  
 Se você converter um `Date` valor o `String` tipo, Visual Basic apresenta a data de acordo com o formato de data abreviada especificado pela localidade do tempo de execução e o renderiza a hora de acordo com o formato de hora (12 horas ou 24 horas) especificada pela localidade do tempo de execução.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos em outros ambientes de data/hora não são compatíveis com o Visual Basic `Date` tipo. Se você estiver passando um argumento de data/hora para um componente, declare-o como `Double` em vez de `Date` no seu novo código do Visual Basic e usar os métodos de conversão <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>e <xref:System.DateTime.ToOADate%2A?displayProperty=fullName>.</xref:System.DateTime.ToOADate%2A?displayProperty=fullName> </xref:System.DateTime.FromOADate%2A?displayProperty=fullName>  
  
-   **Caracteres de tipo.** `Date`não possui caractere de tipo literal ou caractere de tipo identificador. No entanto, o compilador trata literais entre sinais numéricos (`# #`) como `Date`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.DateTime?displayProperty=fullName>estrutura.</xref:System.DateTime?displayProperty=fullName>  
  
## <a name="example"></a>Exemplo  
 Uma variável ou constante do `Date` tipo de dados contém a data e a hora. O exemplo a seguir ilustra essa situação.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.DateTime?displayProperty=fullName></xref:System.DateTime?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Cadeias de caracteres de formato de data e hora padrão](http://msdn.microsoft.com/library/bb79761a-ca08-44ee-b142-b06b3e2fc22b)   
 [Cadeias de caracteres de formato de data e hora personalizado](http://msdn.microsoft.com/library/98b374e3-0cc2-4c78-ab44-efb671d71984)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
