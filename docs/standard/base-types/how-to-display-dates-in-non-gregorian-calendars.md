---
title: "Como exibir datas em calendários não gregorianos"
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
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a79860091e549dcf4eaa7090947f9506eceb6119
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Como exibir datas em calendários não gregorianos
O <xref:System.DateTime> e <xref:System.DateTimeOffset> tipos usam o calendário gregoriano como seu calendário padrão. Isso significa que chamar o método `ToString` de um valor de data e hora exibe a representação de cadeia de caracteres da data e hora no calendário gregoriano, mesmo que a data e hora tenha sido criada usando outro calendário. Isso é ilustrado no exemplo a seguir, que usa duas maneiras diferentes para criar um valor de data e hora com o calendário persa, mas ainda exibe esses valores de data e hora no calendário gregoriano quando ele chama o <xref:System.DateTime.ToString%2A> método. Este exemplo reflete duas técnicas comumente usadas, mas incorretas, para exibir a data em um calendário específico.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Duas técnicas diferentes podem ser usadas para exibir a data em um calendário específico. A primeira requer que o calendário seja o calendário padrão de uma determinada cultura. O segundo pode ser usado com qualquer calendário.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Para exibir a data do calendário padrão de uma cultura  
  
1.  Instanciar um objeto de calendário derivado de <xref:System.Globalization.Calendar> classe que representa o calendário a ser usado.  
  
2.  Criar uma instância de um <xref:System.Globalization.CultureInfo> objeto que representa a cultura cuja formatação será usado para exibir a data.  
  
3.  Chamar o <xref:System.Array.Exists%2A?displayProperty=nameWithType> método para determinar se o objeto de calendário é um membro da matriz retornada pelo <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> propriedade. Isso indica que o calendário pode servir como o calendário padrão para o <xref:System.Globalization.CultureInfo> objeto. Se ele não for membro da matriz, siga as instruções na seção "Para exibir a data em qualquer calendário".  
  
4.  Atribuir o objeto de calendário para o <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> propriedade o <xref:System.Globalization.DateTimeFormatInfo> objeto retornado pelo <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriedade.  
  
    > [!NOTE]
    >  O <xref:System.Globalization.CultureInfo> classe também tem um <xref:System.Globalization.CultureInfo.Calendar%2A> propriedade. No entanto, ele é somente leitura e constante; não é alterado para refletir o novo calendário padrão atribuído para o <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> propriedade.  
  
5.  Chame o <xref:System.DateTime.ToString%2A> ou <xref:System.DateTime.ToString%2A> método e passá-lo a <xref:System.Globalization.CultureInfo> objeto cujo calendário padrão foi modificado na etapa anterior.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Para exibir a data em qualquer calendário  
  
1.  Instanciar um objeto de calendário derivado de <xref:System.Globalization.Calendar> classe que representa o calendário a ser usado.  
  
2.  Determine quais elementos de data e hora devem aparecer na representação de cadeia de caracteres do valor de data e hora.  
  
3.  Para cada elemento de data e hora que você deseja exibir, ligue para o objeto de calendário `Get`... método. Os métodos a seguir estão disponíveis:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, para exibir o ano no calendário apropriado.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, para exibir o mês no calendário apropriado.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, para exibir o número do dia do mês no calendário apropriado.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, para exibir a hora do dia no calendário apropriado.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, para exibir os minutos na hora no calendário apropriado.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, para exibir os segundos no minuto no calendário apropriado.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>, para exibir os milisegundos no segundo no calendário apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo exibe uma data usando dois calendários diferentes. Ele exibe a data após definir o calendário islâmico como calendário padrão para a cultura ar-JO e exibe a data usando o calendário persa, que não tem suporte como calendário opcional pela cultura fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Cada <xref:System.Globalization.CultureInfo> objeto pode dar suporte a um ou mais calendários, que são indicados pelo <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> propriedade. Um deles é designado como o calendário padrão da cultura e é retornado por somente leitura <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> propriedade. Outro dos calendários opcionais pode ser designado como o padrão, atribuindo um <xref:System.Globalization.Calendar> objeto que representa o calendário para o <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> propriedade retornada pelo <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriedade. No entanto, alguns calendários, como o calendário persa representado pelo <xref:System.Globalization.PersianCalendar> da classe, não servem como calendários opcionais para qualquer cultura.  
  
 O exemplo define uma classe de utilitário de calendário reutilizável, `CalendarUtility`, para manipular muitos dos detalhes de gerar a representação de cadeia de caracteres de uma data usando um calendário específico. A classe `CalendarUtility` tem os seguintes membros:  
  
-   Um construtor parametrizado cujo único parâmetro é um <xref:System.Globalization.Calendar> objeto em que uma data deve ser representado. Ele é atribuído a um campo particular da classe.  
  
-   `CalendarExists`, um método particular que retorna um valor booliano que indica se o calendário representado pelo `CalendarUtility` objeto há suporte para o <xref:System.Globalization.CultureInfo> objeto que é passado ao método como um parâmetro. O método ajusta uma chamada para o <xref:System.Array.Exists%2A?displayProperty=nameWithType> método ao qual ele passa a <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> matriz.  
  
-   `HasSameName`, um método particular atribuído para o <xref:System.Predicate%601> representante que é transmitido como um parâmetro para o <xref:System.Array.Exists%2A?displayProperty=nameWithType> método. Cada membro da matriz é passado ao método até que o método retorne `true`. O método determina se o nome de um calendário opcional é o mesmo que o calendário representado pelo objeto `CalendarUtility`.  
  
-   `DisplayDate`, um método público sobrecarregado que é passado com dois parâmetros: o um <xref:System.DateTime> ou <xref:System.DateTimeOffset> valor para expressar no calendário representado pelo `CalendarUtility` objeto; e a cultura cujas regras de formatação serão usados. Seu comportamento ao retornar a representação de cadeia de caracteres de uma data depende de o calendário de destino ter suporte da cultura cujas regras de formatação devem ser usadas.  
  
 Independentemente do calendário usado para criar um <xref:System.DateTime> ou <xref:System.DateTimeOffset> valor neste exemplo, se o valor normalmente é expresso como uma data no calendário gregoriano. Isso ocorre porque o <xref:System.DateTime> e <xref:System.DateTimeOffset> tipos não preservar nenhuma informação de calendário. Internamente, eles são representados como o número de marcadores decorridos desde a meia-noite de 1º de janeiro de 0001. A interpretação desse número depende do calendário. Na maioria das culturas, o calendário padrão é o calendário gregoriano.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer uma referência a System.Core.dll.  
  
 Compile o código na linha de comando com csc.exe ou vb.exe. Para compilar o código em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], coloque-o em um modelo de projeto de aplicativo de console.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)
